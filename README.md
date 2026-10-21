# Cisco Packet Tracer Extended ACL Lab

A Cisco Packet Tracer security lab demonstrating extended access control lists (ACLs) to filter IPv4 traffic between network hosts.

## Project Overview

This lab illustrates extended ACL configuration on a router in a small switched network. The screenshot shows multiple LAN hosts and servers connected through switches, plus router CLI work involving ACL 120 and an inbound application on an interface.

## Features

- Extended IPv4 ACL concepts and traffic filtering
- Router CLI configuration and ACL verification
- Example permit/deny policy discussion
- Topology and CLI screenshots included as documentation

## Technologies Used

- Cisco Packet Tracer
- Cisco IOS CLI
- IPv4
- Extended access control lists (ACLs)
- Ethernet switching

## Project Structure

```text
packet-tracer-extended-acl-lab/
├── README.md
└── screenshots/
    └── extended-acl-topology-and-cli.jpg
```

## Network Topology Details

The screenshot shows a router connected to two switched segments, with client PCs on one side and servers on the other. The CLI shows an extended ACL named by number 120 and an inbound ACL application on `GigabitEthernet0/0`. The visible ACL output also lists entries numbered 10, 20, and 30, but the full intended policy and addressing plan are not completely legible.

## How to Recreate and Test

1. Add a router, two switches, client PCs, and Server-PT devices to a Packet Tracer workspace.
2. Connect endpoints to switches and connect each switch to a router interface.
3. Configure IPv4 addresses and masks on router interfaces and hosts. Ensure routing is in place before applying filtering rules.
4. Create an extended ACL that matches the required source, destination, protocol, and port criteria. ACL wildcard masks are used in IOS ACL statements, not subnet masks.
5. Apply the ACL inbound or outbound on the interface where it should filter traffic.
6. Verify allowed and blocked traffic using pings or application tests that match the policy.
7. Save your own working topology as a `.pkt` file.

## Useful Verification Commands

```text
enable
show access-lists
show ip interface gigabitEthernet0/0
show running-config

# Illustrative ACL pattern only — adapt addresses to your lab
configure terminal
ip access-list extended LAB-FILTER
 permit icmp 192.168.10.0 0.0.0.255 any
 deny ip any any
interface gigabitEthernet0/0
 ip access-group LAB-FILTER in
end
show access-lists
```

## Expected Results

Traffic matching permit statements should pass; traffic matching deny statements should be dropped. ACL order matters because IOS evaluates entries from top to bottom. The screenshot shows CLI attempts and ACL output, but also displays invalid-input messages for some commands, so it should not be presented as proof that every entered line was accepted or that the final policy was fully tested.

## Screenshots

![Extended Acl Topology And Cli](screenshots/extended-acl-topology-and-cli.jpg)

## Important Notes

The original `.pkt` file was not provided. This package includes screenshots and documentation only. The example commands are illustrative and have not been tested against the original topology. Use wildcard masks and interface names appropriate to the recreated lab.

## Portfolio Use

This repository is intended as networking-lab documentation for a student internship portfolio. To present it as a completed practical implementation, recreate and verify the topology in Cisco Packet Tracer and add the resulting `.pkt` file and your own test evidence.

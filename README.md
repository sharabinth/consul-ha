# Consul Enterprise HA Setup
This repo has a vagrant file to create an enterprise Consul Cluster with 3 server nodes without TLS

## Pre-Requisites
Create a folder named as ```ent``` and copy the Consul enterprise binary zip file 
```e.g., consul-enterprise_1.4.4+prem_linux_amd64.zip```

## Description
3 Consul server cluster nodes are created at the following addresses

```
Server1   10.100.1.11
Server2   10.100.1.12
Server3   10.100.1.13
```

After setting up, one of them will be elected as a leader

## Usage
If the ubuntu box is not available then it will take sometime to download for the first time.  After the the servers can be destroyed and recreated easily with Vagrant

```
$vagrant up

$vagrant status

```

To check the status of the Consul servers ssh into one of the nodes and check the cluster members and identify the leader.

```
$vagrant ssh consul1

vagrant@c1: $consul members

vagrant@c1: $consul operator raft list-peers 

```

## Accessing UI
One of the server nodes can be used to access the UI on port 8500

http://10.100.1.11:8500 

The UI will not work if the leader is not elected


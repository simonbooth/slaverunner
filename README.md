slaverunner
===========

A framework designed to enable autonomous generic systems to startup an application with minimal local configuration.

Why
---
Every project I write usually starts out a simple command line or empty window like project, quickly it scales into several interdependant components running in seperate windows / processes.
What I wanted to have was a general purpose framework that would start up all my seperate apps, handle configuration, versioning, deployment, dependancies etc.
Its relatively easy to do this on a single framework (e.g all node, all node-webkit, all java, all .net, etc) but when they all get mixed up along with various whacky system tools and scripts it gets hairy quickly.

How it works
------------
1. The system boots (project goal is to run on linux and windows in both system and user modes)
2. The slaverunner core process starts using a normal service mechnism - slaverunner core is node.js based
  a. If slaverunner detects that it is running on a virtual machine (VMware / hyper-v / openstack / virtualbox / amazon) it will attempt to load bootstrap configuration using known methods
  b. Next slaverunner scans mounted drives and looks for a known configuration file
  c. Slaverunner runs a network discovery (zeroconf or similar) to retrieve local lan available configuration 
  d. Slaverunner goes to a cloud service and attempts to retrieve configuration
3. Usermode slaverunners get started by 0 or more logged in user scripts (Xconfig on linux / xorg or in the startup sequence on windows) - slaverunner usermode is node-webkit based
4. Once configuration is retreived slaverunner begins executing processes defined in configuration.

Is this secure?
---------------
It is as secure as you want it to be, configuration files are signed 



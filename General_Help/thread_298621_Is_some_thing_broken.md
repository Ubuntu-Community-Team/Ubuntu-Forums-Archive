---
title: "Is some thing broken?"
date: 2006-11-13
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-13
Hi Every One! Could some one please have a look at the following? I was installing amarok and doing update when this was spit out from terminal. Thanks:???:                                                                                                                          Fetched 5B in 28s (0B/s)                                                                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  libggi2 mplayer 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libgii1 libgii1-target-x 
The following packages will be automatically REMOVED:
  libgii0 libgii0-target-x 
The following NEW packages will be installed:
  libgii1 libgii1-target-x 
The following packages will be REMOVED:
  libgii0 libgii0-target-x 
The following packages will be upgraded:
  libggi2 mplayer 
2 packages upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 4276kB of archives. After unpacking 1597kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe libggi2 1:2.2.1-4ubuntu1 [482kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe libgii1-target-x 1:1.0.1-2 [15.9kB]                   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe libgii1 1:1.0.1-2 [234kB]                             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse mplayer 2:0.99+1.0pre8-0ubuntu8 [3545kB]            
Fetched 4276kB in 2m24s (29.5kB/s)                                                                  
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by an.echte.trilingue on 2006-11-13
That kind of error usually happens when you are trying to run graphcial programs as user A while logged in as user B.

What was the command you input into the terminal?

were you trying to sudo synaptic from the terminal or something?

---


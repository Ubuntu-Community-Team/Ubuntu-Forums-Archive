---
title: "Cannot Remove Or Install VMWare Player"
date: 2006-10-31
forum: General Help
---

### Post by OffHand on 2006-10-31
Hi
I have been fooling around with vmware and messed up somewhere in the process. At this point VMWare player does not start and I cannot install or remove it either. I get the following error:

```
xxxxx@xxxx:~$ sudo aptitude remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  vmware-player 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.1MB will be freed.
Writing extended state information... Done
(Reading database ... 140732 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
admin@Edgy:~$ sudo aptitude install vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
cp: cannot create regular file `/etc/vmware/locations': No such file or directory
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
xxxxx@xxxxx:~$ 
```

Does anyone know how I can fix this?

---

### Post by distroman on 2006-10-31
I am not sure, never gave vmware-player a try, only vmware-server and installed from there site. 

Anyway see if you got a vmware-uninstall.pl in /usr/bin, give it a try if you do, might clean it up. 

Otherwise I don't know.

---

### Post by mooscape on 2007-02-22
Offhand,  I have the same problem.  Can I get rid of the old version manually?

The current situation:

mooscape@mooscape:/usr$ sudo aptitude remove vmware-player
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Reading task descriptions... Done
Building tag database... Done
Couldn't find any package whose name or description matched "vmware-player"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
mooscape@mooscape:/usr$

:confused:

---

### Post by mooscape on 2007-02-23
I have resolved this issue by doing a search for all files containing the name "vmware". (Doing  an uninstall did not seem to be enough. ) 

The problem originally started when I tried to get both vmware-server and vm-player going (greedy me! :roll: ). After removing everything pertaining to either of these, I installed vmware server and it is working perfectly.

Good luck....

---

### Post by brownknight on 2007-04-28
You mean you manually deleted anything that pertains to vmware and then installed vmware server? I am having the same problem too. Thanks.

---

### Post by mooscape on 2007-05-15
Sorry for late reply....   When installing VMWARE it is best to use vmware server as far as I can judge. 
I have go it running really well on two machines.  HP running XP and IBM running win2000 and autocad. They both run very well.  In both cases I made mistakes that required reinstalling vmware. In both cases I had to carefully remove all references to vmware to get it installed.  Also note that vmware won't run properly until you have installed vmware tools on the guest (virtual machine) operating system! Example: when you have installed XP say, you must start XP, then  you must go to the menue bar in vmware  and click on "VM" button, then select "Install VMware tools" and then go with the flow.  (VMware Tools has to do with graphics drivers etc that vmware needs to install on guest system...) :biggrin:  Good luck.

---


---
title: "Initscripts missing when installing a .deb VPN package"
date: 2017-02-03
forum: General Help
---

### Post by waltd on 2017-02-03
Hi all,  
    My OS is Xubuntu 16.10, 16bit.  I am trying to install ExpressVPN.  It's an openVPN .deb package from ExpressVPN.  But when I run the .deb package I get the following error message:  "Package initscripts is not installed".   
Here is the terminal messages.  Does anyone have an idea how to fix this problem so I can get a clean install of this .deb package?  Thanks. 
 
walter@walter-HP-Pavilion-dv7-Notebook-PC:~$ cd ~/Downloads/
walter@walter-HP-Pavilion-dv7-Notebook-PC:~/Downloads$ sudo dpkg -i expressvpn_1.1.0_amd64.deb
[sudo] password for walter: 
Selecting previously unselected package expressvpn.
(Reading database ... 215156 files and directories currently installed.)
Preparing to unpack expressvpn_1.1.0_amd64.deb ...
Unpacking expressvpn (1.1.0) ...
dpkg: dependency problems prevent configuration of expressvpn:
 expressvpn depends on initscripts; however:
  Package initscripts is not installed.


dpkg: error processing package expressvpn (--install):
 dependency problems - leaving unconfigured
Processing triggers for systemd (231-9ubuntu2) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 expressvpn

---


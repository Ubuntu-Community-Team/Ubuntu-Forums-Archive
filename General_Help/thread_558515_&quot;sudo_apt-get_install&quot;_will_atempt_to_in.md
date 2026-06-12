---
title: "&quot;sudo apt-get install&quot; will atempt to install vmware-player every time"
date: 2007-09-24
forum: General Help
---

### Post by suchawato on 2007-09-24
Hi.
Every time I run a "sudo apt-get" install or remove, at the end of installing or removing whatever appllication I had selected, it will also try to install vmware player.
It has done this since I had originally tried to install vmware player some months ago, and has now gotten annoying enough that I would like to do something about it.
I do not care if vmware player is installed or not.
Here is an example of what the terminal looks like, in this example I ran a redundant reinstall of xscreensaver for demonstration purposes:

[COLOR="Lime"]stu@ubuntu:~$ sudo apt-get install xscreensaver
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xscreensaver is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java liblog4j1.2-java libswt3.2-gtk-java libseda-java
  libcommons-cli-java libgtk-jni libcairo-java libbcprov-java libglib-java
  libgtk-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.[/COLOR]
[COLOR="black"][COLOR="Red"]Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.242.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] n

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.142.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] n

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] n

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
stu@ubuntu:~$ 
[/COLOR][/COLOR]
The section in red denotes the section that repeats every time.
It is quite annoying as it requires me to answer those questions every time in order to complete the operation. 
Thanks a lot in advance.
-Stu

---

### Post by peddy on 2007-09-24
Try 'sudo apt-get remove --purge vmware'.
This will get rid of VMWARE, so that you can try installing it again (if you want to). It should stop the errors. It will not delete your virtual machines.

Peddy

---

### Post by suchawato on 2007-09-27
I tried "[COLOR="DarkOrchid"]sudo apt-get remove --purge vmware[/COLOR]"

It did remove it for the current session, and then it was back the next time I rebooted.
Any thoughts?

---


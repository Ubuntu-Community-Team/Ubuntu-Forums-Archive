---
title: "VNC preventing access to a remote SMB share"
date: 2017-01-25
forum: General Help
---

### Post by 99victor on 2017-01-25
Ive been trying to work through this issue now for a week, and google seems to have very limited information regarding my problem. I was hoping someone in this community could shed a little light.

[B]Infrastructure
Virtual: [/B]Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-59-generic x86_64)
**GUI: **Lubuntu LXDE
**VNC: **tightvncserver
**Dependencies: **xfce4, xfce4-goodies[B]

Problem
[/B]When I open the console window to my Lubuntu GUI via ESXi and login as username "one" and open pcmanfm and browse to "smb://<address>/<directory>" I successfully reach a login prompt. On the other hand if I VNC into "<address>:1" as user "one" and open pcmanfm and try to browse to the SMB like before I am prompted with a popup error "Operation Not Supported".

[B]Troubleshooting Steps Attempted
[/B]1. Made user "one" a sudoer and edited the /etc/sudoer file to add this user into the root group.
2. Inspected VNC config files to look for permission flags. (assuming Im looking at the correct ones)
3. Disable all firewall's installed with Ubuntu and Lubuntu.
4. Rebooted
5. [https://ubuntuforums.org/showthread.php?t=1623346](https://ubuntuforums.org/showthread.php?t=1623346) - Had no effect
6. Inspected /var/log/syslog and did not see anything that stood out as an issue. (Will attach to OP)
7. Inspected ~/.vnc/ubuntu:1.log and did not see anything that stood out as an issue. (Will attached to OP)
8. Installed Thunar to make sure pcmanfm wasn't crapping the bed. No effect.
9. Reinstalled Ubuntu 16 fresh and applied updates. Then installed ONLY Lubuntu-Desktop and the VNC package and dependencies. (To eliminate conflict of other programs or services running on the device.)

[B]Why am I doing this?
[/B]This design strategy is to develop a kiosk solution to securely display PDF's via a VNC connection through Guacamole. PDF's are kept up to date on a SMB share and accessing them through the SMB would prevent the need of hosting a second set of PDF's and keeping them up to date. This solution is contained within a lab environment (non-public facing) and I have no issues with allow all users configured on the device to have full permissions (root) and disable all security firewalls built into the OS. I have gotten everything to work aside from the SMB access via VNC.

Please view attachments for screenshots and log files. (The forums would not allow me to upload a .txt log file for some odd reason)

---

### Post by TheFu on 2017-01-25
Don't use SMB for unix-to-unix sharing. Use NFS and in a commericial environment, probably want NFSv4 with Kerberos. This way you can make the PDFs read-only mounts.

Don't put userids into the "root" group without a thorough understanding of that what does. I've **never** needed to do that in 25 yrs as a Unix/Linux admin. There are less shotgun-type methods available.

Can't help with ESXi issues. Dumped all VMware stuff in 2011.

Just an idea, but why use VNC at all?  Run the kiosk on a Linux machine and use NFS to is to open the PDFs directly. This way you could limit the end users to only 1 program, locked down, that cannot be used for anything else - basically, only arrow keys would be needed - disable all the other keyboard events.  If the files change multiple times a day and NFS isn't workable (for whatever reason), then you can setup an rsync push to each client if any files have changed.

Security of CIFS and VNC is really very poor, BTW.

There are others here who will have different ideas about this too. Can't wait to see what those good folks have to say.

Also, welcome to the forums.

---

### Post by 99victor on 2017-01-25
> **TheFu said:**
> Don't use SMB for unix-to-unix sharing. Use NFS and in a commericial environment, probably want NFSv4 with Kerberos. This way you can make the PDFs read-only mounts.
The remote share is a windows file share.

I was reading some stuff about mounting SMB shares into the file system similarly to what you are describing. I wonder if that is the better approach, because all I need to do is have Firefox open the PDF and kiosk it with a Firefox kiosk add-on.

> **TheFu said:**
> Don't put userids into the "root" group without a thorough understanding of that what does.
I fully understand the consequences of putting users in the root group. However as stated in the OP it is a lab environment, in ESXi (Snapshots), and giving users full control of the device is not something I'm too concerned about. Secondly, it was a troubleshooting step to see if permissions are hindering the task I'm setting out to do.

> **TheFu said:**
> Just an idea, but why use VNC at all?  Run the kiosk on a Linux machine and use NFS to is to open the PDFs directly. This way you could limit the end users to only 1 program, locked down, that cannot be used for anything else - basically, only arrow keys would be needed - disable all the other keyboard events.  If the files change multiple times a day and NFS isn't workable (for whatever reason), then you can setup an rsync push to each client if any files have changed.
I appreciate the secondary solution/idea, I will see if it can be applied into my environment to achieve the same goal. However, I must be able to access to PDF/Kiosk via VNC through a Apache Guacamole VNC or RDP connection. (That just made me think I should try xRDP to see if I get the same behavior. I do feel the original problem can be conquered, it just finding out what in VNC is preventing me from opening an SMB share.)

---

### Post by TheFu on 2017-01-25
Yep - understand. Sometimes we don't have any real controls over all parts of a solution.

Mount the windows storage at the OS level using the fstab.  Then users will just need to access the files inside whatever directory you mount it into from the fstab.  

VNC shouldn't have anything to do with this storage part. Just make certain the mounted CIFS storage is at least readable by the userid VNC is running as.  I looked at Guacamole a few years ago and decided against it. Don't really want a web interface into a machine when a normal web browser can accomplish the same things.  There's a reason that redhat trains people to setup their VNC-servers with the -localhost option. That little thing solves most network security issues with VNC. 

There is another vnc-to-web interface. Learned about it from a Canonical employee last year  ... checking my notes ...  [http://www.admin-magazine.com/Archive/2013/16/Open-Virtual-Desktop-3.0-as-an-alternative-to-VDI](http://www.admin-magazine.com/Archive/2013/16/Open-Virtual-Desktop-3.0-as-an-alternative-to-VDI) and [http://www.linux-magazine.com/Issues/2015/170/Ulteo-OVD](http://www.linux-magazine.com/Issues/2015/170/Ulteo-OVD) ... I've never used it, but the Canonical guy seemed really excited about it. Don't know that I'd switch if you are tied to VNC already. Lots of options in this space.  I use x2go for my daily-use desktop running inside a private cloud.  For me, it feels 2-3x faster than any VNC I've tried.

---

### Post by 99victor on 2017-01-25
> **TheFu said:**
> Mount the windows storage at the OS level using the fstab. Then users will just need to access the files inside whatever directory you mount it into from the fstab.
Trying now. Will update soon.

> **TheFu said:**
> There is another vnc-to-web interface. Learned about it from a Canonical employee last year ... checking my notes ... [http://www.admin-magazine.com/Archive/2013/16/Open-Virtual-Desktop-3.0-as-an-alternative-to-VDI](http://www.admin-magazine.com/Archive/2013/16/Open-Virtual-Desktop-3.0-as-an-alternative-to-VDI) and [http://www.linux-magazine.com/Issues/2015/170/Ulteo-OVD](http://www.linux-magazine.com/Issues/2015/170/Ulteo-OVD) ... I've never used it, but the Canonical guy seemed really excited about it. Don't know that I'd switch if you are tied to VNC already. Lots of options in this space. I use x2go for my daily-use desktop running inside a private cloud. For me, it feels 2-3x faster than any VNC I've tried.
Thanks for the info. Ill give it a read.

---

### Post by 99victor on 2017-01-25
Success!

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

That is the guide I followed. Thanks for talking me through this Fu.

I'd like to add a quote from the person that was teaching me IT at my first IT job. "Always remember that there is usually 3 different ways to accomplish the task you set out to do. Use the one that works and move on." ;)

---


---
title: "Accessing Ubuntu Desktop Remotely"
date: 2015-03-14
forum: General Help
---

### Post by krine11 on 2015-03-14
For my workstation at work, I have been dual booting between Ubuntu and Windows for years. Usually, when I need to access the machine remotely, I RDP into Windows. This time, I left my Windows boot shut off, only with Ubuntu running. Is there a way to RDP to Ubuntu? I am running Ubuntu 14.04 at the moment. 

I want to access the entire desktop, as I am able to with Windows, and of course transfer files between the machine I am logged in from to my work computer I am connecting in via remotely. 

I will be unable to test this out until Monday morning, so for now, I am just seeking answers. 

Thanks!

---

### Post by nerdtron on 2015-03-14
I personally don't remote desktop my ubuntu since all I do is ssh and do command line stuffs, but here is a recent writeup on programs that you may want to checkout.
[http://www.datamation.com/open-source/linux-remote-desktop-roundup.html](http://www.datamation.com/open-source/linux-remote-desktop-roundup.html)

Splashtop, Team Viewer, etc..

---

### Post by krine11 on 2015-03-16
> **nerdtron said:**
> I personally don't remote desktop my ubuntu since all I do is ssh and do command line stuffs, but here is a recent writeup on programs that you may want to checkout.
[http://www.datamation.com/open-source/linux-remote-desktop-roundup.html](http://www.datamation.com/open-source/linux-remote-desktop-roundup.html)

Splashtop, Team Viewer, etc..

I should've added this, but due to restrictions set within our IT department, they only recommend options that are installed within the OS, and not a 3rd Party provider. 

I am definitely open to working through the command line of course, it is just a matter of making sure I know how to access it! Either way, I have installed OpenVPN to VPN to our network.

---

### Post by mastablasta on 2015-03-16
what do you mean how to access it? all you need is a terminal. 

well that and default setting is not really safe. :)  : [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by krine11 on 2015-03-16
> **mastablasta said:**
> what do you mean how to access it? all you need is a terminal. 

well that and default setting is not really safe. :)  : [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

I should've realized earlier about SSHing into my machine, I am now able to login in succesfully! 

Any recommendatons on file transfer? I am obviously using FileZilla at the moment, but I was wondering if there is already an built-in alternative? My IT deparmtment is super strict about these things, and want me to use specifically things that are built onto the OS. 

And lastly, I assume I wouldn't need full Desktop access (as in windows with RDP), but if I do later down the road, is there an built-in service for that as well? Or are third party services such as TeamViewer my only option?

---

### Post by krine11 on 2015-03-16
I also wanted to add, I couldn't see both my Windows partition nor files on our network server, I was wondering if it is possible to browse through these via SSH?

---

### Post by Holger_Gehrke on 2015-03-16
Transferring files: scp

Mounting NTFS partitions: sudo mount -t ntfs "device" "directory"
Finding the "device" names: sudo fdisk -l
You might want to put the NTFS-partitions into the /etc/fstab with the option noauto and user, then the won't be mounted automatically but can be mounted by normal users (which might clear up permission problems ...)

Finding servers: net server domain
Finding shares: net share -S "Servername"
Mounting share: sudo mount -t cifs //"server"/"share" "directory"

Reading the appropriate man-pages would be a good idea ...

---

### Post by krine11 on 2015-03-16
> **Holger_Gehrke said:**
> Transferring files: scp

Mounting NTFS partitions: sudo mount -t ntfs "device" "directory"
Finding the "device" names: sudo fdisk -l
You might want to put the NTFS-partitions into the /etc/fstab with the option noauto and user, then the won't be mounted automatically but can be mounted by normal users (which might clear up permission problems ...)

Finding servers: net server domain
Finding shares: net share -S "Servername"
Mounting share: sudo mount -t cifs //"server"/"share" "directory"

Reading the appropriate man-pages would be a good idea ...

Thank You! This all works now!

---


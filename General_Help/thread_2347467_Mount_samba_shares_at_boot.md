---
title: "Mount samba shares at boot"
date: 2016-12-25
forum: General Help
---

### Post by mgarrett682 on 2016-12-25
I have created a series of samba shares on a computer running Ubuntu 16.04 desktop with one share accessible by all computers on my network for sharing movies and an individual private share for each computer to use for backups and file storage. I set the Windows computers to map those shares at boot with no problems. Now I am trying to get another Ubuntu 16.04 Desktop, my home theater pc, to mount the shares at startup with no luck.

Here is what I've done on the htpc:

1. Created a file, /etc/samba/user with the password and username in the format:
     username=htpc
     password=htpcpassword

2. Created a folder to mount the share using the command:
     sudo mkdir /media/Everybody

3. Added a line to the /etc/fstab file:
    //myserver_ip_address/sambashare  /media/Everybody  cifs  credentials=/etc/samba/user,noexec  0 0

When I reboot the machine the share does not automatically mount. I can mount it from terminal with sudo mount /media/Everybody and it works just fine. I haven't tried setting up the private share to mount at boot since I can't get this one working. What am I doing wrong?

---

### Post by Keith_Helms on 2016-12-25
Is this a wired network or wireless?  Wireless may not be initialized enough to mount a share using fstab.  If wired, open a terminal and do
```
view /var/log/syslog
```
and then type
```
/sambashare
```
To see what kind of error is being logged when the system tries to mount that share.  If the reason for the error is not obvious, post the error lines in a reply.
Do a :q to exit

---

### Post by mgarrett682 on 2016-12-25
> **Keith_Helms said:**
> Is this a wired network or wireless?  Wireless may not be initialized enough to mount a share using fstab.  If wired, open a terminal and do...

This is a wireless connection. Should it be done a different way for wireless?

---

### Post by Morbius1 on 2016-12-25
> When I reboot the machine the share does not automatically mount. I can  mount it from terminal with sudo mount /media/Everybody and it works  just fine. I haven't tried setting up the private share to mount at boot  since I can't get this one working. What am I doing wrong?                 
You may be doing nothing wrong. As stated above it could be that the lines in fstab are being read before the network is fully up on your system so the mount fails. Systemd absolutely positively prevents this from happening. In theory. On paper .............

The next time you reboot issue this command:
```
sudo mount -a
```
[COLOR=#0000cd]**EDIT**[/COLOR]: [COLOR=#0000cd][I]What that command will do is read fstab and mount anything that hasn&#8217;t already been mounted.
[/I][/COLOR]
If it spits out any error messages post them back here. If it just comes back to the prompt your cifs mount should be successful. 

If it does then do this:

** Create a script:
```
gksu gedit /etc/network/if-up.d/fstab
```
** Add these lines to it:
```
#!/bin/sh
mount -a
```
** Save the file, exit gedt, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstab
```
Any script in if-up.d will only be executed after the network is up.

---

### Post by mgarrett682 on 2016-12-26
Excellent. Keith_Helms and Morbius1, your suggestions fixed it perfectly. Both shares now mount at boot or restart. Thanks!!!!

---


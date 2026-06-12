---
title: "How to access a folder on my Mac Book Pro from Ubuntu on a server ?"
date: 2018-06-12
forum: General Help
---

### Post by freeflyjohn on 2018-06-12
I have successfully configured samba and netatalk (for Time Machine) so that I can access drives on my server from my Mac Book Pro (MBP).

But now I want to do the reverse, I want to access folders on my MBP from my Ubuntu server.

The reason for this is because I want to use rsync to backup the iTunes folder on my MBP to a drive on my server, so I plan to setup a cron task for rsync so that it makes a regular backup.

After searching online, the only way I have managed to access a folder on my MBP from Ubuntu is by allowing 'Remote Login' in the 'Sharing' preferences on the MBP and using SSH from the Ubuntu terminal (e.g. ssh [email]username@mymacbook.home[/email]).

Is there an alternative method to using SSH? If my MBP can access folders on the Ubuntu server using samba and netatalk, then can this be used the other way around to access folders on my MBP from Ubuntu server ?

The MBP and Ubuntu server is on a local network so the security offered by SSH is not required and this might be why it appears to run slower than samba or netatalk ?

Another issue with SSH is when I connect to the MBP from Ubuntu server, it first asks if I want to continue because the authenticity of the host can't be established (which requires typing 'yes' and fails to add the host to the list of known hosts), then following that it asks for a password.  As far as I know, I am unable to write a .sh script for a cron task to run rsync because SSH asks for this confirmation and password so it requires user intervention?

I also need to consider how to handle when the MBP is offline and therefore Ubuntu server won't be able to access my iTunes folder and run rsync.

---

### Post by yancek on 2018-06-12
The tools needed to read/write to a MAc are not generally in a default install of any Linux system including Ubuntu simply because Macs have such a small market share.  You need something like hfsplus, hfsprogs or hfs-tools installed to start with.

---

### Post by freeflyjohn on 2018-06-12
> **yancek said:**
> The tools needed to read/write to a MAc are not generally in a default install of any Linux system including Ubuntu simply because Macs have such a small market share.  You need something like hfsplus, hfsprogs or hfs-tools installed to start with.

Thanks yancek,  I assume that I only need to read from the MBP as the iTunes folder on the MBP will be the source and a folder on the Ubuntu server will be the destination ?

I have used the free version of HFS explorer on a Windows laptop to read a USB HDD which was formatted on a Mac.

I (naively) thought that if the MBP can access folders on the Ubuntu server using samba or netatalk, then it would work the other way around so that Ubuntu could access (read) folders on the MBP ?

Is SSH my best option then ?  And if so, when writing a .sh script for the rsync cron task, how do I get around the issue when SSH responds with"[COLOR=#000000]the authenticity of the host can't be established" and when it asks for a password ?[/COLOR]

---

### Post by Holger_Gehrke on 2018-06-12
@yancek: sorry, but the hfs tools are only needed when you're trying to read a hfs(+) formatted hard disk on a Linux machine. They are not needed for network access, just like you don't need a driver for ext2 access on Windows to access file on a Linux server running Samba.

Mac OS X is basically a (BSD-) Unix with a proprietary GUI. Most -- if not all -- the usual command line tools are either already installed or can be gotten either directly from apple or from various other sources. So rsync, ssh(d) and cron should either already be on your MBP or rather easily installed. If your backup should happen when the MBP is running, then it's better to use cron to run rsync on the Mac to push the data to the server than to make the server repeatedly look for a machine that might not be there.

Holger

---

### Post by freeflyjohn on 2018-06-13
Thanks Holger - that makes more sense to use the Mac to run a cron task for rsync, Ill give it a try :)

---

### Post by Morbius1 on 2018-06-13
This is more of an FYI ( OK, it's a very long FYI ) since I'm not sure samba would be the best protocol for what you are trying to do but:

 > I (naively) thought that if the MBP can access folders on the Ubuntu  server using samba or netatalk, then it would work the other way around  so that Ubuntu could access (read) folders on the MBP ?

It can indeed at least for Samba.

I just modified an entry in my Xubuntu desktops /etc/fstab file and added them to an Ubuntu server:

First, I made sure cifs-utils is installed on the Ubuntu server.

Then I added the following line to it's fstab file:
```
 //dmbp.local/smbuser's\040public\040folder /media/DMBP-Public cifs username=smbuser,password=smbuserpw,uid=1000,noauto,nounix 0 0
```

Then I mounted the MBP samba share on the Ubuntu Server:
```
sudo mount /media/DMBP-Public
```

It outputs some scary looking error messages about invalid negotiate response and an ioctl error referencing smb2 most likely because CIFS negotiates which smb dialect to use with the server but it eventually mounts the MBP samba share:
> 
$ ls -al /media/DMBP-Public
total 16
drwxr-xr-x 2 tester root    0 Mar 15  2017 .
drwxr-xr-x 8 root   root 4096 Jun 13 14:35 ..
-rwxr-xr-x 1 tester root    0 Mar  8  2014 .com.apple.timemachine.supported
drwxr-xr-x 2 tester root    0 Mar  8  2014 Drop Box
-rwxr-xr-x 1 tester root    0 Nov 14  2015 FromWin10.txt
-rwxr-xr-x 1 tester root    6 Mar 15  2017 gedit.txt
-rwxr-xr-x 1 tester root    1 Mar 15  2017 gedit.txt~
-rwxr-xr-x 1 tester root    0 Mar  8  2014 .localized
-rwxr-xr-x 1 tester root    2 May 11  2016 Text File


---


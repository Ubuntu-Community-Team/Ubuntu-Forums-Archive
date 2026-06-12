---
title: "Auto-mounted network share suddenly broken"
date: 2006-07-05
forum: General Help
---

### Post by zhenya on 2006-07-05
I've been accessing this auto mounted network share on a Ubuntu 5.1 server from my dapper workstation just fine for a couple of weeks.  Suddenly, tonight I am no longer able access it.  I get the error: mount: only root can mount *servername*

Here is the contents of my /etc/fstab file, which has not changed.  Like I said, it was working earlier this evening.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.15.104/250share /media/250share smbfs username=xxx,password=xxxxx,umask=022 0 0 

```

What's going on?  Thanks for any help you can offer!

---

### Post by dmizer on 2006-07-05
for security reasons, i'm going to suggest some slight alterations, but i think we'll ultimately end up with a more secure and working answer to your problem:
first, create a smbcredentials file so you don't have the un/pass sitting out there for everyone to read:
```
sudo nano /root/.smbcredentials
```
add the following lines:
```
username=yoursmbusername
password=yoursmbpassword
```
save with ctrl+x, select "y" and <enter>
then we have to change the permissions of smb credentials and edit your fstab:
```
sudo chmod 700 /root/.smbcredentials
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
change your samba file mount line to the following:
```
//192.168.15.104/250share /media/250share smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
```
again, save by ctrl+x, select "y" and <enter>
now do:
```
sudo mount -a
```
and see if that fixes your problem.  if not, you may have some adjustment to do on your server side?  you may also have to adjust the permissions of /media/250share (sudo chown yourubuntuun /media/250share).

---

### Post by zhenya on 2006-07-05
Thank you very much for taking the time to help me.  :D 

I think my original issue was a permissions issue of some sort.  Using my original fstab file, the chown command restored my access.  (Although I am still not sure how I lost access in the first place.)

I have, however, also followed your advice and changed my fstab file as you suggested.  Thanks for the assistance!

---

### Post by zhenya on 2006-07-05
hmmm.  the problem does not seem to be solved.  Although I think I have figured out WHEN it is happening.  I've been trying to import my very large music collection mounted on this 250share network drive into Amarok.  It never gets very far, but today I started it before going to work, in hopes that it would be finished when I got home.  Unfortunately it was still locked up when I got home.  I killed Amarok, and now I'm back at the same spot I was when I started this thread, except this time I can't re-gain access.  

I can still access the 250share volume if I go through Remote Places/Samba Shares, but I cannot mount it.  I get the error:

> Could not mount device.
The reported error was:
mount: only root can mount //192.168.15.104/250share on /media/250share

when trying to access it through the GUI.  

Through the console I get:

> jed@Kubuntu-Desktop:/etc$ sudo chown jed /media/250share
chown: cannot access `/media/250share': Input/output error
jed@Kubuntu-Desktop:/etc$ sudo mount -a
Could not resolve mount point /media/250share


Anybody have any ideas?

EDIT: Nevermind.  I was able to umount /media/250share then chown then mount -a and it's working again.

---

### Post by dmizer on 2006-07-07
that's very strange that you should have to chown more than once ... seems like something is changing the permissions of your /media/250share.  i personally can't imagine what might be causing this other than some sort of update to the system.

next time you have the problem you should try to see if you can regain access without doing the chown command.  that is to say:
```
sudo umount /media/250share
sudo mount -a
```
if that allows you to regain access, then that just means that you might have a flaky network connection.

---

### Post by zhenya on 2006-07-07
Yeah, I no longer think it was the chown command that really restored my access.  I'm having problems in general with these Samba shares.  The Server running hoary has been totally stable (system uptime is in excess of 4 months at this point) and I never have any problems whatsoever when accessing these shares from my windows machines.

With Dapper I have this problem fairly regularly now.  If I'm trying to access a large amount of data (like my 40gb music collection through Amarok) and the program locks up, I can kill the program, but it locks the network share.  Sometimes I can umount it, but often the only solution is to reboot.  (The umount command doesn't work; device is busy.)

Additionally, I have had to change my fstab entries for these shares to noauto.  When they are set to auto mount, boot time increases tremendously, stalling at "hardware abstraction layer HALD," and I get an error message relating to the KDE interface at startup.

---

### Post by skirkpatrick on 2006-07-07
I have never, Breezy or Dapper, been able to get Samba shares to auto-mount.  I have always had to **sudo mount -a** whenever I have to reboot my system.  I have tried with and without the auto command in my fstab.  I thought it might have been a problem with my Breezy setup but a fresh install of Dapper has the same problem.  It almost acts like my network isn't completely up when fstab is run.

---

### Post by dmizer on 2006-07-07
> **zhenya said:**
> If I'm trying to access a large amount of data (like my 40gb music collection through Amarok) and the program locks up, I can kill the program, but it locks the network share.  Sometimes I can umount it, but often the only solution is to reboot.  (The umount command doesn't work; device is busy.)
okay, try to access your shares with amarok again. but this time instead of starting amerok via the menu, open up a terminal and type "amarok" ...

this way, you will be able to see amarok's errors in the terminal window.  maybe that will give you a clue.

---

### Post by messynger on 2007-02-05
my auto mounted share stopped working as well.  fixed my problem by removing noauto from the mount commands in fstab.

was:
```

//laptop/Music    /media/Laptop\040Music smbfs  noauto,credentials=/root/.smblaptopcredentials,dmask=777,fmask=777  0    0
```

now:
```

//laptop/Music    /media/Laptop\040Music smbfs  credentials=/root/.smblaptopcredentials,dmask=777,fmask=777  0    0
```

---


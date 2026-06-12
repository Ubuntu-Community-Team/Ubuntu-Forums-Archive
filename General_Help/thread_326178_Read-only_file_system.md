---
title: "Read-only file system"
date: 2006-12-27
forum: General Help
---

### Post by manutdfan2850 on 2006-12-27
When i boot i get the error:

'Could not start the X server due to some internal error. Please contact your system administrator or check our syslog to diagnose. In the meantime this display will be disabled. Please restart GDm when the problem is corrected.'

if i press ok and try to use the command sudo dpkg-reconfigure xserver-xorg it wont save the changes because it says "Read-only file system". How can i modify the settings and have them saved? i want to change from flgrx back to the ati drivers but i even tried the recovery mode but same thing... REad-only file system. ](*,) 

please help...

---

### Post by taurus on 2006-12-27
Post your /etc/fstab here...

```
cat /etc/fstab
```

---

### Post by manutdfan2850 on 2006-12-27
ok i think i know what i messed up. at the same time iwas trying to mount my ntfs windows partition for read/write access using this tutorial and i must have messed up

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

i think i messed up where i was supposed to state in fstab: /dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0

is there a way i can edit this out of it? i tried>  nano /etc/fstab BUt again i get the Read only error. 

what am i doing wrong????? :(

again i cant go into ubuntu when i start my computer because of this strange error it takes me to the command prompt. in recovery mode i also get the read only error.

---

### Post by taurus on 2006-12-27
Can you please post your /etc/fstab here???

---

### Post by dannyboy79 on 2006-12-27
taurus, he is telling you that he can't because when he does nano /etc/fstab, he gets an error telling him it's read only.

what if you pop in a live cd, then mount the drive, and try to post the fstab this way?

---

### Post by taurus on 2006-12-27
You don't have to use nano to look at /etc/fstab!!!  The more, less, or even cat would do just fine!!!

```
cat /etc/fstab
```
p.s.  This is like the third time I have to type that same command!  It feels like pulling teeth here...  ](*,)

---

### Post by manutdfan2850 on 2006-12-27
no sorry for the confusion. let me try to explain my problem. today i was messing with both my graphics settings and i tried to mount my windows partition using a tutorial. When i boot up my computer and select Ubuntu, it initially shows the load screen but then when its full, brings up a strange error that says

> 'Could not start the X server due to some internal error. Please contact your system administrator or check our syslog to diagnose. In the meantime this display will be disabled. Please restart GDm when the problem is corrected.'

if i press OK it does not load ubuntu but takes me to some kind of equivalent of windows command prompt. from there, i can open and view fstab, etc using cat /etc/fstab, but if i try to edit it using nano /etc/fstab and remove the last line where i believe i mesed up and is causing this error, i get the read only message . 



in any case, here the fstab (i am typing from another laptop at home since i cant copy/paste)

/dev/hda2 UUID=10d2b587-493f-4b8b-b8bd-4e75a3c3f290 / ext3 defaults, errors-remount-ro 0 1

/dev/hda5 UUID=51632ad6-d22e-4199-8113-cdf64a5887f9 none swap sw 0 0 

/dev/hdc/ media/ cdrom0 udf, iso9660 user, noauto 0 0 

[COLOR="DarkOrange"]/dev/winpart/media/hd1/ntfs-3g defaults, locale-en_us.utf8 0 0[/COLOR]

i added the last line on while i was following the steps of the tutorial but i believe this has caused the problem. again i keep getting the read only error when i try to remove the last line. i've also tried the recovery mode but same error.    



what do you advise? and sorry for the confusion

---

### Post by taurus on 2006-12-27
Okay, you can use either /dev/hda2 or UUID=10d2b587-493f-4b8b-b8bd-4e75a3c3f290 for your / partition in /etc/fstab but you cannot use both at the same time.  Therefore, boot with the LiveCD, mount your harddrive, and edit /etc/fstab...

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/fstab
```
Now, replace this line
```

/dev/hda2 UUID=10d2b587-493f-4b8b-b8bd-4e75a3c3f290 / ext3 defaults, errors-remount-ro 0 1
```
with this one
```

/dev/hda2   /   ext3   defaults,errors-remount-ro   0   1

```
You also need to modify the entry for your XP.  So while you are still in /etc/fstab, remove this line
```

/dev/winpart/media/hd1/ntfs-3g defaults, locale-en_us.utf8 0 0

``` 
and replace it with
```
 
/dev/hda1   /media/hda1   ntfs-3g   defaults,locale-en_us.utf8   0   0

```
Save it and create a new mount point for your ntfs...

```
sudo mkdir /mnt/ubuntu/media/hda1
```
Now, unmount the harddrive and reboot...

```
sudo umount /mnt/ubuntu
```

---

### Post by manutdfan2850 on 2006-12-27
thank you so much that fixed my problem

thanks again, i really appreciate it.

---

### Post by taurus on 2006-12-27
> **manutdfan2850 said:**
> thank you so much that fixed my problem

thanks again, i really appreciate it.

We could have this thing fix a couple of hours ago if you just showed me the /etc/fstab but nevertherless, it's all good now.  ;)

---

### Post by Dark Cerberus on 2007-02-24
Hey

I have a somewhat similar problem.

When I boot up, it all freezes at the splashscreen and screen goes totally blank with a blinking cursor at the top.
I tried ctrl-alt-F1 to get into console mode, but I only then saw the screen where i says: Uncompressing Linux - ok booting the kernel, or something like that

Then I found out i could press ctrl-alt-del wich then gives me: 
syslogd: /var/logauth.log: Read-only files system
ans a hole row of similar to this just different files

and then it gives me the meassage: 
Could not start the X server due to some internal error. Please contact your system administrator or check our syslog to diagnose. In the meantime this display will be disabled. Please restart GDm when the problem is corrected.

I press OK and I get to where I can Login

I thought I'd try the 'sudo dpkg-reconfigure xserver.xorg' but I just get the same: 'open: Read-only file system'


Here is the output of my /etc/fstab:

# /etc//fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=D474-FF45 /media/windows vfat users,owner,rw,unmask=000 0 0
# /dev/hda4 -- converted during upgrade to edgy
UUID=25100b7a-a43-407a-9bb3-c2c9ee9fa6b6 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=4498-78FB /media/fileshare vfat users,owner,rw,umask=000 0 0
# /dev/hda6 -- converted during upgrade to edgy
UUID=37a84239-51ab-4c34-bc59-eb9a18409a34 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0      0


can you please help me?
Thanks in advance.

I dont know what caused the problem, linux have worked perfectly for a long time now, and I didn't do anything specific the last time it worked.

---

### Post by taurus on 2007-02-24
What's the output of this command from a prompt then?

```
df -h
```

---

### Post by Dark Cerberus on 2007-02-24
the output of df -h:
Filesystem        Size  Used   Avail   Use%  Mounted on
/dev/hda4        15G    11G   2,7G     80%  /
varrun           189M     68K   89M      1%  /var/run
varlock          189M        0  189M      0%  /var/lock
procbususb      10M   388K   9,7M      4%  /proc/bus/usb
udev               10M   288K   9,7M     4%  /dev
devshm          189M       0    189M     0% /dev/shm

---

### Post by taurus on 2007-02-24
While still in the recovery mode, edit your /etc/fstab

```
nano -Bw /etc/fstab
```
and replace all the UUID with the actual device name.

```

# /etc//fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
/dev/hda2 /media/windows vfat users,owner,rw,unmask=000 0 0
# /dev/hda4 -- converted during upgrade to edgy
/dev/hda4 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5 /media/fileshare vfat users,owner,rw,umask=000 0 0
# /dev/hda6 -- converted during upgrade to edgy
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```
Save it with <Ctrl>x.  Then Y for the question and Return.

Reboot and see what happens now.

```
shutdown -r now
```

---

### Post by Dark Cerberus on 2007-02-24
I edit the file but when I save it I get the error:
/etc/fstab: Read-only file system

---

### Post by taurus on 2007-02-24
Can you boot your machine with a LiveCD?

---

### Post by Dark Cerberus on 2007-02-24
Yes I probably can, wait a sec I'll go get the CD.

---

### Post by Dark Cerberus on 2007-02-24
I found the CD.

I am running Edgy but the LiveCD is Dapper. Would this be a problem?

---

### Post by taurus on 2007-02-24
Shouldn't matter what version the CD is.

Now, open a terminal, mount your harddrive, and edit /etc/fstab.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda4 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/fstab
```

```

# /etc//fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
/dev/hda2 /media/windows vfat users,owner,rw,unmask=000 0 0
# /dev/hda4 -- converted during upgrade to edgy
/dev/hda4 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5 /media/fileshare vfat users,owner,rw,umask=000 0 0
# /dev/hda6 -- converted during upgrade to edgy
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```

---

### Post by Dark Cerberus on 2007-02-24
Done.
Now restart without the CD right?

---

### Post by taurus on 2007-02-24
Yip.

---

### Post by Dark Cerberus on 2007-02-24
The same thing happens. It says Read-only file system and all that.

---

### Post by taurus on 2007-02-24
Maybe you need to fsck your / partition (/dev/hda4).  From the LiveCD, run

```
sudo fsck -y /dev/hda4
```

---

### Post by Dark Cerberus on 2007-02-24
Okay, running the liveCD now.

---

### Post by Dark Cerberus on 2007-02-24
When I run fsck I get the messages: 
fsck 1.38 (30-jun-2005)
e2fsck 1.38 (30-jun-2005)
/: clean, 34057/1867776 files, 2843196/3729088 blocks

and then its done.
Anything else I can do?

---

### Post by Dark Cerberus on 2007-02-24
Nothing I can do?

---

### Post by linux_kid on 2007-02-24
Is your /home folder on it's own partition?

---

### Post by Dark Cerberus on 2007-02-24
No its on the same partition as the /

---

### Post by linux_kid on 2007-02-24
Besides applications, do you have any important documents that will be lost in a reinstall?

---

### Post by Dark Cerberus on 2007-02-24
Unfortunately yes I have alot of documents I need there.
But I can accsess them on the LiveCD, maybe I could copy them out to USB storage and reinstall.

---

### Post by linux_kid on 2007-02-24
I was thinking about getting the important docs while in Vista, from [http://www.fs-driver.org/]("http://www.fs-driver.org/") and then save them on the NTFS partition. After linux is reinstalled,  recover them from the NTFS partition using ntfs3g from [http://www.ubuntuforums.org/showthread.php?t=217009]("http://www.ubuntuforums.org/showthread.php?t=217009").
I guess you could do that with your whole /home, which may really help (and /usr/bin for apps)
Just some ideas, though.

The LiveCD and USB flash idea works five, too.

---

### Post by linux_kid on 2007-02-24
How did you resolve your issue?

---

### Post by Dark Cerberus on 2007-02-24
Yes I might do that. Thanks. :D

but I won't need to use ntfs3g since my windows partition is fat32. 

but otherwise this should work great. Thank you. 

I just wish there was some other way I wouldn't need to reinstall, because I don't have an Edgy CD so then I would have to upgrade from Dapper again.

---

### Post by linux_kid on 2007-02-24
Well, you could always just leave the download running for the edgy .iso and have it down in 3 or so hours.  No big deal.

---

### Post by Dark Cerberus on 2007-02-24
I got it down in 20 minutes :D

I think i'll just reinstall everything on my computer while I am at it, including Windows.

---

### Post by linux_kid on 2007-02-24
WOW, 20 minutes, that's pretty awsome.  What's your connection speed?

And a Windows reinstall is always nice; good call.

---


---
title: "ubuntu does not boot with 6 gb SATA cable"
date: 2014-06-17
forum: General Help
---

### Post by kakashi_12 on 2014-06-17
I had 3 gb SATA cable hooked up before. I plugged in 6 gb SATA cable and upped the speed in the BIOS.
Motherboard manual did say it would be best to install the cables before installing the OS. But if there is a way around that, let me know.

GRUB2 boots.
Windows 7 boots.
Ubuntu 12.04 does NOT boot.

See attachment.

---

### Post by Bucky Ball on 2014-06-17
You could try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair"), but not sure if that would help. Never seen this issue before ... :-k

I'm presuming you are using a SATAIII hard drive with this cable (which I believe is 6Gb as oppose to the 3Gb of SATAII)?

* Edit, just looking at your pic and it appears the UUID for that drive might have changed and your fstab and grub don't know where to look. Hang on ... I'll have a think ...

Did you plug it back into the same slot it was in previously???

---

### Post by kakashi_12 on 2014-06-17
Yes, correct.
Also, I've noticed this.
I switched the Linux HDD back to 3 GB SATA cable. Linux will boot fine with it.
Windows 7 HDD is still on 6 GB SATA cable. Windows 7 boots fine with it.
However, I can not mount my Windows HDD while booted into Linux. It just plain won't see it.
I can't even see it from GParted. I tried running System > Admin > Hardware Drivers. But it won't find drivers for the drive (only finds graphic card drivers).

---

### Post by Bucky Ball on 2014-06-17
Boot from the LiveDVD/USB;
'Try Ubuntu' and get to a desktop;
Open a terminal, navigate to the /etc/fstab file of the Ubuntu installed on the hard drive and open the file as root, normally:

```
sudo nano /etc/fstab
```

... but your path will be slightly longer;

Open another terminal and issue this command:

```
sudo blkid
```

With the terminals side by side, compare the UUID numbers. The ones in fstab should match the ones in the output of 'sudo blkid'. My guess is that the one with the altered cable probably doesn't. As I say, it's a guess, but if you look at your pic at the line that starts with 'ALERT!!!' it could be the problem. Good to rule it out either way ...

---

### Post by kakashi_12 on 2014-06-17
What do you mean slightly longer? How do I know what the exact command or path will be?
Edit... nvm. I ran the command now with the 3 gb cable plugged in and get results. I can do it from a live disc. Hang on.

---

### Post by Bucky Ball on 2014-06-17
Well, when booted to the Live desktop, you need to mount the / partition of the hard drive install. In there you will find the folder /etc and in that the file /fstab. Open that and compare the UUIDs with the terminal output of 'sudo blkid'.

---

### Post by kakashi_12 on 2014-06-17
How do I mount the partitions? And how will I be able to if it can't see it?

Besides I ran the command just now and it only saw the Linux partitions anyway. Won't see the Windows partitions. How do I mount them?

---

### Post by Bucky Ball on 2014-06-17
*Thread moved to **General Help**.*

Please post the output of 'sudo blkid' and your fstab file thanks. If you could provide a link to the output of bootinfoscript provided by Boot Repair that would be great. 

I thought the original issue was that you couldn't get Ubuntu to boot. Let's worry about that. The Win partitions are irrelevant at the moment. ;)

---

### Post by kakashi_12 on 2014-06-17
GNU nano 2.2.2              File: /etc/fstab                                  

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0



ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ squashhfs
squashhfs: command not found
ubuntu@ubuntu:~$ squashfs
squashfs: command not found
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ squashfs
squashfs: command not found
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo blkid squashfs
ubuntu@ubuntu:~$ 

HERE'S without mounting anything.

---

### Post by Bucky Ball on 2014-06-17
If this:

```
GNU nano 2.2.2              File: /etc/fstab                                  

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

... is all you have in /fstab, you are not navigating to the fstab on the hard drive but the one in the Live boot. Probably the same with this:

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
```

Totally confused with all of this:

```
ubuntu@ubuntu:~$ squashhfs
squashhfs: command not found
ubuntu@ubuntu:~$ squashfs
squashfs: command not found
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ squashfs
squashfs: command not found
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo blkid squashfs
ubuntu@ubuntu:~$ 
```

Once again, please use code tags for terminal output. Thanks.

Best would be to run the bootinfoscript from Boot Repair (you can install and run it in the Live boot) and post the link here.

---

### Post by kakashi_12 on 2014-06-17
Like I said, I don't know how to mount the volume/disk to run the command from there. That's why I asked how to mount.
Sorry, I'll use code tags next time.
The ^C is me trying to copy and paste with the keyboard. The rest of it is me trying to run the command it told me to run.
I'll try to get the bootinforscript next.

---

### Post by kakashi_12 on 2014-06-17
[http://paste.ubuntu.com/7659570/](http://paste.ubuntu.com/7659570/)

Please note, that where it says "Windows Vista" that is not true. It is actually Windows Server 2008. Boot Repair labelled it wrong.

---

### Post by grahammechanical on 2014-06-18
Someone else had had this problem a few years ago. I do not know if this old thread has anything useful for your problem. It might provide clues.

[http://ubuntuforums.org/archive/index.php/t-1614764.html](http://ubuntuforums.org/archive/index.php/t-1614764.html)

Regards.

---

### Post by kakashi_12 on 2014-06-24
Well, I guess I won't be able to use those option. I just tried a virtual install of XP with the controller being in AHCI mode and it blue screened. I planned on having XP and Win 7 on the same HDD. Maybe my BIOS will let me configure one drive as AHCI and the other as IDE. Then I could separate the installations on different HDD's. See if that works.

---


---
title: "Booting Kubuntu Using NTloader"
date: 2007-02-02
forum: General Help
---

### Post by guguma on 2007-02-02
I have a small (!!!) booting problem with Kubuntu (Dapper Drake alternate for AMD 64).

Are you guys angry that I have to XP partitions so you are not responding COME ON :).

Ok this is the situation I have a Seagate SATA 160GB HDD and the partitions are:

1 Primary NTFS XP installed
2 Primary NTFS storage
3 Primary NTFS XP installed (bootflag)
4 Extended
5 Logical  NTFS Storage
6 Logical  reiserfs Kubuntu dapperdrake installed
7 Logical  linux swap

What I want to do is to boot Kubuntu from the NTloader.(Do not suggest me to use GRUB or LILO I share this computer with some people and they may freak out with something new i just can not use them) I have searched through some posts and the only reasonable thing I heard is to create a bootsec.lnx file and copy it to the winXP and then edit the boot.ini file (show the path of bootsect.lnx) that it gives me an option to boot from the bootsect.lnx so that it will lead me to a linux booter (GRUB or LILO).

But I see that I am totally unable to do it, probably from lack of knowledge.

What I really lack the knowledge about is and suspicious are that:

1. Any kind of booting configuration.

2. I greatly suspect that because Kubuntu is installed on a logical partition I may not be able to boot it. 

What I tried:

1. I installed GRUB to a floppy disk using /dev/fd0 provided with the Grub Installer screen. It did some work to my floppy. Told me it was installed yet when I opened it. The old files in the floppy was remaining and no linux related thing.

2. I then used the installation cd again and installed GRUB to /dev/sda6 (this is the partition with reiserfs right?)

3. I then called the simple shell provided in the installation CD and wrote "dd if=/dev/sda6 of=bootsect.lnx bs=512 count=1"
which is suggested in this very forum to create the bootsect.lnx file.

4. Then I am stuck I mean I really am stuck.

5. What can I do next or where am I totally messed up and can fix it.

Please Help 

Thank You

---

### Post by guguma on 2007-04-13
Hello and good days,

Since I have got no replies I have to post the method I have obtained. (are you guys angry that I choose ntloader over GRUB c'mon :))

All right the only thing one has to do is to copy the first 512 bytes of the boot sector into a file. And add that file as an entry to the boot.ini file under windows.

To copy the first 512 bytes of the boot sector into a file.



```
sudo  dd if=/dev/sda6 of=bootsect.lnx bs=512 count=1 
```

More explanatory:

```
sudo(giving you root privilages) dd if=/dev/(where grub is installed) of=(filename) bs=512 count=1
```

just copy this file over to your windows operating system and modify your boot.ini file

Your boot.ini file should look as this

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /fastdetect
c:\bootsect.lnx="Your Favourite Linux Distro" 

of course you may need to change the path c:\bootsect.lnx to (filepath)\(filename)

Good Luck

---

### Post by louieb on 2007-04-13
> **guguma said:**
> Hello and good days, Since I have got no replies I have to post the method I have obtained. (are you guys angry that I choose ntloader over GRUB c'mon :))
Ah come on  NTLDR  is a pain in the as and you know it. But IMHO so is LILO and GRUB is only sightly less so.  Can't speak for the others but when I first started using Linux I must have spent a weeks worth of time reinstalling Linux because some update had messed up my menu.lst file and I did not know what it was or how to edit it. :confused:  But now I know how to use GRUB to dual boot. 
And thanks to your posting how you did it; the forum has a thread on using NTLDR to dual boo:popcorn:t. It all still looks like gibberish to me.

---

### Post by guguma on 2007-04-14
Thanks for your reply,

I actually renewed my computer I have a couple of Linux Distributions on it and I use GRUB.

You know it is all about learning I started using Linux seriously for about 3 months now (because I wanted to and it also became a necessity) and I am learning since.

NTLDR may suck. But people may want to use it, even if nobody will use it, its still a good thing to know one more little stuff right :).

Good Days and Good Luck to all.

---

### Post by ©TriMoon® on 2007-05-18
> **guguma said:**
> 3. I then called the simple shell provided in the installation CD and wrote "dd if=/dev/sda6 of=bootsect.lnx bs=512 count=1"
which is suggested in this very forum to create the bootsect.lnx file.

4. Then I am stuck I mean I really am stuck.

5. What can I do next or where am I totally messed up and can fix it.

Please Help 

Thank You
the only step you need todo next is to actualy write the bootsect.lnx to a floppy tobe able to boot from it.
Because you only have created a file containing the bootsector :)

---

### Post by RawMustard on 2007-05-27
This is how I've been booting linux for years until feisty came along :(  For some reason feisty does not like reading the boot sector of floppies.  :(

Does anyone know what commands to issue to re write the boot sector to a floppy so I can try to get dd to work.  I have two machines here I can't boot without the floppy in and I can't get the boot sector off them :(

---

### Post by guguma on 2007-08-14
There are 2 different ways to do it.

1. Boot with live cd, and copy the boot feile to a usb drive.

2. Or write it on your ntfs drive using ntfs-3g.

To use ntfs-3g, install it using synaptic and then 

```
sudo gedit /etc/fstab
```

and change ntfs to ntfs-3g.

You can do this second option with live or alternate install cd. Alternate install cd way is more cumbersome though.

---


---
title: "[SOLVED] Adding XP to GRUB isn't working..."
date: 2008-02-23
forum: General Help
---

### Post by kevinkokesh on 2008-02-23
Hi,
I have ubuntu 7.10 and Windows XP installed on one HD partitioned equally for each OS.

Ubuntu is on (hd0,1) and finally successfully boots through GRUB. XP is on (hd0,0) and I tried adding it to the end of **/boot/grub/menu.lst** by doing the following that was suggested on several other threads:

```
title        Windows XP
root        (hd0,0)
makeactive
chainloader    +1
```

When I reboot, the GRUB boot screen shows the timer counting down to my default boot option (Ubuntu) and the option to press Esc to get the boot list. I press Esc to try to boot Windows XP. Windows XP shows up as it should at the end of my boot list and I scroll down to it and press enter.

The odd thing that happens next is that it goes back to the GRUB boot screen and begins counting down again. I can either press Esc and keep going in circles like that or simply wait for the timer to expire and it boots into Ubuntu. Basically, I have a Windows XP entry that doesn't do anything, nor does it produce any error message.

Does anyone know what might be causing this? The only thing I can think of right now is that **(hd0,0)** might need to be (sd0,0)??? I don't see why that would be but I've seen some people using sd instead of hd on their menu files.

Thanks!

---

### Post by lha on 2008-02-23
It sounds like you have installed grub on (hd0,0), since chainloading boot sector of (hd0,0) loads grub. I'd try if using Windows' fixmbr and reinstallation of grub to (hd0) helped.

---

### Post by kevinkokesh on 2008-02-24
I remember installing grub to hd0 by typing **setup (hd0)**, so I would think it's on the whole HD and not just one partition? (I'm not too sure of how grub works so excuse my ignorance.)

[COLOR="DimGray"]The backstory behind this is that I had ubuntu on the HD then created a new partition for XP. The XP installation, of course, wrote the Windows bootloader over grub and so could only load XP. To alleviate this I went into the Live CD terminal and did a grub setup (hd0) to reinstate grub as the bootloader.[/COLOR]

One thing I just thought of is that I added Windows XP to grub's menu.lst file *after* I did **setup (hd0).** Would that affect its ability to boot Windows? (i.e., do I have to do another setup (hd0)? [COLOR="DimGray"](I'm afraid of doing anything at this point without some advice as the first time I tried to reinstate grub as the bootloader it gave me error 17 for several days before I figured it out.)[/COLOR]

[COLOR="Navy"]@Iha: Wouldn't fixmbr just put the Windows bootloader back on as the default bootloader and only allow me to boot Windows?[/COLOR]

---

### Post by lha on 2008-02-24
> **kevinkokesh said:**
> I remember installing grub to hd0 by typing **setup (hd0)**, so I would think it's on the whole HD and not just one partition? (I'm not too sure of how grub works so excuse my ignorance.)

(hd0) refers to the mbr (master boot record) of your hard drive. It is in the beginning of your drive, before any partitions. Grub on mbr is usually the best option.

> **kevinkokesh said:**
> The backstory behind this is that I had ubuntu on the HD then created a new partition for XP. The XP installation, of course, wrote the Windows bootloader over grub and so could only load XP. To alleviate this I went into the Live CD terminal and did a grub setup (hd0) to reinstate grub as the bootloader.

Are you sure that you didn't install grub to (hd0,0), too? Because if you did, fixboot (if memory serves) could reinstall Windows' boot loader to (hd0,0), and (hopefully) leave mbr untouched.

> **kevinkokesh said:**
> One thing I just thought of is that I added Windows XP to grub's menu.lst file *after* I did **setup (hd0).** Would that affect its ability to boot Windows? (i.e., do I have to do another setup (hd0)? 

No, it does not have any effect.

> **kevinkokesh said:**
> (I'm afraid of doing anything at this point without some advice as the first time I tried to reinstate grub as the bootloader it gave me error 17 for several days before I figured it out.)
@Iha: Wouldn't fixmbr just put the Windows bootloader back on as the default bootloader and only allow me to boot Windows?

Well, yes. (It might require using fixboot, too.) It is possible to load grub from WIndows' boot loader. You'd have to install grub to (hd0,1), and then add grub to WIndows' boot loader using, e.g., [BootPart]("http://www.winimage.com/bootpart.htm").

---

### Post by kevinkokesh on 2008-02-27
> **lha said:**
> (hd0) refers to the mbr (master boot record) of your hard drive. It is in the beginning of your drive, before any partitions. Grub on mbr is usually the best option.

Well, yes. (It might require using fixboot, too.) It is possible to load grub from WIndows' boot loader. You'd have to install grub to (hd0,1), and then add grub to WIndows' boot loader using, e.g., [BootPart]("http://www.winimage.com/bootpart.htm").

I'm afraid I don't really understand what you're suggesting. You want to add grub to windows' boot loader so that I could pick either windows or grub, and then if i picked grub i would then pick ubuntu? I guess if that works technically, then I'm willing to do it. I always read not to mess with Windows' bootloader, just boot Windows via Grub. I would think there would be a fairly easy way to add Windows to the grub menu, right?

> **Iha said:**
> 
Are you sure that you didn't install grub to (hd0,0), too? Because if you did, fixboot (if memory serves) could reinstall Windows' boot loader to (hd0,0), and (hopefully) leave mbr untouched.


I know I did setup(hd0). I know I wouldn't have typed in setup(hd0,0) since I knew that was the Windows partition (I might have done setup(hd0,1) but I'm pretty sure I just did setup(hd0). Would that install it to hd(0,0) also?

I'm not really sure what to do because I'd rather just stick to grub if at all possible. If I restore Windows' bootloader to (hd0,0) then can I add it to the grub menu and have grub be the default at startup?

Sorry for the confusing post, I'm a bit lost. :)

---

### Post by confused57 on 2008-02-28
You might want to post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

and the boot entries in your menu.lst:
```
gedit /boot/grub/menu.lst
```

---

### Post by froy02 on 2008-02-28
Boot into Ubuntu, go to terminal then post the results of 'sudo fdisk -l'.

---

### Post by kevinkokesh on 2008-03-01
> **confused57 said:**
> You might want to post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

and the boot entries in your menu.lst

```
kevinkokesh@ubuntu:~$ sudo fdisk -l
[sudo] password for kevinkokesh:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006a56c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986    7  HPFS/NTFS
/dev/sda2            2340        4659    18635400   83  Linux
/dev/sda3            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

```

here are the entries in menu.lst

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dbc8e818-27f1-43c9-93b2-f2924f9c0bae ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dbc8e818-27f1-43c9-93b2-f2924f9c0bae ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,0)
makeactive
chainloader +1

```

---

### Post by confused57 on 2008-03-01
Your grub Windows entry looks OK, it "should" work...it does sound like what lha mentioned, somehow grub was installed to your Windows partition.  Try booting up your Windows install cd, then press "r" for recovery, and enter the command FIXMBR, then  FIXBOOT...this will overwrite your mbr, but see if Windows boots.  Then you should be able to use the Ubuntu live cd to reinstall grub's IPL to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by criskat777 on 2008-03-01
add the map section to your grub.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		MicroVirus WinBlows XP Pro
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

just to make sure WinBlows thinks it's the first OS in the boot order

---

### Post by Herman on 2008-03-04
:) Hello kevinkokesh,
I agree with lha and confused57, your /boot/grub/menu.lst Windows entry looks OK.
It is unusual that you need to press 'Esc' to get your GRUB menu to appear, you should place a hash symbol in front of the 'hiddenmenu' command in your /boot/grub/menu.lst do it will show automatically at each boot-up. Here's a link,  [hiddenmenu]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu").

It is unusual for a dual boot to have the 'hiddenmenu' command commented out, there is something odd going on here, and probably there was something different about your Windows boot sector for a while before Ubuntu was installed. I have no idea what it could be though.

As lha mentioned, it seems as if somehow grub was installed to your Windows boot sector as well as to the MBR, or the Windows bootsector is somehow corrupted to make it point back to the MBR or to GRUB. That's highly unusual to happen by itself, but I guess anything is possible. The only times I have heard of the symptoms you have described, it has been from GRUB being accidentally installed to Windows boot sector instead of to MBR, in every instance. So FIXBOOT should fix it.
 Try booting up your Windows install cd, then press "r" for recovery, and enter the command FIXBOOT...this will overwrite your Windows boot sector. and see if Windows boots. 

You can also read this web page,  [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") and download a file from there to make a special boot CD that will bypass both the MBR and Windows boot sector and even has a generic boot.ini and NTDetect.com and NTLDR in it. That wilkl amost certianly boot Windows for you for now until we find out more about what's wrong (if FIXBOOT doesn't do it).

Regards, Herman :)

---

### Post by kevinkokesh on 2008-03-05
Thanks for your replies. Looks like I'll try the FIXBOOT command. Is it necessary to specify the partition that I want it to fix? I looked [here]("http://pcsupport.about.com/od/termsf/p/fixboot.htm") for some basic info about FIXBOOT and they're saying to do **fixboot c:**. I'm almost positive Windows didn't identify the Windows partition as "C:" because ubuntu was on HD first..so it didn't install to C. Do I need to know the drive letter that Windows calls itself? I gleaned from the article that if I just type **fixboot** then it will fix the partition that I'm "currently logged into" (which I'm not sure what that means, since I would be booting from a CD.. I wouldn't be logged into anything, right?)

So do I just type fixboot or is there some additional information that I need to provide to the prompt?

---

### Post by Herman on 2008-03-07
I don't know, as far as I know every Windows installation in the world thinks it's in 'Drive C:\ '. 
I don't know how Windows differentiates between the different 'Drive C's' when there's more than one in the same computer.
I do know that we use the 'hide' and 'unhide' commands in GRUB to stop one Windows from being aware of the other's existence when there are two Windows in the same hard disk.
I would just try with 'FIXBOOT C:\ ' first and see if ti works and if it doesn't do anything I'd google some Windows forums and try to find more info on FIXBOOT or the recovery console.

Regards, Herman :)

---

### Post by dacheng on 2008-03-08
Not sure if this helps anyone, but here goes:

This worked for me:
> title MicroVirus WinBlows XP Pro
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

When I installed Ubuntu and Windows, I took extra precaution to make sure they were on different hard drives and they did not see each other until they were both installed.  i.e. I first installed Ubuntu on hd0.  After it's done, I unplugged it from the computer and installed Windows in hd1.  I had to go into BIOS to fiddle with the boot sequence in order to have Ubuntu or Windows boot up.

The reason I did this was to divorce any dependence of one OS from another, so if I feel like it, I can just unplug any HDD and the other HDD will run as if nothing happened.

My grub menu was by default hidden, since when I installed Ubuntu there was no other OS.

Since I want Ubuntu to be the default, I manually added an entry to my grub/device.map and grub/menu.lst, and now my grub loader can go into Windows.

---

### Post by kevinkokesh on 2008-03-09
Great! Everything worked perfectly by applying the **fixboot c:** command. Thanks to everyone that helped, especially confused57 and Herman. As for the hiddenmenu..
> It is unusual that you need to press 'Esc' to get your GRUB menu to appear, you should place a hash symbol in front of the 'hiddenmenu' command in your /boot/grub/menu.lst do it will show automatically at each boot-up. Here's a link, hiddenmenu.

It is unusual for a dual boot to have the 'hiddenmenu' command commented out, there is something odd going on here, and probably there was something different about your Windows boot sector for a while before Ubuntu was installed. I have no idea what it could be though.

I didn't see anything commented out in the menu, but it works fine for my purposes. I wanted it to boot to ubuntu by default, which is what it does after the timer runs out. Pressing esc isn't a big problem for me. Thanks for your help on that, though.

:)

---

### Post by Herman on 2008-03-10
:) Okay, I'm glad you have things working the way you want, well done.
Happy Ubuntuing!
Regards, Herman :)

---


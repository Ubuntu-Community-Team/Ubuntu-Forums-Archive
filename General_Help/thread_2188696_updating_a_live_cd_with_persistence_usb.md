---
title: "updating a live cd with persistence usb"
date: 2013-11-18
forum: General Help
---

### Post by user987 on 2013-11-18
i am running a live cd  linux OS with persistence on a 8g usb flash drive.
Can i update  the the OS on the flash drive?
This is not a full install run usb.

---

### Post by varunendra on 2013-11-20
You can install applications and update them, but not the kernel. Kernel is frozen on a live system, can't be updated. This is by design.

---

### Post by Bucky Ball on 2013-11-20
Then you are running a LiveUSB and not a persistence install on a USB. That is Ubuntu installed on a USB like you would install it to a hard drive. I take it you are booting from the USB and either 'Try Ubuntu' or letting it get to the desktop? You still have the option to install USB to a hard drive?

---

### Post by user987 on 2013-11-20
i click on the update in the system setting and it seems like you say my application updated, meaning google chrome browser.

But some items fail so i assume that was the kernel?

Also is it secure to check email and do internet banking or purchases running this way?

I know if i do a full install to internal hard drive and update the system it would be secure but live CD with persistance , maybe not? 


If not , why?

Thanks in advance.

---

### Post by varunendra on 2013-11-20
> **user987 said:**
> Also is it secure to check email and do internet banking or purchases running this way?

I know if i do a full install to internal hard drive and update the system it would be secure but live CD with persistance , maybe not?

In my personal opinion, the 'non-persistent' mode is the most secure way to do internet banking and similar things. It 'Forgets' everything accumulated during a running session and always starts fresh, thus neutralizing any hacking attempts that may take more than one session to escalate the attacker's privileges to dangerous levels.

Persistent Live USB (as well as an installed system) has the advantage that it can be regularly updated with latest security patches, but then it can also get affected with malicious code if an attacker somehow succeeds to inject it (in the browser or a program) during a session. In a non-persistent session, a reboot and everything is fresh again.

Perhaps there could be a way to get the best of both modes (persistent & non-persistent), where you can update the system when you wish, then mount the persistent part in 'Read Only' mode during a normal session, thus NOT accumulating/remembering anything other than an intentionally done update. But I don't know how to do that. The nearest thing I know is to simply create a fresh Live USB with the latest 'Point Release' of an LTS (of course I'm talking about Ubuntu only).

---

### Post by user987 on 2013-11-20
Sorry to be long winded but new to using Linux.
I assume that when i see update available and i do a update, i get all the security patched that goes with the current live CD usb flash drive with persistent version that i am running.

In my case the LTS kernel (OS) version.


For example if using 12.04 LTS liveCD with persistent usb flash drive when i update all the security for this version is done.

But it will not update the kernel (OS) to 13.04 version. Is this correct assumption?

---

### Post by Bucky Ball on 2013-11-20
No, it won't. You can run:

```
sudo apt-get update
sudo apt-get upgrade
```

... and that will update the current system and upgrade any packages *for the current release only*, that need to be upgraded. It will *not* upgrade you to the next release.

---

### Post by varunendra on 2013-11-20
To elaborate what BB said, a persistent live setup can be updated for everything except the Kernel (2.x.x-xx, 3.x.x-xx etc.) _AND_ Release (12.04, 12.10, 13.04, 13.10 etc..). In this description -

**OS** is Ubuntu,
**Release** is its version (for example, 12.04),
'**Point Release**' is an updated officially released version of an [LTS Release]("https://wiki.ubuntu.com/Releases") (12.04.1, 12.04.2, 12.04.3.. etc.), and
**Kernel** is the main Linux engine that a release uses.

The OS (or a Release or Point Release) goes through several Kernel updates (which is recommended but not necessary) before a whole new version of its Release comes out.

Release is not the same thing as Kernel. Kernel is just the engine whose new versions keep coming out every month or so. In a normal (full) installation, they are part of normal updates and get upgraded without changing the version of Release *(for example, Ubuntu 12.04 LTS originally came with kernel 3.2.0-19 (if I remember correctly), and is currently using a much newer kernel, with many different kernel versions in-between).*

So your assumption is partly correct, but is slightly misleading due to misunderstanding of the terminology. Hope the above explanation clarifies that. :)

A few more things that may be interesting for you -

[INDENT]**1)** In a Persistent Live installation, the persistent part is stored to and read from a file or partition called "casper-rw". This file or partition is mounted as your root File System that contains all the directories that are part of a Linux FileSystem hierarchy. All the changes, updates you do are stored in this area and are read when you boot the Live session with "**persistent**" flag (a command line argument supplied to the kernel booting command line).

**2)** This "persistent" flag is added permanently to the boot configuration file (syslinux.cfg, or another file it includes) when you create a 'Persistent' live USB. But it can also be added temporarily to a non-persistent live session while booting by manually typing "persistent" at the kernel boot line (which you can get by going to [advance booting]("https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line") mode). This flag tells the boot loader to look for a file or partition that is named "casper-rw", and try to mount it as the root file system. Since you are new to Linux, this "mounting" stuff can be confusing for you in the beginning, so let's not go into its details for now.. :)

**3)** When you do an update on the Persistent Live system, all the changes go to this "casper-rw" file (which is a virtual file system as explained above), not the original structure of the Linux File System hierarchy that always remains at defaults. This virtual File System (contained within the casper-rw file/partition) is an exact copy of the original Linux File System, the only difference being that it can store changes.

**4)** As such, if you boot without the "persistent" flag, the "casper-rw" file/partition is ignored and the Live session boots with the original directory structure where the directories are either empty or at defaults. Thus the whole session is at its original defaults, not aware of 'ANY' updates you did in a previous session. Thus also not getting any benefits of the security patches you might have got during an update in the previous session.

**5)** Lastly, just as you can 'add' the "persistent" flag temporarily to a non-persistent session (for example, the one running off a live CD/DVD or a non-persistent USB) by editing the kernel boot line, you can also 'remove' this flag from the boot line of a persistent setup, thus making it ignore the "casper-rw" file/partition and load with the original defaults - all fresh, but not updated. Since it does not have to read and mount the virtual File System (casper-rw) and load the custom applications/configuration from there, it boots significantly faster.[/INDENT]

Hope I didn't confuse you even more. ;)

---

### Post by user987 on 2013-11-21
Varunendra,
                 I really appreciate the detail information, i need a little time to absorb it.

but seem from what you say my update did not get the security patches?

Even though the OS tells me no new updates since my update 2 days ago, so i guess i have to run the 2 commands that BB mention to really be updated in the live cd with persistence flash drive?

---

### Post by varunendra on 2013-11-21
The update via gui is the same thing as doing "apt-get update" and "apt-get upgrade". But it won't harm doing it again (via those commands) if doubtful. And those updates do contain security patches by default, although sometimes not all of them, since some of the security patches are done in the kernel itself which can't be updated on a live install.

---

### Post by user987 on 2013-11-23
I think i understand how the update work except for point release as it apply to 12.04 long term support.

I now know kernel and release do not get updated in liveCD with persistence, but point release like 12.04.1, 12.04.2 and so on do they get updated?

Also is there anyway to get some of my post from a year or so, there was some answers to my post that i like to see, but it seems i can only access recent posts

Thanks in advance, this has been very educational.

---

### Post by varunendra on 2013-11-23
> **user987 said:**
> ....point release like 12.04.1, 12.04.2 and so on do they get updated?
No they don't, as the point releases are specially related with driver and kernel updates. No kernel upgrade = no point release upgrade.

> Also is there anyway to get some of my post from a year or so, there was some answers to my post that i like to see, but it seems i can only access recent posts
In "Advanced Search" page (Search Single Content Type), fill in your User Name (3rd field from top), and change "Find Posts" field (3rd last) to "A Year Ago" .. "and Older".

Your first post (your own [thread]("http://ubuntuforums.org/showthread.php?t=1743781")) seems to be posted on April 30, 2011, and then you seem to have posted many different threads on same or similar topics at different times.

---

### Post by user987 on 2013-11-25
Varun,
          Thanks for all your answers.
I think i am at the point i will switch over to Linux completely from my win XP OS.

I know if i do a full install on the internal HD or a USB flash drive , i will get the kernel and LTS point release updated.

But what if i use   persistence live CD usb flash drive with the latest 9 month cycle ubuntu (example 13.10) and update it and then use a new flash drive live CD with persistence when a new version comes out (say 14.10 ) the next 9 month.

Is this a good alternative to use Ubuntu, because i have a few computers, some with Window XP others with Vista.

This way a LiveCD with persitence usb flash drive running a 9 month cycle , i can boot up any of those computers with great portablity and get latest OS with security patches.

Does this make sense to you? 

Pro or Cons on what i want to do?

---

### Post by varunendra on 2013-11-25
> **user987 said:**
> But what if i use   persistence live CD usb flash drive with the latest 9 month cycle ubuntu (example 13.10) and update it and then use a new flash drive live CD with persistence when a new version comes out (say 14.10 ) the next 9 month.
Sounds good to me.

However, if it is just portability why you want to stick with live install, be informed that a full install of Ubuntu/Linux is just as portable until you install proprietary drivers.

Both the live and full installations *may* face problems if you install proprietary drivers on them, especially graphics (will boot fine on the computer for which the driver was installed, *may* not as well on other hardware). For best compatibility, choose 32 bit so that it can be used on older machines too.

> Pro or Cons on what i want to do?
Here (almost a copy-pate from **C.S.Cameron's [post=10293555]post[/post]**, with some added points) -

[Note that the portability factor is generally same for both]

**Advantages of a [COLOR="#000080"]Live Persistent install[/COLOR]:**
[INDENT]1) You can use the persistent pendrive to install Ubuntu to another computer.
2) A persistent install takes up less space on the pendrive. *(the size of source ISO + the size of persistent space)*
3) You can reset the pendrive by overwriting the old casper-rw file with a new one.
4) The install to pendrive takes less time.
5) Does less read/writes on the source media (runs mostly from RAM), thus prolonging its life. Ideal for flash drives
6) You can always choose to temporarily boot without persistence during boot time (see [post=12853363]post #8[/post], point 5), handy in case the persistent changes cause booting issues.
7) Doesn't ask for password while running administrative tasks. ;)[/INDENT]

**Disadvantages of a [COLOR="#000080"]Live Persistent install[/COLOR]:**
[INDENT]1) Can't update/upgrade the kernel.
2) The applications can be updated, but only as long as the updates don't depend on a newer kernel/headers, since those can't be updated.
3) Takes longer to boot, with unnecessary screens in-between that you have to skip every time you boot.
4) A persistent install is limited to a 4GB casper-rw and a 4GB home-rw persistence file, to get more persistence requires persistence partitions.
[/INDENT]

**Advantages of a [COLOR="#800000"]Full install[/COLOR]:**
[INDENT]1) You can update and upgrade.
2) If you have problems or wish to modify, the solution is the same as with an internal install, (You can ask for help in these forums).
3) No ugly startup / install screen.
4) Better security, you can encrypt home folder.
[COLOR="#FF0000"]5) You can use proprietary drivers.[/COLOR] (as per my experience, this is applicable to both full and persistent install, and pros/cons are same)
6) Hibernation works.
7) Boots faster, works faster, with more RAM available to work.
[/INDENT]

**Disadvantages of a [COLOR="#800000"]Full install[/COLOR]:**
[INDENT]1) Needs more space to install. 2 GB bare minimum and at least 4 GB to work effectively.
2) Does frequent reads/writes on the source media, thus not ideal for flash drives. No problem with normal hard disks though.
3) If something goes wrong with updates/upgrade, it may sometimes be impossible to revert/reset.
4) Asks for password everytime you do some administrative task. :P[/INDENT]

Hope I didn't miss any difference of critical importance.

---

### Post by user987 on 2013-11-27
Varun,
          Wow thanks for all the info.
I think i will proceed with a flash drive Live CD with persistence with the 9 month ubuntu OS for now to save on my flash drive R/W cycles.

If all goes well for a while, i will probably do a LTS OS full install on the internal HD of my old PC with XP .

I will probably stay with a Live CD and new persistence USB with the latest 9 month for my other PC with Vista so i don,t touch the internal HD.

One more thing with Live Cd with persistence Cameron say that the casper RW file can be overwriiten.

Meaning i guess when i do a file delete, or cookie purge i free all the casper RW memory and can use it to save new file and cookie?

---

### Post by bashiergui on 2013-11-27
> **user987 said:**
> Also is it secure to check email and do internet banking or purchases running this way?

I know if i do a full install to internal hard drive and update the system it would be secure but live CD with persistance , maybe not? If not , why? If all you do is bank with it then you would be fine. If you browse the internet then it would be no more secure than using a normal computer. If checking email means that you click on links and open documents emailed to you, then no. Anything you open that's malicious would persist just like on a normal computer.

---

### Post by sudodus on 2013-11-28
Hi user987,

In the long run most people prefer installed systems to live or persistent live systems.

There are tips about USB drives, if you want to run either way from a USB device at this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by varunendra on 2013-11-28
> **user987 said:**
> One more thing with Live Cd with persistence Cameron say that the casper RW file can be overwriiten.

Meaning i guess when i do a file delete, or cookie purge i free all the casper RW memory and can use it to save new file and cookie?

Consider the casper-rw file just like a partition (virtual) that is almost a mirror image of your root (/). So just like you can free space from your actual partitions by deleting files/cookies, you can do the same with the casper-rw file (when you boot with persistence, you are 'INSIDE' that file, seeing it as your root filesystem).

However, what C.S.Cameron meant is much more than that. The whole casper-rw file can be deleted or replaced with a new one. Of course this has to be done from another OS, because you can't delete the file when you are 'INSIDE' it (that is, while using the live usb in persistent mode).

Suppose you created a fresh live usb with persistence, and installed your most favourite applications on it, customized it to your liking etc. All these applications and settings are saved in this casper-rw file. Now you can keep a backup copy of this casper-rw file, and use it to replace the one in use on the live usb when it gets full or corrupt for any reason. Whenever you want to return to the exact state when you took the backup, just replace the casper-rw file with a copy of the backup.

This is just one example of how you can take advantage of this flexibility. Another use may be to keep multiple backup copies of the casper-rw file with different sets of applications/settings. Of course these copies will be compatible with only that version of Ubuntu on which they were prepared.

---

### Post by C.S.Cameron on 2013-11-29
Thanks  varunendra, You have added some valid points, (although I have not been able to add Nvidia drivers to a persistent install myself).

The main disadvantage I see running a Persistent CD, is that boot and operating speeds are much slower than with Full and Persistent USB's, oh, and they scratch.

---

### Post by user987 on 2013-11-29
Varun, and everybody else thanks alot for your insight.

---

### Post by inhumangeek on 2014-10-06
Hi Cameron,

I have tried to create a persistent Live USB installation of Ubuntu  14.04 however the persistence doesn't work. I looked at your post here [http://ubuntuforums.org/showthread.php?t=2124124](http://ubuntuforums.org/showthread.php?t=2124124) and followed the instructions _to the letter_  however the persistence still doesn't work, and I still get the  Try/Install splash screen. Has something changed for 14.04? Does the  whitespace formatting of the syslinux.cfg file matter?

 I read somewhere else that there is a limit of 4GB for the persistence  file - does this mean that the partitions you have mentioned each have  to be less than 4GB? My USB stick is 32GB so I end up with a 2, 4, and  approx 26 GB FAT32, casper-rw, and home-rw respectively; would this  partition size be causing problems? 

Any tips gratefully received. Many thanks.

P.S. In your post when you ask "do you see a casper-rw file" do you mean  the folder in the first partition, a file in the root directory, or the  second partition (called casper-rw as per your instructions)?

---

### Post by varunendra on 2014-10-06
Hi inhumangeek,

I hope it's okay if I chip in a little info while Cameron is away.
> **inhumangeek said:**
> I have tried to create a persistent Live USB installation of Ubuntu  14.04 however the persistence doesn't work. I looked at your post here [http://ubuntuforums.org/showthread.php?t=2124124](http://ubuntuforums.org/showthread.php?t=2124124) and followed the instructions .... Does the  whitespace formatting of the syslinux.cfg file matter?

The 'syslinux.cfg' file no longer contains the booting line. It now uses the modular programming technique, means some of the contents it is supposed to have are now scattered across different files for easy maintenance. If you didn't notice yourself, it only contains a line "include menu.cfg", which means "also include the contents of the 'menu.cfg' file. Now this 'menu.cfg' file further includes the contents of another file - 'txt.cfg'.

Now this **'txt.cfg'** file is where you should see the booting line, the place where you are supposed to put the "**persistent**" flag. This file may look like this (copy-pasted from a Xubuntu Live USB) -
```
default live
label live
**menu label ^Try Xubuntu without installing**
kernel /casper/vmlinuz
**[COLOR="#0000FF"]append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --[/COLOR]**
label live-install
**menu label ^Install Xubuntu**
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
label check
**menu label ^Check disc for defects**
kernel /casper/vmlinuz
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
**menu label Test ^memory**
kernel /install/mt86plus
label hd
**menu label ^Boot from first hard disk**
localboot 0x80
```
The line highlighted in blue is where you should put the word "persistent" among other flags. It should look like -
```
**[COLOR="#0000FF"]append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz [COLOR="#FF0000"]persistent[/COLOR] quiet splash --[/COLOR]**
```

Note that I intentionally put the word "persistent" just before "quite" and "splash" as against the post that you followed where it is right after "boot=casper". This is just to emphasize that it doesn't matter where it is put as long as it is separated from other flags by blank spaces and comes BEFORE "--" in the last.


Please try this and assuming you have did the partitioning part correctly, it should work right away.

**PS:**
You can also add the "persistent" flag in temporary mode during boot time. See points 2 and 5 of post #8.

---

### Post by inhumangeek on 2014-10-07
Varun,

Thanks very much for your help and quick reply. Unfortunately I am still having problems. I have tried what you/Cameron suggested:
1) Use gparted to partition memory stick: 2GB FAT32; 4GB ext4 (casper-rw); and 24GB ext4 (home-rw) (screenshot attached)
2) Use startup disk creator with said memory stick (it only allows me to use the first partition), with *no* persistence
3) Change contents of txt.cfg to include the word "persistent" where indicated.
4) Boot to from USB, add a file to home area, reboot and it's gone.

I might try doing a full install instead, unless you have any other suggestions?
[ATTACH=CONFIG]257015[/ATTACH]

Many thanks again,
Paul

---

### Post by yancek on 2014-10-07
> I read somewhere else that there is a limit of 4GB for the persistence  file

That only applies to FAT32 partitions.  If you use ext2 or another Linux filesystem it can be larger.

> In your post when you ask "do you see a casper-rw file" do you mean  the  folder in the first partition, a file in the root directory, or the   second partition (called casper-rw as per your instructions)? 		

There is a casper directory/folder in any Ubuntu Live CD, the persistence file shows as a file and it is labelled 'casper-rw' and needs to be all lower case.

---

### Post by varunendra on 2014-10-07
> **inhumangeek said:**
> 
2) Use startup disk creator with said memory stick (it only allows me to use the first partition), with *no* persistence
The startup disk creator works only with FAT/FAT32 partitions, and I think it doesn't have to be first one. But that's not the problem here.

An easier approach might be to simply create the Live filesystem again _WITH_ Persistence this time. This will automatically create the files and settings the way they should be. Of course you must make the size of the FAT32 partition bigger to do this. I suggest deleting the 2nd partition and expanding the FAT32 partition to cover the area.

Once it is created and working, delete the "casper-rw" file from the Live partition > run GParted (from another source, not from the target Live USB itself) > shrink the FAT32 partition again > create a fresh EXT3/4 partition > label it "casper-rw" > Done!

But it would be interesting to see what may be wrong in your current approach to do it all manually. Could you post the contents of your syslinux.cfg and txt.cfg files before trying above?

---

### Post by inhumangeek on 2014-10-08
Hi Varun, 
I'll try what you have suggested and let you know. Unfortunately I have been playing with the usb stick and don't have the cfg files. 

Many thanks!

---

### Post by inhumangeek on 2014-10-11
> **varunendra said:**
>  simply create the Live filesystem again _WITH_ Persistence this time. 

So I have tried this again but the persistence still doesn't work, back to square one really. I have attached syslinux.cfg and txt.cfg from the vanilla installation, created with a 4GB persistence file. (I notice that there are two syslinux.cfg files, one in the root of my USB and one in the syslinux folder). There is a casper-rw file in my root, if that is important.

Just to reiterate what I have done: I simply booted from a (lubuntu) LiveUSB, created a second LiveUSB startup disk (on a second USB stick, 100% FAT32), and used the persistence setting. Since my last message I have also tried doing it from a Windows PC using UNetBootin, again selecting persistence, but it also doesn't work. Can there be something wrong with the current 14.04 image?!

> **varunendra said:**
> Once it is created and working, delete the "casper-rw" file from the  Live partition > run GParted (from another source, not from the  target Live USB itself) > shrink the FAT32 partition again >  create a fresh EXT3/4 partition > label it "casper-rw" > Done!

Didn't get to this part because I didn't get it working. 

syslinux.cfg (_in root folder_):
```
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash -- persistent

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry1
menu label ^Try Ubuntu GNOME without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu-gnome.seed boot=casper  quiet splash -- persistent

label ubnentry2
menu label ^Install Ubuntu GNOME
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity  quiet splash -- persistent

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit  persistent

label ubnentry6
menu label Try Ubuntu GNOME without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash -- persistent

label ubnentry7
menu label Install Ubuntu GNOME
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash -- persistent

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash oem-config/enable=true -- persistent

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- persistent


```

syslinux.cfg (in syslinux folder):
```
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
```

txt.cfg:
```
default live
label live
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
label live-install
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
label check
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
menu label Test ^memory
kernel /install/mt86plus
label hd
menu label ^Boot from first hard disk
localboot 0x80


```

Thanks again

---

### Post by varunendra on 2014-10-11
> **inhumangeek said:**
> (I notice that there are two syslinux.cfg files, one in the root of my USB and one in the syslinux folder)
There shouldn't be. It seems you used unetbootin AFTER making it live with the native Startup Disk Creator, _without_ formatting it. Unetbootin doesn't format it for you, it simply copies the file and installs its boot loader.

Anyway, you don't need to go in those technicalities. I don't think there can be anything wrong with the startup disk creator since the 'txt.cfg' file seems to be okay. It is the 'syslinux.cfg' file created by unetbootin that is not okay. The "persistent" flag is [COLOR="#FF0000"]after "**--**"[/COLOR], while it should be before it as I already pointed out very clearly earlier -
```
append initrd=/ubninit file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash **[COLOR="#FF0000"]-- persistent[/COLOR]**
```
Unless you did it yourself (the wrong way), it is the fault of unetbootin.

Please correct the position of the flag, or format the usb and use either unetbootin or the native startup disk creator, not both. It shouldn't be a problem but creates unnecessary confusion.

Making a Live USB persistent is one of the easiest things possible with it, you seem to be overthinking it.

---

### Post by sudodus on 2014-10-11
I think it is possible to have boot options also after --

It is used in order to separate options to be ported into an installed system. See this link

[https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line](https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line)

> The "**-- **" entry defines the boundary between  options  which are specific to the installer and ones that are copied to  the  target system. Often you would like to copy the boot option to the   target system, so add the option at the very end of the line, after  the "**-- **". 

But I'm not sure if it is also valid with Unetbootin. I think so, but I have not tested it.

-o-

If you are happy with a standard 4 GB file for persistence, please re-format the pendrive to FAT32 and start all over with either of the Ubuntu ***Startup Disk Creator*** or ***Unetbootin***. Just following the instructions in the graphical user interface should help you get there.

If you want more disk space for persistence, you can make a second partition on the pendrive, format it to ext2, ext3 or ext4 and give it the label casper-rw. Then run the Ubuntu ***Startup Disk Creator*** or ***Unetbootin***, this time without creating any persistence (you don't want the default file). Finally adding persistence as suggested by *Varunendra* should do the trick.

---


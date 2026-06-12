---
title: "Ubuntu &amp; Grub 1.5 is installed on an external harddrive, Error 21 when booting laptop"
date: 2006-11-10
forum: General Help
---

### Post by seriousstorm85 on 2006-11-10
I have installed Ubuntu 6.10 on my external USB hard disk.
I have my windows XP installed in my Laptop.

When I boot my laptop without turning on my external hard disk i get 

Error 21.

The reason for that is Grub 1.5 cannot be launched unless the external hard disk is turned on before booting my laptop.

I am able to use Ubuntu without any problems as well as XP.

But da problem i am having is when i wanna use my laptop when i am on da move, i can not boot windows as grub 1.5 is on the external hard drive. ](*,)

Can someone help me on this

Is it possible for grub 1.5 to be installed in my laptop HDD even though Ubuntu is on the external hard drive or is there a better way?

Thanks in advance.

---

### Post by catlett on 2006-11-10
Turn on the external usb drive and boot into ubuntu from your laptop. First find out which hard drive is your laptop. If you are unsure enter this in the termional```
 sudo fdisk -l
``` Once you know the harddrive, you can install grub with this command (just to have an example command, I am going to use /dev/hda as your laptop's partition)
```
sudo grub-install /dev/hda
```
Installing to hda is installing to the mbr. When you just list the drive i.e. hda then grub goes to the mbr. If you used a specific partition like /dev/hda1 then grub would install to the partition and not the mbr. This isn't what you want because grub needs to be on the mbr to boot your system.
Just make sure you know how the system labels your laptop's hard drive then use sudo grub-install to install grub to the mbr.
If this is done correctly you will be able to booot your laptop without the external hard drive. When you boot your laptop you will be able to access windows from the menu.

---

### Post by seriousstorm85 on 2006-11-10
my laptop device is /dev/hda1

My external hard drive is dev/sda1 (music, etc)
                          dev/sda2 (linux)
                          dev/sda3 (Linux swap)

I have used the command sudo grub-install /dev/hda1 but when restarted my with laptop (while the external hard drive is switched off)still got the same problem, "Error 21".


After installing the grub using this command sudo grub-install /dev/hda1

I get this in the terminal:-
 
(hd0)   /dev/hda
(hd1)   /dev/sda

So what  i also tried was changing the device.map file from (hd0) /dev/hda by adding "1" at the end of hda, and i saved the file and restarted my machine, I got the same problem "Error 21".

I have changed back the device.map file to what it was before.

Hope you can show me what i am doing wrong.

---

### Post by catlett on 2006-11-10
Just use hda. If you use hda1 it goes to a partition and not the mbr. Use this command
```
sudo grub-install /dev/hda
```
Also change your device map back to hda

---

### Post by seriousstorm85 on 2006-11-10
I have used sudo grub-install /dev/hda and changed back the device map.

When restarted my computer without the external hard disk, i still get Error 21.

But I restart the computer with the external hard disk, i get GRUB loaded up but now a bigger problem has risen.

When I select XP (on the laptop's internal hard disk (has no partitions just one)) it loops back to the grub again. I can only use Ubuntu only

---

### Post by catlett on 2006-11-10
I do not know why this is happening but it shouldn't be. Just so you know, this is the grub manual with the grub-install command 
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)
First let's trouble shoot a bit. Open up the grub menu and post it.
```
sudo gedit /boot/grub/menu.lst
```
Then go into your windows hard drive from ubuntu (if it isn't mounted  let me know and we can mount it) Look for a grub folder. If there, open it and post what is in it.
Open up the boot.ini file and post the contents.
Last, do you have a windows XP installation disk? Not a compouter maker (like dell or toshiba) recovery disk but a real XP install disk. I ask because the install disk has a recovery console that allows you to fix the mbr of an xp install.

That may be the way to get this right. It is a bit involved but it will end up working. Before we get to that, do you have an xp install disk and I assume your laptop has the ability to boot to a usb device, correct?

---

### Post by seriousstorm85 on 2006-11-10
First of all, I don't have an XP install disk, just the recovery disk. :-(

My internal harddrive(XP) is not visible when using ubuntu (unmounted).

And this is whats in the menu.lst of the grub in Ubuntu.

/*Stuff in the beginning */
default 0
time   10

/*Actual code in the menu.lst, this does not include the comments in the file*/
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by seriousstorm85 on 2006-11-10
And yea, the machine can boot to a usb device.

---

### Post by catlett on 2006-11-10
Let's mount your windows drive and look at the boot.ini and anything grub may have left there. 
Enter these commands in the terminal
```
sudo mkdir /media/windows
```
This command opens up a file. Put the next line into the end of the file
```
sudo gedit /etc/fstab
```
```
/dev/hda1 /media/windows  ntfs nls=utf8,umask=0222 0 0
```
```
sudo mount -a
```
Now go to the top panel and enter into Places>Computer>Filesystem>Media/windows Those are your windows files. Open up the boot.ini and look for any file from grub.
If you get an error during mounting, post it

---

### Post by seriousstorm85 on 2006-11-10
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by catlett on 2006-11-10
Let's quickly go in a different direction. Since you wanbt to be able to boot into windows when the usb is not connected this might be the answer, as well as getting you back to a dual boot. GAG [http://gag.sourceforge.net/](http://gag.sourceforge.net/) is a bootloader. It is a very small download. Extract the package and burn the iso file to a cd. Then boot to it. The prompts are straight forward. Gag will install on your laptops mbr. This way it will work when the usb sin't connected. Just run gag with the usb connected and powered on so it can see the ubuntu install 
Try this before we go further with the grub fixes.

---

### Post by seriousstorm85 on 2006-11-10
I tried booting the machine with GAG but to no avail, it still shows me Error 21.

My machine boots the dvd-rom first then the hard drive(s) then external drives then network.

I have burnt the cd twice, one time the cdrom.iso by itself, the other time buring all the files that where in the downloadable zip file.

Both times I still got error 21, except when the external hard drive is on.

When I select XP i still get the Grab stage 2 which then loops back to the grub screen in which Ubuntu still boots.

---

### Post by catlett on 2006-11-10
What happens when you select XP again after you get grub the second time? Meaning have you tried this...It boots to grub, you select XP. It loops to grub you select XP. Have you done that yet?
We may get lucky and the issue is you have grub twice. Meaning grub may be on the external and on the laptop. So you get it twice but hopefully you get to windows the second time.
Try selecting XP twice. I am trying to find you a boot disk with the rcovery console. The xp recovery console will solve this issue inb a second but we need to find a way to get it. In case I don't find a boot disk, do you know how to use a bittorrent client. You can download a copy of XP PRO, burn it to disk, boot to it and then get into the recovery console. Then we can fix your mbr on windows.
I have to try this boot disk real quick and then I'll post back. Try selecting XP twice for now.

---

### Post by seriousstorm85 on 2006-11-10
Yup, I know how to use torrents. I have got Azeurus installed in Ubuntu.

I will  download a copy of XP. but before I do that, my machine is windows HOME edition, is that relevant or should it work normally on the XP pro cd. I  have tried selecting XP twice, same old error 21. :-(

---

### Post by seriousstorm85 on 2006-11-10
I found this torrent. Dunno if this should do the trick if not, can you send me a link of the correct torrent file.

[http://isohunt.com/torrent_details/10766631/Windows+XP+boot+disk](http://isohunt.com/torrent_details/10766631/Windows+XP+boot+disk)

---

### Post by catlett on 2006-11-10
Home or PRO shouldn't matter. You won't be installing anything. Good Ole' Microsoft only put the recovery console on XP install disks. Nevermind very few people have one. Mine is from a bittorrent as well, I only had IBM recovery disks.
What I want you to do is fix your windows mbr and then put grub on the usb drive. What I am hoping for (actually this should work but the grub-install mess up has me cautious) is for your laptop to have the regular windows bootloader. That you turn on the laptop and it boots to windows. Then you plug in the usb drive and make sure your boot order is set to the usb drive. When you boot with the usb drive, grub appears and it boots to ubuntu.

Before you do the recovery console, lets fix the usb drive so it has grub on its mbr. Boot into ubuntu and do this 
```
sudo grub
```
This will give you a grub shell. At the grub shell, which looks like this grub>, enter these commands 
```
root (hd1,1)
```
```
setup (hd1)
```
```
quit
```
That puts grub on your external's mbr as well as in ubuntu's partition. Now the part of grub on your laptop can be removed and replaced with the windows bootloader.

Now do the recovery console. Boot to the XP install disk and enter```
 R
```at the prompt to enter the recovery console. Follow the prompts and when you get to the command line, enter ```
FIXMBR
``` This web page has screenshots [http://www.geocities.com/kilian0072002/recconsole2.html](http://www.geocities.com/kilian0072002/recconsole2.html)

Now if everything went correctly XP can boot from the laptop and ubuntu can boot with grub from the usb external. Post with any errors or questions. Hopefully we are in the home stretch,

---

### Post by catlett on 2006-11-11
> **seriousstorm85 said:**
> I found this torrent. Dunno if this should do the trick if not, can you send me a link of the correct torrent file.

[http://isohunt.com/torrent_details/10766631/Windows+XP+boot+disk](http://isohunt.com/torrent_details/10766631/Windows+XP+boot+disk)

Jusr get an XP install disk. You don't need a boot disk. Get the xp pro off this site. [http://isohunt.com/torrents/?ihq=windows+xp](http://isohunt.com/torrents/?ihq=windows+xp) Make sure it is the install disk and not just an activation crack. Look for a 700mb file or a 600mb or so file.

---

### Post by seriousstorm85 on 2006-11-11
THANKS ALOT MAN, U R THE BEST. :-)

I will update you on my progress tomorrow. Sorry for being an annoyance :-(

---

### Post by catlett on 2006-11-11
You are not an annoyance at all. I would never leave you with a system not booting correctly. I think the issue comes from using grub-install hda1 instead of hda but the recovery console should take care of that.
Post tomorrow if you have issues. I'll be checking in throughout the day.

---

### Post by seriousstorm85 on 2006-11-11
I have booted up the laptop with the XP disk.

I have got to the point where it says type "R" for recovery console.

I have selected R.

I then types FIXMBR.

It asked me if I wanted to proceed.

I type "y".

After that is said showed me the device that MBR was affecting

\device\Partition0\HardDisk0

I then typed "Exit".

When it booted my machine (with external hard disk is on) it showed me "Grub...Stage 2" then the usual grub list.

The unusal thing in here is, Grub stage 2 never appeared before, it only used to appear after selecting XP.

Anyhow, XP still loops back to the grub. :-(

As a last resort, in my XP hard drive I have only applications installed. All my stuff is in the external hard disk (partition different to Ubuntu's partition) so i am not loosing anything by formatting my internal hard disk.

Is this wise to do or is there hope to hang on to and see if the current XP can be saved :-0

---

### Post by catlett on 2006-11-11
If you do not have any important data, re-format and install again BUT before you do that, install grub entirely to the usb device. The external drive is using data stores in the laptop for booting. If you reformat, grub will have issues because the data it wants is not there. To solve this issue, install to the usb's mbr with the last commands I gave you 



```
sudo grub
```

This will give you a grub shell. At the grub shell, which looks like this grub>, enter these commands


```
root (hd1,1)

```


```
setup (hd1)

```


```
quit

```
Once you do that, reformat and reinstall XP. Make sure your bios has the usb device first in the boot order.

---

### Post by EliteGamer on 2006-11-11
I had a problem similar to that.  The problem however had nothing to do with my drives even though i was getting hard drive errors.  My cd player for some reason was making everything go funky. What i did to fix it was just get an external cdrom player and the problem was fixed.  It probaly doesnt relate to your situation but just wanted to share in case you are having that same problem.

---

### Post by seriousstorm85 on 2006-11-11
in the bios, it picks up the external hard disk as part of the hard disk and not external drives.

When expanding the hard disk in the BIOS it shows me the 2 hard drives rather than showing me the internal hard disk.

i will still make the removeable device ahead of Hard disk but below CD-DVD-ROM. In order to use the XP intsall disk.

---

### Post by catlett on 2006-11-11
> **seriousstorm85 said:**
> in the bios, it picks up the external hard disk as part of the hard disk and not external drives.

When expanding the hard disk in the BIOS it shows me the 2 hard drives rather than showing me the internal hard disk.

i will still make the removeable device ahead of Hard disk but below CD-DVD-ROM. In order to use the XP intsall disk.

The reason for the usb being ahead of the hard drive is so when you wnt to boot to ubuntu. If the hard drive is first, you won't get grub. It will boot right to windows after the xp install is finished.
For now you can put the cd first so you can boot the install cd

---

### Post by seriousstorm85 on 2006-11-11
Ok, I have good news and i have bad news.

The good news.

XP works now.

1) When starting the laptop while removable disk is off, XP is booted and no Error 21 :-)

2) When switching on the external hard drive while XP is on, I am able to retrieve my stuff from the external hard drive (ubuntu partition is unseen as usual).

3) Restarting the laptop using the follwoing lineup 1) Dvd-Rom 2) Removable Disks 3) Hard disks 4) Network

I don't get to see Grub 1.5 but i get directly into XP which is a good thing as well, incase i turn on the external hard disk before the laptop, i won't be getting grub but XP instead. Something is fine by me, because I have a Bios password enabled so by da time i enter da password I will press f2 to change the boot lineup in Bios or press F12 and then get the boot option and I can then choose which boot i want. :-)

4) When in Bios and expanding the Hard disk, i get to see it in this order Toshibaxxxx then Samsungxxxx.

When changing the order so the external one (samsung) is first, i can then get to load Grub 1.5 rather than automatically loggin on to XP. :-)



NOW THE BAD NEWS.

When selecting Ubuntu i get this

"unknown partition" even though Ubuntu partition is still in the external hard drive. :-(

When selecting XP from GRUB its not recognized. (i can live with that) as xp can be loaded up by changin the hard disk order and no grub is needed. :-)

---

### Post by catlett on 2006-11-11
First install the ext2 driver so you can access your ubuntu partition from windows. [http://www.fs-driver.org/](http://www.fs-driver.org/) It is pretty simple to use. Run the install and then you will give the linux partitions a drive letter. Then it will show up under My Computer as anothe local disc.. If you need to accesss the driver application after thge initial run, it is found in the Comtrol Panel. It is easiest to see when you switch to Classic View.
Next try getting back grub with this method [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) I was hoping the setup hd1 command would have worked before but obviously it didn't.  As long as you don't enter hd0 or hda XP's drive won't be touched. You may want to look at the menu.lst before you run the setup just to see if their is an obvious error that can be fixed before running the 'how to' method. Check the device map and the menu.lst to see if the partitions are labeled right.

---

### Post by seriousstorm85 on 2006-11-11
The menu.lst seems ok to me


title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


The device.map seems ok aswell

(hd0)	/dev/hda
(hd1)	/dev/sda



Will start loading the live cd now.

/*fingers crossed*/

---

### Post by seriousstorm85 on 2006-11-11
Before I do anything,

Is the code for the windows OS in the grub necessary?

Because if i can boot XP while the external hard drive if off or on and the internal hard disk is higher in the order then there is no need for it to be shown in grub, correct?

so can i remove the code for the XP in the menu.lst

---

### Post by catlett on 2006-11-12
Yes. When it is done, xp will boot on it's own and grub will be on the external drive, entirely.
In the futurer, if you want xp, boot with the external powered off and the boot will go to windows bootloader. Boot with the external powered on and with it first in bios boot order for booting ubuntu.

---

### Post by seriousstorm85 on 2006-11-18
I have tried the steps u told me from this post [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351).

And it didn't work, i still kept getting the Error 22 "Partition not found.

So what I did was since I don't have anything important installed in Ubunutu I formatted my previous Ubunutu partition (via windows) then loaded up the live cd and went through the installation process. I have set up a new patition from the previous ubunut.

The setup was complete (also chose to make the grub load from (hd1) and not (hd0).
 

However when I tried to use Ubuntu from the grub same error 22 :-(

is there any hope? :-(

---

### Post by seriousstorm85 on 2006-11-21
I have managed to fix da prb.

Da prb was ubuntu was installed in my external harddisk (hd1,1).

So when i wanted to load the grub, i used to change the hard drive rank making my extternal harddisk ahead of my internal harddisk. 

So what i had missed was when the change of rank happened my external harddisk became (hd0) and my internal harddisk as (hd1).

So to successfully load Ubuntu and not get da Error 22 "Unable to find partition).

I changed the menu.lst (in the ubuntu in my external harddisk from (hd1,3) to (hd0,3) via the live cd.

Now it boots perfectly.


*Incase ur having Error 22, and u know dat u have ubuntu installed in ur computer.

In da grun splash screen select 

"c" to open the command line and search for da menu.lst

/boot/grub/menu.lst

which ever partition is found in, thats ur ubunutu OS.

just edit the boot of the ubuntu in the grub using "e".

And Ubuntu will be loaded successfully.

---


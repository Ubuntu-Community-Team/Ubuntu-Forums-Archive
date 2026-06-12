---
title: "Grub error 17"
date: 2007-05-14
forum: General Help
---

### Post by AmericanYellow on 2007-05-14
After installing Ubuntu on my hard drive( dual booting with Windows XP) I got the Grub 1.5  Error 17 message. Spent 2 days pulling my hair out trying to figure out why I got the error. Browsed the Ubuntu forums, saw good advice, but nothing help. I was just about to give up on Ubuntu, until I just started messing around with my PC and surprisingly :) :) :) :guitar:  the error was gone! Here's what I did:

For ASUS P4S333 motherboard:

1. Enter BIOS
2. Make sure all HDD's are detected.

* *Take note of (write down) the current settings just in case you need to set things back later**

3. Search for the HDD that has Ubuntu installed and set its MODE to AUTO (not LBA, large, or normal)
4. Also, if you have this option available, set TYPE to USER, but don't change any of the figures that were automatically detected.
5. And you are done!


Just in case this doesn't work, then:
6. Set all drives to TYPE --> USER and MODE --> AUTO (not LBA, large or normal)


I just took the time to post this because of the all the trouble I when through for something so simple to do. I hope that this post helps.....

---

### Post by Herman on 2007-05-14
Thanks AmericanYellow,
You did a wonderful job finding that out and passing it on. You typed it out nice and clearly too. I have added a link to this thread to my Super Grub Disk Page's collection of Grub Errors and some possible solutions to them. Here's the link, [     Grub error 17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17"). It might help someone there too. I hope that's okay. If you want it edited differently or if you object, please let me know.

Regards, Herman :)

---

### Post by SPBesui on 2007-07-10
AmericanYellow,

I'm also getting Error 17 and can't boot beyond that.

In your instructions Step 1 is "Enter BIOS" but I'm not sure exactly what you mean.  I can enter the Setup menu at boot, and it looks just like [this image from Wikipedia (Phoenix AwardBIOS)]("http://en.wikipedia.org/wiki/Image:Phoenix_-_AwardBIOS_CMOS_Setup_Utility.jpg"), but I don't see any options for setting the MODE to AUTO for the HDD's.

Am I looking in the right place?  If so, how do I change the settings as described in your post?

---

### Post by Herman on 2007-07-10
Hello SPBesui,
Just in case AmericanYellow is away from the computer for a while, maybe I can help. By co-incidence I have an Pheonix Award BIOS too. Take a look in this link and see if that helps you, [BIOS Page.]("http://www.users.bigpond.net.au/hermanzone/p1.htm")
Regards, Herman :)
.

---

### Post by SPBesui on 2007-07-10
Thanks Herman, I got the same answer on another thread but your link is much more detailed.  I'm at work at the moment but I'll give it a shot when I get home.  Appreciate the help.

---

### Post by sub7 on 2007-07-25
I now have this error and my BIOS isn't capable of modifying any HDD settings that you people are talking about.
I have not touched any BIOS/CMOS settings while i have been using Ubuntu, i have not played with any special settings at all and it won't even get to the OSboot menu.
I now lose weeks of hard work and am completely disillusioned.

[IMG]http://lab.zio-matrix.net/doc/doc-img/se7505vb2/se7505vb2_bios_main.gif[/IMG]

Similar except i dont have that system menu option.

---

### Post by Herman on 2007-07-26
Hello sub7,
So you have GRUB error 17? 
Did you already check the usual causes of GRUB error 17? You haven't specifically stated whether you already tried the most common cause and remedy already.  The cause and solution mentioned here in this thread is rather out of the ordinary, and is the next step after the regular solution doesn't work.

Please make sure you have read this link first, [     Grub error 17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17"), and i9f you need specific help then you might post a copy of the output from sudo fdisk -lu here please, along with a copy of the bottom portion of your /boot/grub/menu.lst file. 
```
sudo fdisk -lu
``````
sudo gedit /boot/grub/menu.lst
```Other wise if it really is a BIOS related problem and you don;t have those BIOS settings, I don't know what to tell you, except to take a look at the way your IDE cables are plugged in and what jumper settings you are using for your hard drive(s). Or use a different computer.

Regards. Herman :)

---

### Post by jacksolc on 2007-09-21
The specific Award BIOS you're referencing does not show the hard drives you're using.  This means that you have your drives on another controller which the BIOS cannot see.  These could be either SATA drives or IDE drives on what's being seen as a SCSI controller.

If the Ubuntu install engine detects these drives at all it will see them only during the install process and read them in as IDE drives, giving them an "hd_" designation.  But when the install is finished and it's time to boot, the drives will be seen as "sd_" drives, and thus the boot or root volumes will not get referenced.

I was only able to get a successful install on this BIOS by dropping down to a 20GB standard IDE drive and installing to that rather than to my DMA 5 Ultra 250 GB drive installed to the alternate controller.

---

### Post by mbwardle on 2007-10-12
I got this error after installing the Ubuntu 7.10 release candidate.

The error usually happens because Linux and your BIOS detect your hard disks in different orders.  GRUB tries to translate between the two using the device.map file in /boot/grub/device.map, which is automatically generated.  Chances are, it guessed wrong.

In my case, I have three SATA hard disks.

My BIOS sees them as:
HDD1 - 80 GB - Windows
HDD2 - 80 GB - Linux
HDD3 - 250 GB - Media

Linux sees them as:
/dev/sda - 80 GB - Windows
/dev/sdb - 250 GB - Media
/dev/sdc - 80 GB - Linux

So it generated device.map assuming that order was correct, i.e.:
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

When the installer installed GRUB using that data, it tried to install the first part of GRUB on /dev/sda and told it to look for the OS on /dev/sdc.  Unfortunately, this translated to "install on (hd0) then look for the OS on (hd2)", so it was looking for the OS on the wrong drive.

To fix it, you have to teach GRUB which order the BIOS uses.  To do this, follow these steps:

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"
8) Edit device.map (using vi or another text editor)

In my case, my new device.map was:
(hd0)    /dev/sda
(hd1)    /dev/sdc
(hd2)    /dev/sdb

which told GRUB that sdc was really the second hard drive, not the third.

9) Run "grub --device.map=device.map"
10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)

You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that.  This is what we want.

12) Edit menu.lst

You need to change references from (hd2,0) to (hd1,0), or whatever your Linux boot drive was autodetected as to whatever it is according to your BIOS.

If you get this step wrong, you'll see an error message something like:
Error 17: Cannot mount selected partition

meaning it's looking for a Linux file system on that partition, but it can't find one (because the drive device number is wrong in menu.lst).

13) Reboot

14) Celebrate or complain in this thread!

---

### Post by Herman on 2007-10-12
That looks like the best explanation on the subject of editing GRUB's device.map file I have ever seen! 
Well done mbwardle and thanks for sharing that! :)

Is it okay with you if I add a link to this in my GRUB Page? :)

Regards, Herman :)

---

### Post by akanriches on 2007-10-20
As I'm talking to you now, I have a problem in the office. I installed Ubuntu on one of my pc now I removed it by deleting the the partitions create and restated the system then Wala the ERROR 17 appears on the screen. I had Windows Xp installed on the other partition. i have used Windows Xp cd but what comes up on the xp cd when i boot frpom it is Caldera DR-DOS instead of the option for me to choose fixmbr. how do I solve this before my boss wants to make use of the system. Thanks...........

---

### Post by Herman on 2007-10-20
Hello akanriches,
Normally I would have expected [GRUB error 22]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22") from deleting the Ubuntu partition, (thus also deleting GRUB),  without installing another boot loader to the MBR first.
It probably doesn't matter what GRUB error you have, there are lots of easy and fast ways to install another boot loader in your MBR to make your computer boot normally again, here is a link to a page with a whole list of different ideas, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm") 
Just choose whichever one will be easiest for you or best.

I don't know why your Windows Install CD boots to Caldera DR-DOS. Here is another link about how to use Windows XP [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") in case that's any help to you.

Regards, Herman :)

---

### Post by Reavermann on 2007-10-20
Hi.
I get the same error from grub, after installing Kubuntu 7.04.
I have only ONE SATA Drive, a 320GB Seagate.
I tried to do what mbwardle said in his post, but still not working.
Anyway, at every step explained by him, I checked my existing settings and everything was OK.
My drive was on /dev/sda and in device.map I had (hd0) /dev/sda
My linux partition was on /dev/sda3 and in menu.lst the linux was pointed as (hd0,2) which is also corect.
I also tried to reinstall grub using /usr/sbin/grub-install /dev/sda, everything was successful, but after rebooting, also got Error 17.
What else can I do? :(

---

### Post by Herman on 2007-10-20
If you just have one single hard disc, there shouldn't be any problem with GRUB's device.map, that's only for those of us who have more than one hard drive.
 [Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")  In a single hard drive, normally is caused by either by using the root command instead of rootnoverify, when chainloading Windows with the NTFS file system, 
or by getting the disc number or partition number wrong when trying to boot Linux.
Since you say you have already checked, and it's definitely right, then I don't know.

You could still check your BIOS and try to make sure there isn't some problem with a some setting or another in there to do with how your hard disk is set up in your BIOS.
Maybe, for example, your CD-ROM drive is set as first hard drive in your BIOS's hard disk boot priority or something else like that.

You should try booting up manually using [**GRUB's Command Line Interface**]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and [using GRUB's Command Line to investigate your computer]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")

See if you can boot Linux up from GRUB's CLI, that should help you sort your problem out, [                                                                         How To Boot Linux from GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI")

Then when you can boot from CLI mode GRUB, just copy down the commands you used and copy those to your boot entry in your menu.lst file.

Regards, Herman :)

---

### Post by Reavermann on 2007-10-22
Hi all.
I found the problem. The Kubuntu installer just screwed my partition table or don't know what, but a friend of mine fixed the Grub and linux boots fine, but my previous version of Windows does not boo anymore. I checked the partitions with fdisk the it says that some partitions are misplaced or something. :-<. Dooh, why this should happen to me?
Now I saved all my data and I'm preparing to repartition the whole hard drive.
Anyway, thanks for help.

---

### Post by duffmeister on 2007-10-23
I am completely new to Ubuntu and I installed 7.10 Server and also get the Grub 17 error.
My system also has Windows XP

A Better Solution from mbwardle seems to apply to me.

How do I "Open a Terminal (Applications->Accessories->Terminal)"

I have booted from the desktop disk and all I get are icons for examples, install,  and the drives.

A while ago I did an install and I used to get a bunch of programs and I am sure the ability to get to terminal.
With this desktop version I don't get that.

Any help is appreciated

duffmeister

---

### Post by Herman on 2007-10-23
Hello 
>          I am completely new to Ubuntu and I installed 7.10 Server and also get the Grub 17 error. My system also has Windows XP A Better Solution from mbwardle seems to apply to me. How do I "Open a Terminal (Applications->Accessories->Terminal)" I have booted from the desktop disk and all I get are icons for examples, install,  and the drives. You downloaded and installed [Ubuntu 7.10 Server]("http://www.ubuntu.com/news/ubuntu-server710")? Wow! 
This question is way out of my league! You are using real professional software there! I don't know very much at all about servers.
If you are working for a large company or organisation, Canonical provides commercial support, I'm just an amateur hobbyist here, giving free help, mainly for ordinary home users and small or non-profit organisations. :)

Nevertheless, I'll do my best and take a guess. Since you can't get a terminal, maybe the Server Edition doesn't come with that program. According to the information you are reporting there isn't even a terminal in the Live CD used to install it either?  
I would guess you should be able to get a tty by pressing your  CTRL+ALT+F1 key, or any other F key between 2 and 6.
To get back to any desktop, (if Ubuntu Server has a desktop, maybe the CD for it has), you would press 'CTRL+ALT+F7' keys.
Does Ubuntu Server come in a LiveCD? Or do you install it with a special version of the 'Alternate' CD? By the sounds of what you are telling me it must be a special version of the Live CD.

>  A while ago I did an install and I used to get a bunch of programs and I am sure the ability to get to terminal.
With this desktop version I don't get that. Well I don't know, I have never tried out Ubuntu Server. I wouldn't have any idea what programs it would have with it. I wouldn't imagine it would have anything regular users would be intererested in at all, and I'm surprised it even has a desktop at all.
Are you sure Ubuntu Sever is really the right Ubuntu for you? If you are a home user like I am or even someone running a small business, you should probably try out the regular ubuntu-7.10-desktop-i386.iso before you advance to Ubuntu Server. You install some pretty good server software with ubuntu-7.10-desktop-i386.iso and still have a regular operating system as well.

Sorry if this information isn't what you were looking for, maybe someone else who is familiar with Ubuntu Server can step in and help here.

Regards, Herman :)

---

### Post by snkmad on 2007-10-24
I need help with my grub install. Ive read your guide, but im real on linux. Ive made a thread about it [here]("http://ubuntuforums.org/showthread.php?t=588418").
Looks like grub got installed on the IDE drive, not the SATA one.
Just need to know what do i need to change.

EDIT: Ok i think i gonna try it, but i dont know what to change on the menu.lst.
The new settings would be:
> New device.map order: 
(hd0)	/dev/sda
(hd1)	/dev/hda

Run: grub --device.map=device.map
type: root (hd1,1)
type: setup (hd1)

changes in  menu.lst:
??

EDIT2:
Wait i think i got it wrong. Since now hd0 is the SATA which contains linux, i should put root (hd0,1) and setup (hd0) right? And make the changes on menu.lst, changing all entries from hd(1,1) to hd(0,1) right?

EDIT3: Didnt work, I wont be able to fix this by myself. Any help is appreciated.

EDIT4: Got it working now, thx to meierfra for the help ;)

---

### Post by MQMike on 2007-10-26
This is an interesting thread. (. .. tells you how exciting my life has been this week  :)   )
I’ve wondered about this deal with device.map, trying to sort out exactly what/why it is used for.  I’ll write out loud here, and maybe you guys can either confirm my understanding or shoot it down or correct it?  So, in a way, the following are questions:

#1   When you turn on the PC, GRUB comes up after POST, then GRUB *does not consult with device.map *;  GRUB sees the drives the same way BIOS does;  and GRUB tries to do what you’ve told it to do (in menu.lst).
So, device.map, whether it is right or wrong, is not used here and does not affect how GRUB actually boots up or fails to boot up your OSes in this sense.

#2   In fact, taking the point even further, even if device.map is wrong, and even if GRUB has a booting problem, it seems like you can usually fix GRUB using a few simple methods, like root-setup-quit, or editing menu.lst, using geometry (fdisk –lu, etc.) to sort things out for root and setup devices and for the device references in the menu.lst—no need to mess with device.map.

#2   If your system has just one HDD, device.map really isn’t very relevant to anything practical that most users would ever notice.

#3   If you have more than one HDD, device.map becomes more relevant, and especially so if there’s a mixture of IDE and SATA drives.  Is there any predefined order preference that device.map uses in listing IDEs and SATAs?  I’ve read both ways—that SATAs go first, that IDEs go first in the device.map list.  In any case, if the user changes that order by physically changing his drives, then it’s a good idea to correct the mapping by editing device.map.

#4  USB flash devices, do not show up on device.map.  So, to know it’s BIOS naming (hdx), you can simply run geometry (hd<TAB key> or whatever to find it out.

# 5  When you install an OS, apparently, the installer uses device.map?  
--  However, even if it does, and whether device.map is correct or wrong, it doesn’t really matter * assuming * you manually install GRUB during the installation of the OS.  Using the Live CD Desktop install, you can use that Advanced button in Step 6 of the Manual Partitioning method.  Or use the Alternate install CD.  
--  And if you don’t know where to put GRUB, for now you can always just put it in the same partition that you specified (using either GRUB or Linux device notation) for the root files (/) of the OS you are installing (and later sort out the root-setup-quit and menu.lst editing you need to do).

# 6  During some updates, apparently, device.map is referenced?  E.g., a kernel update?  or a version update (say from 7.04 to 7.10)?  (At that time, is GRUB updated and grub-install run by the update process, thus necessitating reference to the device.map?)

#7  If you are working in Linux at the command line, using the grub shell (as in Section 15 of the GNU GRUB manual), then device.map is used by the grub program, and device.map, therefore, becomes important.  But even then, you can use the command: “device (hdx)  /dev/sdy”  to specify the map to use or to override device.map.

# 8   Editing device.map:  An easy way, it seems, is to simply access device.map using su/sudo, either from inside the OS installation at a terminal or using a live CD (and mounting, etc.).  You can use GRUB methods, e.g., geometry command, to sort things out, along with sudo fdisk –lu or whatever, to get the correct mapping and do the edit.  Seems like a naïve but easy-to-understand way to do it?


So, I guess I don’t really understand or appreciate, except when invoking the grub shell (Section 15 of the GRUB manual), the fuss over device.map issues.  Except, and this is part of my question, possibly during automatic installation of an OS when there is more than one HDD; or possibly during a kernel update or OS-version upgrade.

---

### Post by jimminy_kriket on 2007-10-27
I need some help. Grub is trying to boot my media partition as seen here.
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1b1b1b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154400714    77200326    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6a5ad122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   417593609   208796773+   7  HPFS/NTFS
/dev/sdb2       417593610   501436844    41921617+  83  Linux
/dev/sdb3       501436845   507573674     3068415   82  Linux swap / Solaris

```

This is what my device.map looks like:
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

This is what my menu.lst looks like :
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cdc6d252-ce18-4a1c-877d-90c268999477 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cdc6d252-ce18-4a1c-877d-90c268999477 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Ive tried changing ```
(hd0)	/dev/sda
(hd1)	/dev/sdb
``` to ```
(hd0)	/dev/sda
(hd1)	/dev/sdb2
``` but it didnt work and now im pretty much lost and stuck with a non-booting laptop (im using a live cd and it sucks).

Any help is much much much much appreciated as im trying to get this fixed asap.

---

### Post by meierfra on 2007-10-27
jimminy_kriket: The original device.map looks fine. I wouldn't change it. 
Do you get any error messages at boot up? 
Does the grub menu show up?

---

### Post by jimminy_kriket on 2007-10-27
Yeah, it just pops up and says "error 17".
Nothing else.

Its on a usb external harddrive, but even when I unplug the harddrive grub pops up anyways, so grub is on my windows drive.

---

### Post by meierfra on 2007-10-27
Are your bios able to boot from a usb drive?

---

### Post by jimminy_kriket on 2007-10-27
Im not sure, ive never tried but i read a couple other threads where people had sucess. But your right, it could be my bios.

Im thinking of just disabling grub for the time being if its easier and booting windows. But i bet you disabling grub is really hard..sigh

---

### Post by meierfra on 2007-10-27
Get [Supergrub]("http://supergrub.forjamari.linex.org/"). It might help you boot in ubuntu. But it almost certainly will let you boot into windows again.

Here is some more information on subergrub: [Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by meierfra on 2007-10-27
> Im not sure, ive never tried but i read a couple other threads where people had sucess. 

If your bios are able to boot  an usb drive, then super grub should let you boot  into ubuntu.

But  if the bios are not able to boot an usb drive, you will have to work a little harder. For example you could create a small boot partition for ubuntu on the internal hard drive.
But lets  first see what super grub can accomplish.

---

### Post by jimminy_kriket on 2007-10-27
Thanks for the help, but ive just gone back to running ubuntu off of my primary hard drive.
This was just getting to complicated and its not a huge deal, i just wanted the rest of my HD for games/programs in windows.

Thanks again for the help, I just dont have the patience at the moment.

---

### Post by meierfra on 2007-10-27
That's fine. But I recommend to get super grub anyway. It probably will come in handy sometime.

---

### Post by MQMike on 2007-10-27
I agree with meierfra, and for even more convenience, you might wish to put Super Grub Disk (SGD) on a flash drive (it’s a piece of cake, and there’s plenty of help around).

If you’re interested, have a look at how I did this recently.  I put SGD, GParted, and Puppy Linux on a flash drive (USB flash drive or UFD as it’s called), at my How-To:

How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)
(aka Qqmike, See Reply #10 for an improved update, 2007)
If you try this and do have questions, please post them under Installation & Booting at the forum there under Feisty or Gutsy so I don’t miss your post.  Or post here and some of the many, many good people can pitch in, too, or PM me or something to get my attention.  Herman at  hermanzone: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)   has done this work, as well.

Just by itself, SGD can be put on one of those very small 3 MB flash disk drives (Memorex makes them, like $10 for a 3-pack at Best Buy).  I’ve done that, and it works great.   EDIT: I just checked: the SGD /boot folder is just under 1 GB.

GParted requires another 50-60 MB, and Puppy another 80-90 MB (for the version  I used), so I allowed “about” half of a 512 MB flash drive for the project (allowing some extra room).

---

### Post by Herman on 2007-10-27
Hello MQMike and all,
firstly, my appologies to snkmad and jimminy_kriket for not being available to help for a few days. Sorry about that, but luckily there are lots of great people here who also like to help, so it looks like your problems are already solved now. :)

MQMike, you said,
> This is an interesting thread. (. .. tells you how exciting my life has been this week  :smile:   )
I&#8217;ve wondered about this deal with device.map, trying to sort out exactly what/why it is used for. I&#8217;ll write out loud here, and maybe you guys can either confirm my understanding or shoot it down or correct it? So, in a way, the following are questions: I'll have a try, but I would like to encourage others to also offer their insights. I have a computer that I had two IDE hard drives in and which didn't have any problems or conflict between the BIOS and Linux over the disk order, except when I switched the drives in my BIOS deliberately, for experimental purposes. Then things could get quite confusing even with only two IDE hard disks.
Now, hoping to gain some more insights into this interesting problem, I have rigged up a computer with three IDE hard drives, two SATA hard drives, and I plugged in two external USB drives as well just for good measure.
I carried out one or two test installations in each different type of drive. In my computers at least, Ubuntu gets it right every time. I am a little disappointed because I was hoping something would go wrong so I would have a chance to learn something.
That's why I was so happy when mbwardle posted such an excellent, well written account of how to edit /boot/grub/device.map, posts like that are worth their weight in gold when it comes to helping others who happen to run into similar problems.
I guess it must only happen to a small percentage of computers given the huge numbers of Ubuntu installations that have been taking place in the past week or two.

Okay, now I'll try to give you my opinions about your excellent questions,
>  #1 When you turn on the PC, GRUB comes up after POST, then GRUB *does not consult with device.map *; GRUB sees the drives the same way BIOS does; and GRUB tries to do what you&#8217;ve told it to do (in menu.lst).
So, device.map, whether it is right or wrong, is not used here and does not affect how GRUB actually boots up or fails to boot up your OSes in this sense.
 Well in my opinion, GRUB does use device.map at that point '*in a way*'. I don't think GRUB actually looks at /boot/device.map at that point, it doesn't need to. When a user edits /boot/grub/device.map, they run 'grub --device.map=device.map', or reinstall GRUB using the grub-install command.
Therefore the user is either booting up with the natural GRUB or with a modified GRUB, customized with special device.map information.
That means the GRUB they have installed is already programmed with the (hopefully corrected) device.map information, or if they didn't touch their device.map file yet and haven't re-installed GRUB, they will just be booting with the natural GRUB the way the Ubuntu installer set things up..
That's my impression, someone please correct me if I'm wrong, I am still trying to learn more about this myself.
>  #2 In fact, taking the point even further, even if device.map is wrong, and even if GRUB has a booting problem, it seems like you can usually fix GRUB using a few simple methods, like root-setup-quit, or editing menu.lst, using geometry (fdisk &#8211;lu, etc.) to sort things out for root and setup devices and for the device references in the menu.lst&#8212;no need to mess with device.map. That's right, MQMike, it isn't compulsory to mess with device.map if the user doesn't want to. The way I always used to help people with this type of problem was to advise them to edit their /boot/grub/menu.lst files with equally wrong information to counter-act the wrong GRUB set-up. Two wrongs do make a right, (at least in this type of situation). The best way to do that is to use a [GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell") to find out which device GRUB thinks is which, or try booting up from  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), and write down the commands you need to use to boot successfully. Then you can edit your/boot/grub/menu.lst with the exact same information and you will then be able to boot fine after that. You should also make any changes persistent by editing your debian automagic kernels list too, ([groot=]("http://users.bigpond.net.au/hermanzone/p15.htm#groot") (grub root device)).
>  #2 If your system has just one HDD, device.map really isn&#8217;t very relevant to anything practical that most users would ever notice.No, I agree, I think users of computers with only one hard disk can ignore their /boot/grub/device.map files, and they should never have any problems.
>  #3 If you have more than one HDD, device.map becomes more relevant, and especially so if there&#8217;s a mixture of IDE and SATA drives. Is there any predefined order preference that device.map uses in listing IDEs and SATAs? I&#8217;ve read both ways&#8212;that SATAs go first, that IDEs go first in the device.map list. In any case, if the user changes that order by physically changing his drives, then it&#8217;s a good idea to correct the mapping by editing device.map.I used to think SCSI or SATA drives were always numbered first by default, but in my computer now it's the IDE drives that are numbered 1, 2 and 3, SATA drives are 4 and 5. I'm not sure. Maybe the developers made changes to the scripts at some stage.
If the user or the computer technician changes the way the disks are plugged in and jumpered or the way the [Hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") in the BIOS then it's anyone's guess what will happen. I suspect that in a high percentage of instances, that would be the main cause of the user's problems. Especially Windows users who are new to Linux and still think of their drives in terms of 'Drive C', Drive D', and so on. Those descriptions don't tell them which hard drive is which, so they might have had Windows on their second hard drive, and had the drives reversed in their BIOS for years and never known about it until they installed Linux. I'm not sure about that, but it seems to me that it might be possible. Then of course Linux gets it right, but the user thinks Linux is wrong, so it could be all in the user's mind if you agree with that possibility.
>  #4 USB flash devices, do not show up on device.map. So, to know it&#8217;s BIOS naming (hdx), you can simply run geometry (hd<TAB key> or whatever to find it out.
 My external USB drives did appear in this computer when I installed with them plugged in, but mine are not flash memory devices in this instance, they are real hard drives, but they are external, so I'm not sure. Here's my current /boot/grub/device.map file,
```
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdc
(hd3)   /dev/sda
(hd4)   /dev/sdb
(hd5)   /dev/sdc
(hd6)   /dev/sdd
``` I agree about using  geometry (hd<TAB key> to use GRUB to investigate the computer. >  # 5  When you install an OS, apparently, the installer uses device.map?  
-- However, even if it does, and whether device.map is correct or wrong, it doesn&#8217;t really matter * assuming * you manually install GRUB during the installation of the OS. Using the Live CD Desktop install, you can use that Advanced button in Step 6 of the Manual Partitioning method. Or use the Alternate install CD. 
-- And if you don&#8217;t know where to put GRUB, for now you can always just put it in the same partition that you specified (using either GRUB or Linux device notation) for the root files (/) of the OS you are installing (and later sort out the root-setup-quit and menu.lst editing you need to do). I think scripts that are run by the installer create the /boot/grub/device.map and then install GRUB accordingly. 
Using the installer's options to manually select where we install GRUB will work if we choose to install GRUB to a partition. Back in the days when everyone used the 'Alternate CD' for installing and the Live CD wasn't made yet or didn't have an installer in it, there were just as many, if not more instances of wrong device.map and GRUB's IPL going to the wrong hard disk.
I don't think the user has any control over the new device.map, not at the moment anyway. We could suggest it as a possible improvement for the next release. Imagine if the Ubuntu installer used a similar method to Super Grub DIsk? I mean let the user manually select which hard disk is which from a menu, like Super Grub Disk's 'Advanced' menus. However, I don't know if an idea like that would be accepted. The percentage of people who experience problems is minute compared with the number of perfect installations, so why burden everyone with extra questions that will be un-necessary for most people?
>  # 6 During some updates, apparently, device.map is referenced? E.g., a kernel update? or a version update (say from 7.04 to 7.10)? (At that time, is GRUB updated and grub-install run by the update process, thus necessitating reference to the device.map?)
 I'm not sure but I don't think the device.map is actually referenced unless that is deliberately specified by someone or a script.
>  #7 If you are working in Linux at the command line, using the grub shell (as in Section 15 of the GNU GRUB manual), then device.map is used by the grub program, and device.map, therefore, becomes important. But even then, you can use the command: &#8220;device (hdx) /dev/sdy&#8221; to specify the map to use or to override device.map. Yes.

>  # 8 Editing device.map: An easy way, it seems, is to simply access device.map using su/sudo, either from inside the OS installation at a terminal or using a live CD (and mounting, etc.). You can use GRUB methods, e.g., geometry command, to sort things out, along with sudo fdisk &#8211;lu or whatever, to get the correct mapping and do the edit. Seems like a naïve but easy-to-understand way to do it?
I think the easiest way would be to boot Ubuntu and do it from inside the operating system, you could boot Ubuntu up from [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") if you can get one, or using [Super Grub Disk]("http://supergrub.forjamari.linex.org/"). Most people would find Super Grub Disk the easiest. 
From a Ubuntu Live CD probably mbwardle's instructions would be correct, you would probably need to chroot into your hard disk installed system as mbwardle advises, I'm not sure, but probably for the 'grub --device.map=device.map command mainly.
>  So, I guess I don&#8217;t really understand or appreciate, except when invoking the grub shell (Section 15 of the GRUB manual), the fuss over device.map issues. Except, and this is part of my question, possibly during automatic installation of an OS when there is more than one HDD; or possibly during a kernel update or OS-version upgrade.Well I think you are right, only a few people will need to know anything about their /boot/grub/device.map files. It should only be needed right after an new installation as far as I know. It's nice to know the proper and correct way to do things though, that's why I'm so interested. According to the GNU/GRUB manual, editing /boot/grub/device.map is the correct and proper thing to do, [15.3 The map between BIOS drives and OS devices]("http://www.gnu.org/software/grub/manual/grub.html#Device-map"). At least that's how I read it anyway.
Even then, like we discussed earlier, it's fine for most people to just edit their /boot/grub/menu.lst files wrong to suit a wrong GRUB. Editing /boot/grub/device.map is the proper way to do things for fussy people who like everything to be perfect. 

Some new users get all worked up and upset if GRUB gets installed to the wrong MBR, but actually, that's a trivial matter. It's simple to install GRUB to a different MBR of your choice later at any time. Some Windows users in particular, seem to worship the MBR as if it is some sort of a pagan god. I don't think a MBR is anything more than just another sector on a hard disk, except it has some code in it. It is within our human powers to use programs to control what code is written there, so I don't know why some people are so frightened by that.
I guess when people spend a lot of time recording things about their lives in their computers, they come to subconscioulsy equate the bootability or inability of their computers to boot with their own life and death. (Symbolically anyway).:lolflag:
Really though, I do feel great sympathy for those people who may be unlucky enough to experience booting problems, that's why I'm so interested in learning how to help people with them. Fortunately there are lots of other people around here, such as yourself, MQMike, and all the other people who help with GRUB questions who feel the same way and really help new users out of trouble.

Thanks to all the GRUB helpers out there! :)
And well done to all the new users who are brave enough to 'take the plunge' and install Ubuntu too! :)

Regards, Herman :)

---

### Post by MQMike on 2007-10-27
Herman, thanks for your excellent response – I couldn’t have hoped for more – and it confirms that if I’m nuts to think about this stuff, I‘m not alone.  :)

I just read through your detailed response, and I need some time to think about it, maybe run a test or suggest a test or two, and respond back here.  

Off the top of my head:

Question #1:
The test is this:  In a working system, intentionally mess up your device.map (by editing it wrongly).  Keep menu.lst the same.  Now see if the PC boots right.  I’m sure it will.

Question #2:
The groot=  thing you noted, I wonder if using a separate GRUB-files partition affects groot?  That is, putting just the /grub files in its own partition?  That’s what I do – I put GRUB in sdb1 and root (hd1,0) & setup (hd0) to boot 2 HDDs (XP on sda and Linux distros on sdb).  I need to think about this with respect to groot=.

Question #4:  USB
One test would be to connect a new flash drive or external USB HDD that was NOT connected during an OS install, run the grub --device.map=device.map command, and see what happens to device.map.

Question #8:
For example, can one edit device.map from live Ubuntu CD using just sudo/gksudo/kdesu and see if  chown is really necessary?  A test would tell.


So, I’ll think about all this and post back later or tomorrow.


As you indicated, I’d love to get other expert or experienced opinions on these device.map issues.

Many thanks for your interest and response here, Herman.

Mike
Aka MQMike, Qqmike, mikemqa

---

### Post by Herman on 2007-10-27
> it confirms that if I’m nuts to think about this stuff, I‘m not alone.  :smile: No, you're not alone, I'm nuts too! :lolflag:

>  Question #1:
The test is this: In a working system, intentionally mess up your device.map (by editing it wrongly). Keep menu.lst the same. Now see if the PC boots right. I’m sure it will.
Okay, I rebooted first just to prove my computer reboots okay to begin with.

Then edited my /boot/grub/device.map to place all the SCSI (SATA) drives ahead of the IDE drives without applying any extra commands.

Sure enough, as we both expected, my computer still boots as the same as normal so far.

Next, I re-installed GRUB using 'sudo grub-install /dev/hda', and Ubuntu still rebooted the same as usual.
I was expecting some problems this time, but nothing went wrong at all.

...okay, I tried lots of ways to try to get GRUB to install with a messed up device.map, but my computer just keeps on booting up normally with no problems. 

How come other people keep reporting there SATA/IDE GRUB problems and claim that editing /boot/grub/device.map and re-installing GRUB fixes their problems then? It doesn't seem to have any effect in my computer, but then again I didn't have a real problem to begin with, so I still don't know. :confused:

One thing I did notice though, mbwardle's command: grub --device.map=device.map,
>  9) Run "grub --device.map=device.map" Should be corrected to:  9) Run "grub --device-map=device.map"
```
grub --device-map=device.map
``` See, there's a hyphen between the words device and map the first time they appear the command, not a dot.

So, MQMike, you win, I have tried every way I can think of to install GRUB to MBR with a deliberately wrong /boot/grub/device.map and to no avail. My system just keeps right on booting right up properly regardless.

What am I doing wrong?.. I mean right.. no wrong.. or...:confused:

>  Question #2:
The groot= thing you noted, I wonder if using a separate GRUB-files partition affects groot? That is, putting just the /grub files in its own partition? That’s what I do – I put GRUB in sdb1 and root (hd1,0) & setup (hd0) to boot 2 HDDs (XP on sda and Linux distros on sdb). I need to think about this with respect to groot=. I think if you mean a 'dedicated GRUB partition' (the GRUB files but not the Linux kernel), then your groot= line should still point to your '/' (root) parititon, because that's where your kernel is.
If you have a separate /boot partition, (meaning a partition containing your GRUB files and your Linux kernel, which is registered in /etc/fstab as your /boot partition), then your groot= line should point to that one instead.
That might need to be edited if you make changes to your operating system boot entires in menu.lst, in order to make your changes persistent over a kernel update.
>  Question #4:  USB
One test would be to connect a new flash drive or external USB HDD that was NOT connected during an OS install, run the grub --device.map=device.map command, and see what happens to device.map.
 Okay, since you asked nicely, I have plugged in another USB external hard disk drive and six USB flash memory drives and I have issued the command 'sudo grub-install --recheck /dev/hda'
I'll let you know what happened in a minute or two...  :)

---

### Post by Herman on 2007-10-27
Okay, right now I have three IDE disks and two sata disks in my computer.
Outside my computer I have three external USB hard disks plugged in plus another five flash memory disks.
That's a total of thirteen drives altogether.

Here's my fdisk output,
```
herman@amd46b:~$ sudo fdisk -lu
[sudo] password for herman:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ba675

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306937889   153468913+  83  Linux
/dev/sda2       306937890   312576704     2819407+   5  Extended
/dev/sda5       306937953   312576704     2819376   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000576d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321   83  Linux

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00026d85

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   146914424    73457181   83  Linux
/dev/hda2   *   146914425   306937889    80011732+  83  Linux
/dev/hda3       306937890   312576704     2819407+   5  Extended
/dev/hda5       306937953   312576704     2819376   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c87d3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   312576704   156288321    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000a95c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1              63   156296384    78148161   83  Linux

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x548118f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32     4030463     2015216    e  W95 FAT16 (LBA)

Disk /dev/sdd: 1030 MB, 1030750208 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cca6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63     2008124     1004031    b  W95 FAT32

Disk /dev/sde: 6448 MB, 6448619008 bytes
255 heads, 63 sectors/track, 783 cylinders, total 12594959 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80888a5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63    10554704     5277321   83  Linux
/dev/sde2        10554705    12578894     1012095    5  Extended
/dev/sde5        10554768    12578894     1012063+  82  Linux swap / Solaris

Disk /dev/sdf: 514 MB, 514850816 bytes
255 heads, 63 sectors/track, 62 cylinders, total 1005568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006a372

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63      996029      497983+  83  Linux

Disk /dev/sdg: 40.0 GB, 40060403200 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242975 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000105f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1        30507435    78236549    23864557+   5  Extended
/dev/sdg2              63     7807589     3903763+  83  Linux
/dev/sdg3   *     7807590    29447144    10819777+  83  Linux
/dev/sdg4        29447145    30507434      530145   83  Linux
/dev/sdg5        30507498    32611949     1052226   82  Linux swap / Solaris
/dev/sdg6        32612013    78236549    22812268+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdh: 1994 MB, 1994227200 bytes
4 heads, 16 sectors/track, 60858 cylinders, total 3894975 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          16     3894974     1947479+   e  W95 FAT16 (LBA)

Disk /dev/sdi: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a70cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1              63     2104514     1052226   83  Linux
/dev/sdi2         2104515     8048564     2972025   83  Linux
```

And here's how they go listed in /boot/grub/device.map after I ran the 'sudo grub-install --recheck /dev/hda' command,
```
herman@amd46b:~$ sudo grub-install --recheck /dev/hda
[sudo] password for herman:
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdc
(hd3)   /dev/sda
(hd4)   /dev/sdb
(hd5)   /dev/sdc
(hd6)   /dev/sdd
(hd7)   /dev/sde
(hd8)   /dev/sdf
(hd9)   /dev/sdg
(hd10)  /dev/sdh
(hd11)  /dev/sdi

```
All perfect!

---

### Post by Herman on 2007-10-28
Okay, now I'm typing to you from my Ubuntu Gutsy Gibbon desktop LiveCD for AMD64.
I have just chrooted into my hard disk installed Gutsy and here's what I did,
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/ubuntu/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev/ /mnt/ubuntu/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu/ /bin/bash
root@ubuntu:/# cat /boot/grub/device.map
(fd0)   /dev/fd0
(hd0)   /dev/sdd
(hd1)   /dev/sdg
(hd2)   /dev/sde
(hd3)   /dev/sdi
(hd4)   /dev/sdc
(hd5)   /dev/sdb
(hd6)   /dev/sda
(hd7)   /dev/hdc
(hd8)   /dev/sdf
(hd9)   /dev/hdb
(hd10)  /dev/sdh
(hd11)  /dev/hda

root@ubuntu:/# grub --device-map=device.map
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 

```Now I'll reboot and see if that had any effect.

---

### Post by Herman on 2007-10-28
No effect whatsoever, apparently.
Here I am in my hard disk installed Ubuntu Gutsy Gibbon again after rebooting from Ubuntu Gutsy Gibbon Live CD and trying to bork my /boot/grub/device.map and re-install grub.
It didn't work! Gusty Gibbon booted perfectly again!
I must have the world's only bullet proof GRUB. 
>  Question #8:
For example, can one edit device.map from live Ubuntu CD using just sudo/gksudo/kdesu and see if chown is really necessary? A test would tell. I won't be able to prove anything because even when I did do it by chrooting it still didn't seem to be effective.

Maybe it's smart enough to know there's no real problem here and that's why I can't seem to trick it into doing anything stupid. :confused:

Regards, Herman :)

---

### Post by MQMike on 2007-10-28
Question #1: (mess up the device.map and see if you can boot)

Herman, I did some testing, too, and got the same result you did:
No matter how I (intentionall) messed up my device.map, I was able to re-boot normally, as I always do.  This confirms something I was told on SGD once, that the GRUB you see when you re-boot the PC is not the grub from grub shell in Linux (Section 15 of the GRUB manual); and this GRUB you see when you re-boot the PC does not look at your device.map to do its job.

Question #2 (groot=)

OK, I'm with you here on groot=.  What you said is right; I just got something confused here.
I do have a * dedicated * GRUB partition (on sdb1= (hd1,0), GRUB files only, no kernel files), and my main automagic kernel is sdb5 = (hd1,4), so my groot=(hd1,4) as it should.

Elsewhere, we've discussed how terminology can be confusing in GRUB (like "/boot" for example), and here's another example for me, anyway:  "GRUB root".   If you keep in mind the 3-step fixer of all fixers:  root--setup--quit, then the GRUB root, in my mind, should be the partition where you want GRUB to get the GRUB files to use in the setup command.  This process builds the machine you need for GRUB to boot: Stage_1 in 512B of MBR of hdx (setup (hdx)), Stage_1.5 in the sectors following that MBR of hdx (but preceding the first partition of hdx), and Stage_2 where we see menu.lst etc that is in the partition specified in the root command (in:  root-setup-quit).  So, in my (admitted crazy) mind, GRUB root refers to the partition specified in this root command (and may be different each time you want it to be different in different root (hdy,z) commands).
You said on your website:
". . . 'groot' is short for 'grub root device'. That will be the partition you want your new Linux kernel to be installed in when you get a new one during an update. Your /boot partition is the partition you should specify here.  If you have a standard installation, with a /boot directory in your root partition, (/ ), then the number you will see here will be the same as the number you will see for kopt.  
If you have a special installation with a separate /boot partition, the number you should see here will be the the partition number of your /boot partition."

And that is what is intended for the menu.lst configuring, with the groot=  statement.
OK, case closed (for me) on Question #2 about groot (I think).


Question #4: USB detection in device.map

Again, Herman, my tests agree with your testing.  I checked my device.map, my USBs were not there (because they weren't connected when I ran any installations), then I connected a flash drive and an external USB HDD (both are bootable), then I ran the --recheck command, and now the USBs do show up in device.map properly.  No problems.  

But there could be an issue for really crazy applications:  Which shows up first?  When you do this, you might get flash drive = sdc and external HDD = sdd; but disconnect them, re-connect them (in various USB ports, in maybe a different order, etc.), --recheck again, and they might be reversed sdd and sdc, respectively.


# 8 Editing device.map:

I used the Kubuntu 7.04 live CD, re-booted, got a command line (Konsole terminal), opened Konqueror (file manager) as root, made sure my dedicated GRUB partition was mounted (sdb1), edited and saved device.map from sdb1, closed out and re-booted into Kubuntu on sdb5, and checked device.map on sdb1, and the edits were there (although the intentionally incorrect edits did not affect GRUB when I re-booted--as you've noted, too).  So, it is easy to edit device.map from a live CD using GUI, even if you don't know much about command-line methods.  Except, you do need to know how to work as root in GUI, so you need a root terminal (sudo -i, or sudo su even though I've read that it is naughty to use sudo su) or somehow work so you edit as root (Actions>Edit as root).


# Another issue/comment:  Invoking grub-install.
You know, I always work with root-setup-quit at a grub>  prompt, partly because I've read so many warnings about using grub-install while running Linux.  And here's an example.
While in a terminal in Kubuntu on sdb5, I ran:
mike@mike-desktop:~$ sudo grub-install --recheck /dev/sdb5

Now what does that do exactly?  I thought it installed GRUB to the root partition sdb5=(hd1,4).  But does that mean it installed which GRUB to (hd1,4)--the GRUB in (hd1,4)?  Another way to word this question is, Would this be the equivalent way to do it:
grub> root (hd1,4)
grub> setup (hd1,4)
grub> quit

I think so, right?  If so, that should not affect any GRUB set up in any MBR, including the first-bootable MBR (in BIOS).  That is, running that grub-install command (above) should not affect how the machine boots up.


Well, that's long enough for now, and about all I had time to do.  

In general, I must say, Herman, my experience with GRUB is the same as yours, which is why this thread caught my attention.  That is, I don't seem to have any problems with GRUB, even in complex hardware configurations, and even when I try to break GRUB.  It always works.  Or, when it fails to boot the PC I know exactly why and simply use a few standard GRUB methods to fix the problem.  When GRUB goofs up for me, it's always been my fault somehow, and then it is readily fixable.  My ace-in-the-hole is simple:  use geometry or find (and the Linux fdisk -lu) to know * exactly * where things are, then go with the proper root-setup-quit commands, and you're done.

What a way to start the day at 4 am here.  Hmm . . .  can't think of a better way.  :)
Thanks, again, for you interest and input here to all this stuff I brought up.

--Mike

---

### Post by meierfra on 2007-10-28
> mike@mike-desktop:~$ sudo grub-install --recheck /dev/sdb5

Now what does that do exactly? I thought it installed GRUB to the root partition sdb5=(hd1,4). But does that mean it installed which GRUB to (hd1,4)--the GRUB in (hd1,4)? Another way to word this question is, Would this be the equivalent way to do it:
grub> root (hd1,4)
grub> setup (hd1,4)
grub> quit

No.  Say your terminal is  rooted on partition (hd0,3) . Then  "sudo grub-install --recheck /dev/sdb5" does 
1) Create a new device.map
2)  Copies all the grub files from "/usr/lib/grub/i386-pc" to "/boot/grub"   ( it does this on (hd0,3))
3) grub>  root (hd0,3) 
    grub> setup (hd1,4) 
    grub> quit

---

### Post by meierfra on 2007-10-28
> root@ubuntu:/# grub --device-map=device.map
Probing devices to guess BIOS drives. This may take a long time.
This is where all your experiments  are going wrong.

You need to use :   "grub --device-map=/boot/grub/device.map"
Otherwise grub  does not find the file and creates its own device.map as you can see from  "Probing devices to guess BIOS drives."

---

### Post by MQMike on 2007-10-28
Just checking in here quickly -- meierfra, thanks for your last two posts.

I need to give some thought to your last Post #38, exactly.

---

### Post by KanadianKozak on 2007-10-28
I installed Ubuntu on my computer the other day and everything was working fine.  I have 2 IDE drives in my computer, one with Window XP on it, and one now with Ubuntu.  After a restart today in windows, I got the error 17 message.  I'm kinda new to Linux, so I came to the forums to see what to do.  I was going with mbwardle's solution and it was working good until I go the the device.map part.  My XP is installed on hda1, which is hd0, and Ubuntu is on hdb7, which is hd1.  

> **mbwardle said:**
> 
9) Run "grub --device.map=device.map"
10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)

You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that.  This is what we want.

12) Edit menu.lst


When I run "grub --device-map=device.map" and type "root (hd1,7)", it tells me "Error 21: Selected disk does not exist"

I don't know what do do after this.  The menu.lst has the right hard drive associated in it, but I still get the grub error 17 when I try to boot.  Any help would be greatly appreciated.

KanadianKozak

---

### Post by meierfra on 2007-10-28
KanadianKozak:   post  your "menu.lst" and the output of "sudo fdisk -l".

---

### Post by KanadianKozak on 2007-10-28
_**menu.lst**_

# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
 
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
 
# Pretty colours
#color cyan/blue white/blue
 
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
 
#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#
 
#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
 
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
 
## DO NOT UNCOMMENT THEM, Just edit them to your needs
 
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5f82b544-4ffc-4396-80a4-f6d84c40ddcf ro
 
## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,7)
 
## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true
 
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false
 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
 
## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false
 
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
 
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
 
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single
 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
 
## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true
 
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
 
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
 
## ## End Default Options ##
 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5f82b544-4ffc-4396-80a4-f6d84c40ddcf ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
 
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5f82b544-4ffc-4396-80a4-f6d84c40ddcf ro single
initrd		/boot/initrd.img-2.6.22-14-generic
 
title		Ubuntu 7.10, memtest86+
root		(hd1,7)
kernel		/boot/memtest86+.bin
quiet
 
### END DEBIAN AUTOMAGIC KERNELS LIST
 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
 
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

**_sudo fdisk -l_**

Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2333819f
 
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       15217   122230521    7  HPFS/NTFS
/dev/hda2           15218       30515   122881185    f  W95 Ext'd (LBA)
/dev/hda5           15218       30515   122881153+   7  HPFS/NTFS
 
Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03e1e482
 
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4651    37359126    7  HPFS/NTFS
/dev/hdb2            4652       38913   275209515    f  W95 Ext'd (LBA)
/dev/hdb5            4652       12403    62267908+   7  HPFS/NTFS
/dev/hdb6           12404       13014     4907826   82  Linux swap / Solaris
/dev/hdb7           13015       17802    38459578+  83  Linux
/dev/hdb8           17803       38913   169574076    7  HPFS/NTFS

---

### Post by meierfra on 2007-10-28
Your ubuntu partition is (hd1,6) and not (hd1,7) (Grub starts counting at 0). So you need to change all "(hd1,7)" in menu.lst to (hd1,6). Don't   forget to change "# groot=(hd1,7)" to "# groot=(hd1,6)" otherwise you will have problems after the next kernel upgrade.

Reboot and you should be all set.

---

### Post by KanadianKozak on 2007-10-28
I'm still recieving the Error 17.

Is it a problem that when I go to grub --device-map=device.map and type "root (hd1,7)" it tells me "Error 21: Selected disk does not exist"?

---

### Post by dpod on 2007-10-28
Did you look at [http://ubuntuforums.org/showpost.php?p=3653638&postcount=38](http://ubuntuforums.org/showpost.php?p=3653638&postcount=38) ?

It looks to me from that that you need to do a path.

---

### Post by meierfra on 2007-10-29
> It a problem that when I go to grub --device-map=device.map and type "root (hd1,7)" it tells me "Error 21: Selected disk does not exist"?
 
1) As the previous poster pointed out, you need to use the full path "/boot/grub/menu.lst"
2) it should be (hd1,6) and not (hd1,7).

But I don't think you have a problem with the  device.map. So 1) should be irrelevant.
And 2) should have given a different error. 

Some question which might help to  figure out what is going on:

Did you change the device.map? Could you post your device.map?
Could you post "menu.lst" again so that we can look at the changes you did?
Did the grub.menu appear when you rebooted?
If  you  do "sudo grub" and then  "find /boot/grub/stage1" what is the output?
Did you do any partitioning before your problems started? I'm trying to figure out why your menu.lst contained "(hd1,7)".

---

### Post by KanadianKozak on 2007-10-29
I had done partitioning to my hard drive originally.  It had mutliple partitions on it, and I then used the unallocated space for Ubuntu.  I know the problems started after I inserted a USB memory stick and my computer treated it like it was a floppy drive, when I don't have a floppy drive on my computer.

When I reboot, without the Ubuntu boot disk in, all that happens is the Error 17 message appears on my screen.

The device.map is

(hd0)  /dev/hda
(hd1)  /dev/hdb

I didn't change anything in it from what it originally was.

Here's the new menu.lst

# menu.lst - See: grub(8 ), info grub, update-grub(8 )
# grub-install(8 ), grub-floppy(8 ),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5f82b544-4ffc-4396-80a4-f6d84c40ddcf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,6)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=5f82b544-4ffc-4396-80a4-f6d84c40ddcf ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd1,6)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=5f82b544-4ffc-4396-80a4-f6d84c40ddcf ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd1,6)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

When I did find /boot/grub/stage1 it returned (hd1,6)

Kanadian Kozak

---

### Post by meierfra on 2007-10-29
Since you don't reach the  grub  menu, grub needs to be reinstalled:

Do this:

sudo grub

and at the grub prompt:

root (hd1,6)

setup (hd0)

quit

Then reboot.

---

### Post by KanadianKozak on 2007-10-29
After I did "sudo grub" and "find /boot/grub/stage1", I changed "root (hd1,6)" and "setup (hd0)"

It brings me to the grub menu and boots up in XP and Ubuntu fine!  :D

Thanks for all your help!

---

### Post by bluntz on 2007-10-30
I too have the grub error 17 on a phoenix bios board (msi)
after Installing Gutsy,I swapped out the drive after giving it a good run,all seemed good ,but
when I swapped it back in,it dies with a scream:
grub error 17
loading the grub recovery disc doesnt fix it either in auto or manual mode.
loading the edgy live disc and going to gparted for some help just shows the hda1 partition as unknown fs, and cant mount it. so it seems I've lost everything on it.
I even had tovid and zoneminder running fine,downloaded some DVDs Mp3s ect...was really sold 
on it!

Then POOF.........
Damn. disappointing.
However after the grub bug is squashed,I am sure to Run this bad boy for sure!
Oh Sooooooooooooo Close.......

---

### Post by meierfra on 2007-10-30
> loading the edgy live disc and going to gparted for some help just shows the hda1 partition as unknown fs, and cant mount it. so it seems I've lost everything on it.
Seems you have a disk problem and not a grub problem. Give testdisk a try:

[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk")
[URL="http://www.users.bigpond.net.au/hermanzone/p21.html"]
Hemanzone info on testdisk[/URL]

Testdisk is on the gparted live cd. It can also be installed on the Ubuntu live cd via synaptics or apt-get.

---

### Post by redenex on 2007-10-31
Guys, I have a Grub Error 17 too. The BIOS is detecting the hard disk, but Ubuntu fails to load. When I connect the Hard disk to my other computer (which runs Ubuntu too), the disk is not getting reflected and I am not finding a way to mount it. Can someone help please?

---

### Post by Herman on 2007-10-31
Hello redenex,
When there is only one hard disk in the computer and you get GRUB error 17 when trying to boot Linux, it's most likely just caused by a simple mistake in the menu.lst file. Make sure to check your operating system entry's 'root (hdx,y)' details are correct.
For example,
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd[COLOR=Red]**0,1**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```If you need any specific help with that, please post the output from 'sudo fdisk -lu' here along with a copy of the bottom portion of your /boot/grub/menu.lst file and I or someone will take a look at it for you.
```
sudo fdisk -lu
``````
sudo gedit /boot/grub/menu.lst
```You can fix your Ubuntu operating system with a Ubuntu Live CD. The way to do it is explained in the following link, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD.
                                        
Another way is to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to 'direct boot' Ubuntu for you so that you can easily check and repair your operating system's entry in menu.lst. 
                                       Super GRUB can boot your operating system by symlinks to the kernel if you use, from the Main Menu,'English Super Grub Disk'--> Gnu/Linux --> Boot Gnu/Linux Directly -->Boot Gnu/Linux Directly -->...And select either IDE or SCSI type hard disk, then keep selecting your Ubuntu partition.
That will boot Ubuntu for you directly by symlinks to your kernel and initrd.img, thus bypassing your menu.lst file.

Regards, Herman :)

---

### Post by Herman on 2007-10-31
Hello meierfra,
Thank you very much for that help with my experiments to try to learn how to bork my system by deliberately installing a corrupted /boot/grub/device.map file.
> This is where all your experiments  are going wrong.
You need to use :   "grub --device-map=/boot/grub/device.map"
Otherwise grub does not find the file and creates its own device.map as you can see from "Probing devices to guess BIOS drives." Following your excellent advice does seem to have helped me get a little further at least. After I use that corrected command and then try 'find /vmlinuz' or similar, I do get the wrong answer that I am hoping for from the mixed up GRUB shell.
However I still can reboot normally every time, so I don't seem to be successful yet in making the changes 'permanent'.
I will keep trying.

Regards, Herman :)

---

### Post by meierfra on 2007-10-31
Herman:  I run a few test with the following simple  set up:

I am working on a Ubuntu terminal on sda2. The  "correct" device map is
(hd0)  sda
(hd1)  sdb
and I  changed it  to
(hd0) sdb
(hd1) sda
 
My conclusions:

 1) device.map is not used during boot up. It is only used when running "update-grub" "grub-install" or "grub". So during boot-up (hd0) still was sda and (hd1) was sdb.


2)  update-grub uses "device,map" to determine "groot"  (thats is the (hdx,y) notation of your current partition).   But  only if menu.lst does not have a "# groot" statement. I tested this  as follows: I   run update-grub and I got  a correct "menu.lst", that is (hd0,1) was used for sda2. Then  I removed "groot" from menu.lst and run update-grub  again. Now  menu.lst  uses (hd1,1) for sda2.
 But at boot up (hd1,1) stands for sdb2 and  I no longer could  boot into sda2 from the grub menu.


3) grub-install:  To  test this you need to run grub-install without the --recheck option. 

running  grub-install sdb:

This does not seem to use the device map and everything  was fine (although I didn't run to many test so I'm  not sure)

running grub-install sdb3:

This  will install grub on the MBR of sdb3. And it does copy the grub files to /boot/grub on /dev/sda2.
But  chainloading into sdb3 gave some inconclusive results. But it never did what is was supposed to do, namely load the grub menu on /dev/sda2.


4) grub:   If you run grub without the "device-map" option, then grub produces its own device map and every thing works fine (unless it guesses the wrong device.map) (Note  that grub  does not write its device map to the file /boot/grub/device.map.  So  that device.map is still screwed up)

grub --device-map=/boot/grub/menu.lst:

I did:
root (hd1,1)
setup (hd0)

With the wrong device map, grub  thinks (hd0) is /dev/sdb and (hd1,1) is sda2. So  it installed the stage 1 and stage 1.5 file from /boot/grub/ on sda2 to the MBR of sdb. 
Booting from /dev/sdb will now  fail, and instead the computer will try to boot from  the next hard drive in boot order. 

Next I did:
    root (hd1,1)
    setup (hd0,0)
This installs  grub  to sdb1.
Now if there was   a /boot/grub folder on  sdb2, it would somehow load a grub.menu from somewhere, (I didn't do enough testing to  know how it picked this grub.menu)
But if   there wasn't a /boot/grub folder on sdb2  I got a  grub-prompt at boot up.

So  grub installs the stage 1 files  to the MBR in the location  one would expect.
This seems to indicate that "(hd1,1)" was written into the MBR. (Note that grub uses the correct device.map at boot up, so (hd1,1) is sdb2 during boot up) So at boot up it  looks  for the grub files somewhere on sdb2 and fails.


Next I did:
 
root (hd1,1)
setup (hd1)

This case behaved differently, since root and setup are on the same partition
With the wrong device map, grub  thinks (hd1) is /dev/sda and (hd1,1) is sda2. So  it installed the stage 1 and stage 1.5 file from /boot/grub/ on sda2 to the MBR of sda. 
If one  boots from sda, the grub.menu from sda2 appears. Note that at boot-up (hd1,1) really is sdb2. 
So the MBR of sda  must contain instructions to look at the second partition of the CURRENT drive (rather than to look at (hd1,1), which would be the second partition on sdb) 



Conclusion: One only needs to use the device.map if all of the following occurs simultaneously:

a)  Grub guesses the boot order wrong;
b) On tries to install Grub to an  MBR on a drive different from the drive  containing /boot/grub;
c)  One is unwilling or unable to change the boot order;
and
d) One is unable to get to the grub command line at boot up (the grub command-line at boot-up always lists the drives in boot order, so using "root (hdx,y) setup (hdz)" always gives the correct results.)

---

### Post by redenex on 2007-11-02
> **Herman said:**
> Hello redenex,
When there is only one hard disk in the computer and you get GRUB error 17 when trying to boot Linux, it's most likely just caused by a simple mistake in the menu.lst file.You can fix your Ubuntu operating system with a Ubuntu Live CD. The way to do it is explained in the following link, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD.
Regards, Herman :)

Thank you Herman, I went to the link you posted, and here is my result:


```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    75409109    37704523+  83  Linux
/dev/hda2        75409110    78236549     1413720    5  Extended
/dev/hda5        75409173    78236549     1413688+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /media/ubuntu 
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Ironically, I am unable to mount it. :confused:



I also tried Super Grub, but it couldn't rectify my problem either! Maybe I am doing something wrong? Or is my hard disk having any irrepairable errors?

---

### Post by Herman on 2007-11-02
Hello redenex,
>  wrong fs type, bad option, bad superblock on /dev/hda1,missing codepage or other error? :confused:  
Thanks for posting back that feedback there, redenex, that should help us solve the problem. 
Maybe this is a file system problem or a hard disk problem.
Firstly, are you sure you installed Ubuntu in an ext3 file system? (Not reiserfs or anything else?). To check, you can open a terminal and run ' [FONT=Bitstream Vera Sans Mono]sudo parted /dev/hda p'
[/FONT] ```
sudo parted /dev/hda p
```Another way to check would be to open GParted Partition Editor in your Gutsy Gibbon Live CD and take a look at your /dev/hda1 partition and see what it looks like. If the file system is healthy you should see a colored box around the partition, and the partition should be white in the middle with a colored area to the left where the space is used. GParted should tell you what kind of file system you have, ext3 or reiserfs or whatever.

If the file system is not healthy, it may be shown in GParted with black box around the partion and the black box might be blank inside. 
I expect probably that is what you will see this time, redenex.

First, you can try running a file system check, if it is an ext3 file system in that partition you can try running, 'sudo e2fsck -C0 -p -f -v  /dev/hda1' 
```
sudo e2fsck -C0 -p -f -v  /dev/hda1
```Normally, that would fix most  ordinary ext3 file system problems, but I'm not sure if that will really solve the problem in your instance, redenex, but it shouldn't hurt to try that. What I really want is to see what error messages that will produce. I'm expecting that will confirm your superblock is missing or corrupt.
If it doesn't, it might say something like this,
                             /dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
If so, let me know and I'll tell you what to do next.

If it does confirm that your superblock is missing or corrupt, you can replace the superblock with a backup superblock, 
To find the location of your backup superblocks, you use a command like, 'sudo dumpe2fs /dev/hda1'
```
sudo dumpe2fs /dev/hda1
```That command will produce a very long output, you will probably need to scroll back to the top of it in your terminal. 
Just down from the top you will see something like;
Group 0: (Blocks 0-32767), followed by some information, I'm not sure exactly what that will look like in your case.
Then just below that you should see something like:
Group 1: (Blocks 32768-65535)
Backup superblock at 32768, Group descriptors at 32769-32769.
There are more backup superblocks as well, if you look through the rest of the text you will see where those are as well.

A better command if you don't want to see that large output but only where your superblocks are located would be, '[FONT=Bitstream Vera Sans Mono]sudo dumpe2fs /dev/hda1 | grep -i superblock'
[/FONT]```
sudo dumpe2fs /dev/hda1 | grep -i superblock
```So to restore your primary superblock from the backup, you would use something like, 'sudo e2fsck -b 32768 /dev/hda1'
```
sudo e2fsck -b 32768 /dev/hda1
```
If that doesn;t fix it, try the same command but replace the number '32768' with the number for a different backup superblock.

References: [DAMAGED SUPERBLOCK]("http://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html") by Bruno
 [Understanding UNIX/Linux filesystem Superblock]("http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html") by nixcraft.

Regards, Herman :)

---

### Post by loneshadowcccp on 2007-11-03
mbwardle:
thanks for the explanation, but i got stuck right after
7) Run "cd /boot/grub"
how do i edit the device map after that? i am a noob plz help.
thks

---

### Post by loneshadowcccp on 2007-11-03
oooops nvmd wrong one sorry

---

### Post by redenex on 2007-11-03
> **Herman said:**
> Hello redenex,
 :confused:  
Thanks for posting back that feedback there, redenex, that should help us solve the problem. 
Maybe this is a file system problem or a hard disk problem.
Firstly, are you sure you installed Ubuntu in an ext3 file system? (Not reiserfs or anything else?). To check, you can open a terminal and run ' [FONT=Bitstream Vera Sans Mono]sudo parted /dev/hda p'
[/FONT] ```
sudo parted /dev/hda p
```
Regards, Herman :)

Hello Herman.
```
ubuntu@ubuntu:~$ sudo parted /dev/hda p

Disk /dev/hda: 40.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  38.6GB  38.6GB  primary                boot 
 2      38.6GB  40.1GB  1448MB  extended                    
 5      38.6GB  40.1GB  1448MB  logical   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.         
```

Why does it show msdos in there? This was a perfectly running system on Ubuntu Studio (upgraded to Gutsy on 18th Oct). The Grub Error 17 started to show while I once restarted the system. Moreover, the partition, I am sure is ext3! Will wait for your reply to try out other things! 

> **Herman said:**
> Another way to check would be to open GParted Partition Editor in your Gutsy Gibbon Live CD and take a look at your /dev/hda1 partition and see what it looks like.

I have Feisty Fawn Live CD, does it have GParted too?

Thanks in advance. :guitar:

---

### Post by redenex on 2007-11-03
Here is a comparison. Right now, I have another Hard Drive running Gutsy Gibbon and Ubuntu Studio. It has all the setting identical to the disk that has problem.

```
root@ableblue:/home/teddy# parted /dev/hda p

Disk /dev/hda: 40.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  38.6GB  38.6GB  primary   ext3         boot 
 2      38.6GB  40.1GB  1448MB  extended                    
 5      38.6GB  40.1GB  1448MB  logical   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.     
```

I see that "ext3" mentioned in this disk, but in the disk that has problems (and also the one which contains all my crucial files), it is shown blank! Could this is a file syetem corruption? Or some other unfortunate issue? :popcorn:

---

### Post by Herman on 2007-11-03
Hello redenex,
> Why does it show msdos in there? It's just letting you know you have a msdos type of partition table. Our partition tables are located inside the MBR, (or disk label). There are lots of different kinds of disk labels (Master Boot Records), such as msdos, amiga, bsd, dvh, gpt, mac, pc98, and sun, just to name a few. Ubuntu and most Linux distros use a disk label, (or MBR) that complies with the rules that were written down for the msdos style of disk label.  At least we use an msdos type of disk label by default, I have read somewhere that Ubuntu can be installed in hard disks with other disk labels as well.
>  This was a perfectly running system on Ubuntu Studio (upgraded to Gutsy on 18th Oct). The Grub Error 17 started to show while I once restarted the system. Moreover, the partition, I am sure is ext3! Will wait for your reply to try out other things! Okay, that's good that you are sure it's ext3.
> I see that "ext3" mentioned in this disk, but in the disk that has problems (and also the one which contains all my crucial files), it is shown blank! Could this is a file syetem corruption? Or some other unfortunate issue?  I hope it's only file system corruption caused by an electrical interruption or an improper shut down or something simple like that, because there is a good chance we can use Linux commands to easily fix corruption caused by those kinds of things. 
If the hard disk has a mechanical problem like a bad bearing or physical damage to the surface of the platters then a file system check or other such Linux commands won't be able to save it. Maybe we can get it to be readable again long enough to rescue your data though.

Chances are it has nothing to do with upgrading to Gutsy at all, but upgrading was a time when a lot of writing to your hard disk was taking place. If a small problem of some kind already existed quietly without being noticed, doing a large amount of writing to your hard disk in a short time would have made the problem get bigger fast. The same thing could have happened no matter what the nature of the data you were writing to your hard disk might happen to have been.
At the moment we can't really tell what the problem is exactly yet, but we can try to find out by running some commands to test for clues.

The command I already gave you should be a good starting point and it should either fix your problem, or at least give some feedback that should be helpful, or maybe we'll need to run more tests. 
```
sudo e2fsck -C0 -p -f -v  /dev/hda1
```Another command you might try later if you want would be 'sudo badblocks /dev/hda1', you might try that if you want to see if your hard disk itself is getting old or has a physical problem, but I don't recommend you try that one until later.
> I have Feisty Fawn Live CD, does it have GParted too? Yes, the Feisty Fawn Live CD does have GParted in it, that will be more than good enough for taking a look at your partitions with, and doing many types of partitioning work.
It is a very old version and not as useful as the latest version of GParted that Gutsy Gibbon has. More recent versions of GParted can move Linux partitions and run file system checks from the right-click menu and lots of other things.
The file system check I gave you is the same as the one in GParted LiveCD, but GParted LiveCD also runs a few other useful commands like resize2fs as well, just in case they are needed.  If you you want the latest version of GParted but you don't want to download a whole Gutsy Gibbon Live CD just to get it, you can just download [GParted -- LiveCD]("http://gparted.sourceforge.net/") instead. That will be only around 50 Mb to download and is very useful.

Regards, Herman :)

---

### Post by redenex on 2007-11-05
I ran GParted Live CD, and well...... /dev/hda1 FileSystem: UNKOWN!

Still no luck!:(

---

### Post by Herman on 2007-11-06
Hello redenex,
>          I ran GParted Live CD, and well...... /dev/hda1 FileSystem: UNKOWN! Okay, that is what I was expecting already.

Did you try running a file system check with GParted LiveCD to see what feedback you might get from it?

A file system check might fix your problem or at least give us further information that will tell us what other commands to run next in order to fix your problem.
I am still hoping you will try running the command 'e2fsck -C0 -p -f -v  /dev/hda1'
```
e2fsck -C0 -p -f -v  /dev/hda1
``` If you run that command from a terminal in GParted Live CD or 'sudo e2fsck -C0 -p -f -v  /dev/hda1' from a termianl in the Ubuntu Live CD it should give you some output that you can post here to show me what happened.
If you use the GParted LiveCD and right-click on the partition and click 'check, then click 'Apply' on the toolbar, and 'Apply' again in the confirmation box, GParted LiveCD will run e2fsck -C0 -p -f -v  /dev/hda1 as well as some other commands, for you without the need for you to type anything into a terminal.
To see what happened afterwards, you need to click the 'details' button, it is shaped like a triangle. That expands a text window. To see everything you need to keep clicking all those triangles until it is fully expanded.

I want to see if the feedback from the e2fsck command will tell us something like 'there is no valid superblock in /dev/hda1, or the file system in 'dev/hda1 is not a valid ext file system. If you are sure the file system in /dev/hda1 is an ext3 file system, please run e2fsck -b 32768 /dev/hda1 to restore your superblock from a backup'. (Or something like that, I can't remember the exact words).
If it tells us that, then we will try doing as it says.

Or the e2fsck command might fix your file system already if you are lucky.

Or we might also need to run more commands after e2fsck -b 32768 /dev/hda1 if even that doesn't work and we need to try harder.

Good luck,
Regards, Herman :)

---

### Post by redenex on 2007-11-08
> **Herman said:**
> 
I am still hoping you will try running the command 'e2fsck -C0 -p -f -v  /dev/hda1'
[code]e2fsck -C0 -p -f -v  /dev/hda1

:guitar:Thanks brother! It worked, I have got back all my data, which I would be copying to my new hard disk and back up too!

Thanks again!

Sorry I was a bit late, had some important meetings and seminars! :KS

---

### Post by Herman on 2007-11-08
Hello redenex,
Thanks you for letting me know your problem is solved. 
I am feeling very happy for you too, now :), and I imagine anyone else reading this thread will share your happiness too.

Your data is safe with Linux, because there are lots of very clever programmers making up excellent software for us. If the file system check didn't work and if even replacing the superblock didn't work, we could have still applied several other commands to try to recover your file system with Linux commands for free.
GParted LiveCD also has TestDisk and PhotoRec in it as well, which we might have needed. 
Even if recovering the file system proved impossible, we could still have used PhotoRec at the last, to recover your files if we had to.
We can install TestDisk and PhotoRec in Ubuntu too if we want to.
So as you can see we had lots of resources at our disposal.

I am very pleased the fixing your file system turned out to be so easy.
You can run that command again every once in a while too, whenever you like, as it will not do any harm to your file system and often it will do some good, keeping your ext3 file system in good order. 
It is especially good to run that command right away from a LiveCD if you know you have had your computer shut down too fast, (if you had an electrical interruption or something like that, for example).

Thank you for your patience and perseverance too, and good luck with everything from now on,
Regards, Herman :)

---

### Post by redenex on 2007-11-08
Your effort and knowledge......
........ my luck!

Thank you again! :guitar:

---

### Post by meierfra on 2007-11-11
I updated my post [#55 ]("http://ubuntuforums.org/showthread.php?t=442945#55")

Here is a summary of that lengthy post:

1) Device.map is only used when you run "grub-install", "grub --device.map=path_to_device.map" or "update-grub" (and in the latter case only if you do not have a "#groot" statement in your menu.lst")

2) This is the situation where you need to edit the device.map and use "grub --device.map=path_to_device.map" :

root (hdx,i)
setup (hdy)

But only if all of the following conditions are met:
a) x is different from y
b) grub is guessing the boot order of (hdx) wrongly.
c) One does not want or is not able to change the boot order of (hdx)
d) One is not able to get to the "grub commandline" at boot-up. (At boot-up, grub always uses the correct order)

mbwardle case [ #9]("http://ubuntuforums.org/showthread.php?t=442945#9") is a good example for this, although I think he/she could just have switch "Linux" and "Media"  in the boot order in the bios  instead of  editing  device.map and menu.lst

---

### Post by Herman on 2007-11-12
Hello meierfra,
Thank you for taking the time to clear that up for me.
That makes sense to me now, and I have no problem agreeing with what you are telling me. 

I feel more confident about helping people with that type of problem now.

Thanks again,
Regards, Herman :)

---

### Post by MQMike on 2007-11-12
meierfra,  Thank you, too, from me, for your postings here.  

I need to catch up with this and review what we've said here and will do that first thing this week.  For some reason, I was not getting notices of postings to this thread to my Thunderbird mail and just got this notice this morning--sorry about popping in after being absent; I will study what you have done here on this topic for us--It looks good and interesting  :)   .

--Mike

---

### Post by MQMike on 2007-11-12
meirerfra, OK, I'm  up to speed here again, and yes, thanks for your work on this.  Your work looks good, I’ve saved it, and hope to also have some time to play with this further.  Thanks, again!
--Mike

---

### Post by andycap on 2007-11-14
I must agree that mbwardle did an excellent job. I actually have an almost exact setup as him, 

80GB /dev/sda for Windows XP
250GB /dev/sdb for Windows Vista
80GB /dev/sdc for Ubuntu Linux

I ran into the exact same problem and this really helped!

Thanks so much.

---

### Post by jimraehl on 2007-11-21
Thanks to everyone for such an enlightening thread.  I had error 17 also.  The first few posts I read pointed out that the Ubuntu ext3 partition might have moved.  I then realized from my Acronis Disk Director display, that the program makes an Extended partition in unused spece, when it copies a Primary partition, thus adding an extra partition number.  I deleted the new Extended partition, and made a new Primary again in the same place.  All back to normal, except for a messy OS folder copy in Windows Explorer.

The thread also is an excellent tutorial on GRUB idiosyncrasies.  My total previous GRUB experience was installing it in the ext3 partition (using the alternate Ubuntu CD) and leaving Wndows to handle the initial boot.  The strategy was in this thread for dual-boot Windows XP and Ubuntu:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

The thread confirmed my experience that ReiserFS doesn't work for installing Ubuntu.  Stick with ext3.  So much useful information in one thread.

Jim

---

### Post by katepaulk on 2007-11-22
mbwardle's post for this was excellent, but didn't completely cover my situation.

When I first installed Ubuntu (Feisty, since upgraded to Gutsy), I had some USB drives plugged in. Ever since, Grub couldn't boot if I had any USB or flash drive plugged in. Since I'm using an external USB hard drive to store data, this was something of a nuisance.

Editing device.map to remove the unwanted USB entries (since they were never the same twice anyway) didn't help, so I finally tried mbwardle's solution. 

Here's what I found:

1. step 9 should have been --device-map=device.map. Someone else in the thread has mentioned this.
2. Steps 10 & 11 could not be run on the live CD. I checked menu.lst (which had no references to the USB drives, since they don't contain anything bootable), then closed down and restarted.

When the Grub menu came up, I used "c" to move to the Grub command line, where mbwardle's steps 10 and 11 worked perfectly.

Reboot was fine. Next step is to try booting with a USB drive plugged in, but that can wait :) First was to not break anything I had!

** and I get the same error booting. Oh well... I guess I'll get it sorted out eventually! 

Kate

---

### Post by meierfra on 2007-11-25
It seems that mbwardle method in post [9]("http://ubuntuforums.org/showthread.php?t=442945#9") sometimes leads to an error message at Step 10 or 11.  To avoid this problem the following needs to be inserted between Step 5 and Step 6  (see  Herman's post  [34]("http://ubuntuforums.org/showthread.php?t=442945#34")):

5.1)  Run  "mount -t proc none /ubuntu/proc"
5.2)  Run "mount -o bind /dev /ubuntu/dev"

And as pointed out before: Step 9 has a typo and should be

9) Run "grub --device-map=device.map"

mbwardle: If you happen to read this, could you edit your post accordingly? Thanks.

---

### Post by prc320 on 2007-11-25
Yes you have guessed it I too have Error 17.............

It is a laptop toshiba 2001/2 no cd-rom or fdd

I get "Check system. Then press [F1] key."

This gets the following: System Setup (1/2) ACPI BIOS version = 1.30

What do I do now?

---

### Post by Herman on 2007-11-25
How did you install Ubuntu if you have no CD/DVD drive?
Did you install from a partition with the Live CD files copied into it, or from a USB disk with the Live CD in it or did the CD/DVD drive quit since then? 

Sometimes you can get old CD/DVD drives working again simply by cleaning the optical lens with a cotton bud (Qtip) dipped in methylated spirits (denatured alcohol).

If your laptop can boot a USB disk then  you should be able to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") for USB to get your computer started up. After that, fixing the problem will be much easier.

If your laptop cannot boot a USB disk or you don't think you can get it to do that you might have to remove the hard drive from the laptop and plug it in to another computer to work on it.

Is this a new installation or one that's been in use for some time and has data in it? 

Some models of Toshiba laptops have the 'Express Media Player' in them, and that means there might be software for that in the first track of the hard disk which is normally reserved for boot loaders and other programs of that nature. That software has been known to interfere with GRUB.
There's a special dual boot site dedicated to Toshiba laptops here: [U][Matthew J. Miller's HOWTOs: Dual Booting Ubuntu Linux and Windows on a Toshiba Laptop]("http://www.google.com.au/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.matthewjmiller.net%2Fhowtos%2Fdual-boot-linux-and-windows%2F&ei=vctJR7yWIYqopwTu-9CwCw&usg=AFQjCNHig8N2cD5twwEkyIBdwYI7GkPaKg&sig2=nL468VN_IehG7M_K4YoLcA")
[/U]If your model of Toshiba Laptop does not have the 'Express Media Player' in it then you can probably just do a regular install like everyone else.
Does yours have the  'Express Media Player' in it?

Regards, Herman :)

---

### Post by prc320 on 2007-11-26
1. No, it used to have a CD but that lost a piece of plasitc to fit a around the middle. It is out balance now!

2. No I don't have Express Media Player installed!

---

### Post by leat on 2007-11-26
I have the same problem, but I can't try the fix because I can't get to the HD menu thingie in the BIOS since I use S-ATA, How do I do ? :P

---

### Post by Chinfrim on 2007-11-26
I tried putting GRUB into my pen drive but I encountered some troubles different from the home page,

I had to mannually copy files around the place, I Untared it just ok, when on grub, it woulnt run the comman geomtery (hd so, I'd just pick numbers untill i found my pen drive. I setuped it and booted using the pen.. now it says.

"NTLDR is Missing
Press any key to restart"

Help! This grub thing is driving me nuts!

There isn't any specific cases in that guide for people who can't boot anywhere and need to use the live cd to get anywhere! or maybe there is, im just too blind for it!

---

### Post by Herman on 2007-11-27
> 1. No, it used to have a CD but that lost a piece of plasitc to fit a around the middle. It is out balance now! Okay.
>  2. No I don't have Express Media Player installed! Good.

If your laptop can boot a USB disk then  you should be able to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") for USB to get your computer started up. After that, fixing the problem will be much easier.

If your laptop cannot boot a USB disk or you don't think you can get it to do that you might have to remove the hard drive from the laptop and plug it in to another computer to work on it.

There are other options you could look into, but the ones I can think of all involve tinkering with hardware and rigging things up in strange ways that a normal person wouldn't bother attempting. It depends on how keen you are and what resources and abilities you have.

Regards, Herman :)

---

### Post by Herman on 2007-11-27
Hello leat,
What kind of computer do you have? 
I really need to know *some* information before I can help you at all.
You should be abel to get into your BIOS or boot from the BIOS using F8 or F12 keys regardless of what kind of hard dirves you have, SATA, PATA or even a USB disk. :)

---

### Post by Herman on 2007-11-27
Hello Chinfrim,
I need more information from you also, what home page are you talking about?

What GRUB are you installing in a USB?  Gnu/GRUB or Super Grub Disk?

"NTLDR is Missing Press any key to restart" is an error message from Windows and has nothing to do with GRUB. I'll go into more details about that later.

What guide are you talking about?

Regards, Herman :)

---

### Post by Chinfrim on 2007-11-27
Things evolved,

I wanted to format my whole computer since I wanted to completely get rid of many useless crap i have been ammounting,

So.. I picked up my ASUS Recovery Disk, and my ASUS Driver disk, and told it to format using 2 Partitions.

It did, asked for drivers, installed the drivers, I reboot it and...

GRUB does it again, Loading Stage 1.5 and Error 22 Pops up! 

What now?

---

### Post by Herman on 2007-11-27
>  GRUB does it again, Loading Stage 1.5 and Error 22 Pops up!
No, GRUB didn't 'do it again', you did!
And no-one can help you without you providing any of the necessary details, I'm sorry, but it's just impossible to guess what could be wrong untill you can help me or someone elae to help you by telling us what you are trying to do, firstly, and then some details about your partitioning and booting arrangement so far.

Otherwise it's kind of like playing 'Pin the tail on the donkey'.

Regards, Herman.

---

### Post by Herman on 2007-11-28
24 hours later....
Okay, here: [     Grub error 22]("http://users.bigpond.net.au/hermanzone/p15.htm#22").

Maybe you can use that link to help yourself. :)

Here's another one too: [ NTLDR is missing, press any key to restart]("http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to").

I am trying to guess what the heck you could be on about. :confused:
I didn't mean to be unfriendly at all, I  want to help you, and if you still want specific help  all you need to do is take a little bit more time to explain to me what you are actually trying to do.

For example:
"I tried putting GRUB into my pen drive but I encountered some troubles different from the home page,"

Might mean:
I tried putting the [GNU/GRUB]("http://www.gnu.org/software/grub/") into my pen drive but I encountered some troubles different from the home page,

OR, it might mean:
I tried putting [Super Grub Disk for USB]("http://sgd.benjamin-butschko.de/?section=download#usb") into my pen drive but I encountered some troubles different from the home page,

Or, it might mean, 
I installed Ubuntu and tried installing Ubuntu's GRUB into my pen drive but I encountered some troubles different from the home page,
(Maybe you are trying to install Ubuntu from some guide I'm not familiar with).

Or, it might mean something else...

I'd like to help you, but I need to know just a little more about your specific circumstances and what it is you are trying to achieve. :)

Regards, Herman :)

---

### Post by meierfra on 2007-11-28
Herman: Chinfrim solved the problem in a different thread but is to lazy to let you know:
[URL="http://ubuntuforums.org/showthread.php?t=623962"]
http://ubuntuforums.org/showthread.php?t=623962
[/URL]

---

### Post by nmurlidh on 2007-11-29
Hi:

I have a thinkpad and had both Windows and Ubuntu on it.
I tried to format my C Drive using IBM's rescue and recovery system. When i restarted my laptop, i could not get in because I got the error message "Grub Loading, Please wait.. ERROR 17"

What do I do now to get my system back to life??

Nupur

---

### Post by meierfra on 2007-11-29
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Herman on 2007-11-29
> Herman: Chinfrim solved the problem in a different thread but is to lazy to let you know:[URL="http://ubuntuforums.org/showthread.php?t=623962"]
http://ubuntuforums.org/showthread.php?t=623962[/URL] Thank you very much for letting me know, meierfra. :)
That saved me some work.

Regards, Herman :)


---

### Post by kerredc on 2007-12-02
I'm new to Ubuntu, decided to install it on a system with 2 HDD, and I'm getting Error 17.  Below is my 'fdisk -ul' output:

```

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb07e6997

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   123732630    61866284    7  HPFS/NTFS
/dev/sda2       123748695   125853209     1052257+  82  Linux swap / Solaris
/dev/sda3   *   125853210   320159384    97153087+  83  Linux

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b7d0b7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    80035829    40017883+   c  W95 FAT32 (LBA)

```

...and the bottom of my menu.lst file:

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9203742c-66d0-4b3a-ac40-f108fbd7d57b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9203742c-66d0-4b3a-ac40-f108fbd7d57b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Any help would gladly be appreciated.

---

### Post by merlinus on 2007-12-02
This has lots of useful info:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by meierfra on 2007-12-02
fdisk and menu.lst look fine. Check you bios and make sure your ubuntu drive is first in the boot order.

And a quote from [Hermanzone Error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17"):
Make sure your hard disks are properly detected in your BIOS and set to AUTO, (not LBA, large or normal)

---

### Post by ianzhere on 2007-12-07
I got the GRUB error 17. I did however change some of the partitions, but i thought i knew what i was doing. I am using 1 HD. any ideas?

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   171573297    84249625    7  HPFS/NTFS
/dev/sda3       171574200   195045164    11735482+   f  W95 Ext'd (LBA)
/dev/sda4       195045376   234438655    19696640    7  HPFS/NTFS
/dev/sda5       177454053   195045164     8795556    7  HPFS/NTFS

---

### Post by Herman on 2007-12-07
> I got the GRUB error 17. I did however change some of the partitions, but i thought i knew what i was doing. I am using 1 HD. any ideas?

```
 Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device______Boot______Start__________End______Blocks______Id______System
/dev/sda1______________2048______3074047___1536000______27___[COLOR=Red]**Unknown**[/COLOR]
[COLOR=Red]** Partition 1 does not end on cylinder boundary.**[/COLOR]
/dev/sda2______*____3074048___171573297___84249625______7____HPFS/NTFS
/dev/sda3_________171574200___195045164___11735482+_f  W95___Ext'd (LBA)
/dev/sda4_________195045376___234438655___19696640______7___HPFS/NTFS
/dev/sda5_________177454053___195045164____8795556______7___HPFS/NTFS
```Hello ianzhere,
It looks like your partition editor has had a problem with your partition table and caused the first partition to be goofed up.

First you need to make a backup of all your important data and any other data you can if you haven't done so already.

Second, you will probably want to try whatever partition editor you were using to work on your partitions to see if it thinks it still recognizes the /dev/hda1 partition it changed. 
If it does think your /dev/hda1 partition is fine, you might be able to try resizing your /dev/hda1 partition just a little smaller and see if it will fix its mistake and end your partition on the cylinder boundary this time and hope that will fix everything. If not there are more things we can try.

Regards, Herman :)

---

### Post by skibum1321 on 2007-12-10
I just got pretty much the same error as was described above. I have Vista and Ubuntu dual booting. It was booting fine until I tried to boot up Vista today. That is when I began getting a Grub Error 17.

Here is my fdisk:
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99113d0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    10242047     5120000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    10242048   177990094    83874023+   7  HPFS/NTFS
/dev/sda3       178000200   235946654    28973227+  83  Linux
/dev/sda4       235946779   390719487    77386354+   f  W95 Ext'd (LBA)
/dev/sda5       238532608   390719487    76093440    7  HPFS/NTFS

```

And here is the menu.lst:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec3fd668-d102-4e6b-a036-de3d53c5c282 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ec3fd668-d102-4e6b-a036-de3d53c5c282 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```
I just changed the Vista entry to be rootnoverify after I got the error, but to no avail. Any suggestions to fix this?

---

### Post by MQMike on 2007-12-11
Interesting.  And confusing, with the Vista-thing.  It uses the two partitions, one for recovery.  You guys are both getting the same weird partitioning and errors.

skibum1321, it looks like your Ubuntu is on (hd0,2), not (hd0,3) as your menu.lst says.
sda3 = (hd0,2)

Looks like you have an extended partition “at” sda4.

And, yes, for Vista, you do, specifically, want rootnoverify.

Try changing (hd0,3) to (hd0,2) for Ubuntu in the menu.lst.

---

### Post by skibum1321 on 2007-12-11
That didn't work for me. I tried to change it to hd2 and also tried to comment out the first Vista entry (which is the recovery partition and the one that says "Partition 1 does not end on cylinder boundary").

One other thing that I should point out is that my menu.lst is not in /boot/grub. It is in /media/disk/boot/grub. I have to mount a volume that is labeled 27.6 GB Volume before I can even access the menu.lst. I'm not sure if this makes a difference. I think it has been this way since I first installed Ubuntu. Grub worked for a few weeks - until I tried to load Vista.

Any ideas on what else I could try?

---

### Post by kotak07 on 2007-12-11
wow a whole error 17 thread. i've been looking all around this forum for a problem like mine but unlike all of yours mines a bit peculier. [http://ubuntuforums.org/showthread.php?t=638047](http://ubuntuforums.org/showthread.php?t=638047)

I can't boot any ubuntu Live CD and super grub doesnt do anything also tho zenwalk does but the advice that was given i think requires me to delete my sda 2 which i dont want to do. Please i need help as quick as possible. 
Thanks.

---

### Post by xof7 on 2007-12-12
I seem to be having a uniuqe error 17 issue.

My computer has 3 hard drives in it. They are as follows:
sata 320gb > xp sp2 install
sata 250gb > misc files
ide 40gb > ubuntu 7.10 install

I've modified devices.map heavily with no luck. When I try to use geometry in grub, or try to do anything with grub, it can't find any hard drives.

 hd0 through hd10 is what i've tried with no luck.

Any ideas?

---

### Post by Herman on 2007-12-12
Originally posted by meierfra in post #68,
> I updated my post [#55 ]("http://ubuntuforums.org/showthread.php?t=442945#55")

Here is a summary of that lengthy post:

1) Device.map is only used when you run "grub-install", "grub --device.map=path_to_device.map" or "update-grub" (and in the latter case only if you do not have a "#groot" statement in your menu.lst")

2) This is the situation where you need to edit the device.map and use "grub --device.map=path_to_device.map" :

root (hdx,i)
setup (hdy)

But only if all of the following conditions are met:
a) x is different from y
b) grub is guessing the boot order of (hdx) wrongly.
** c) One does not want or is not able to change the boot order of (hdx)**
d) One is not able to get to the "grub commandline" at boot-up. (At boot-up, grub always uses the correct order)

mbwardle case [ #9]("http://ubuntuforums.org/showthread.php?t=442945#9") is a good example for this, although I think he/she could just have switch "Linux" and "Media" in the boot order in the bios instead of editing device.map and menu.lst
SO, first try going into your BIOS set-up and changing the  hard disk boot priority, if your computer has that ability in the BIOS.
I'm not sure what your BIOS would be like, but here, for example, is how I do that in one of my own computers [    Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").
That has been found to be the easiest and best way for some computers.

Or, if you can, get a   [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and boot from that (with [Super Grub Disk]("http://sgd.benjamin-butschko.de/") you'll surely be able to if you can't any other way). Remember the commands you used to boot successfully, as those will be the same commands you can add to your /boot/grub/menu.lst file later, and you might have to re-install GRUB to a different hard disk's MBR if you decide to do it that way.

Regards, Herman :)

---

### Post by skibum1321 on 2007-12-13
I used the Super Grub disk to boot up the other night and it worked. I just did it with the GUI so I'm not really sure how that would translate into command line entries. Basically, I chose to boot GNU/Linux and then it brought me to the GRUB menu that I am used to seeing where I can choose Linux or Windows. It let me boot into either one - now I just need to translate that into something that I can put into my menu.lst.

Can someone help me figure out what I need to do from here?

---

### Post by Herman on 2007-12-13
Okay then, when you boot Ubuntu again, please post here in this thread a copy of the bottom part of your /boot/grub/menu.lst file, (mainly the part with all the boot entries), and a copy of the output from 'sudo fdisk -lu'
```
sudo gedit /boot/grub/menu.lst
``````
sudo fdisk -lu
```Regards, Herman :)

---

### Post by Raven18940 on 2007-12-16
> **mbwardle said:**
> I got this error after installing the Ubuntu 7.10 release candidate.

The error usually happens because Linux and your BIOS detect your hard disks in different orders.  GRUB tries to translate between the two using the device.map file in /boot/grub/device.map, which is automatically generated.  Chances are, it guessed wrong.

In my case, I have three SATA hard disks.

My BIOS sees them as:
HDD1 - 80 GB - Windows
HDD2 - 80 GB - Linux
HDD3 - 250 GB - Media

Linux sees them as:
/dev/sda - 80 GB - Windows
/dev/sdb - 250 GB - Media
/dev/sdc - 80 GB - Linux

So it generated device.map assuming that order was correct, i.e.:
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

When the installer installed GRUB using that data, it tried to install the first part of GRUB on /dev/sda and told it to look for the OS on /dev/sdc.  Unfortunately, this translated to "install on (hd0) then look for the OS on (hd2)", so it was looking for the OS on the wrong drive.

To fix it, you have to teach GRUB which order the BIOS uses.  To do this, follow these steps:

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"
8) Edit device.map (using vi or another text editor)

In my case, my new device.map was:
(hd0)    /dev/sda
(hd1)    /dev/sdc
(hd2)    /dev/sdb

which told GRUB that sdc was really the second hard drive, not the third.

9) Run "grub --device.map=device.map"
10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)

You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that.  This is what we want.

12) Edit menu.lst

You need to change references from (hd2,0) to (hd1,0), or whatever your Linux boot drive was autodetected as to whatever it is according to your BIOS.

If you get this step wrong, you'll see an error message something like:
Error 17: Cannot mount selected partition

meaning it's looking for a Linux file system on that partition, but it can't find one (because the drive device number is wrong in menu.lst).

13) Reboot

14) Celebrate or complain in this thread!

A much simpler solution is to just take you SATA cables and swap them.

---

### Post by skibum1321 on 2007-12-19
I actually got this fixed. I used the repair option on the Super Grub CD and it did all of the work for me :).

Thanks for your help.

---

### Post by SigmaGru on 2007-12-27
Hello All

I am having the same Error 17 message 

Thiis  is my output(after fdisk -lu)

device boot             system
/dev/sda1  *           HPFS/NTFS
/dev/sda2                    W95/Fat32(LBA)
/dev/sda3                 Linux

I need help getting back the dual-boot i had with Vista on the NTFS and Ubuntu Gusty gibbons on Sda 3 

I am having a rough time uderstanding

---

### Post by Herman on 2007-12-27
:) Hello SigmaGru,
The first thing to do probably is to get yourself a [Super Grub Disk]("http://sgd.benjamin-butschko.de/") if you don't already have one and you should be able to boot with that for now.
That will make you feel better and you'll be able to use your computer again for whatever it is you use it for until we get the booting problem sorted out.

One thing you will find helpful is that you can copy things like your output from commands like 'sudo fdisk -lu' and paste them into your replies to the forums here, that will make things a lot easier for you. If you try to type things out by hand we only get part of the info we need and you'll be doing a lot of work for nothing. 
Thanks for being thoughtful enough to include at least part of your fdisk output though, a lot of people don't bother at all until they have to. :) That one will do for now.

The other thing that will be needed to help solve your problem will be a copy of the bottom portion of your /boot/grub/menu.lst file. 
The idea is to compare the info from your fdisk output with the info in your menu,lst file to see if they match up.
```
sudo gedit /boot/grub/menu.lst
```Thanks!

You only have one hard disk, so hopefully this will be quite simple.

Are you getting this error when you are trying to boot Windows, or when you are trying to boot Ubuntu? 

Regards, Herman :)

---

### Post by fenixartzz on 2008-01-01
hey thanks a lot 
i dont know but without doing anything system started giving error 17
thanks to the tut here i used live cd to make changes to the menu.lst file and its working alright now

---

### Post by ac3raven on 2008-01-03
sure that's a good tutorial, but I'm not allowed to over write device.map with my new one.  Ubuntu just won't let me.  How do I get around that?

---

### Post by Herman on 2008-01-04
Are you opening the file with a 'gksudo' command from your terminal?
Like this,
```
gksudo gedit /boot/grub/device.map
```

---

### Post by ac3raven on 2008-01-04
Okay I got that squared away now, but what exactly do I edit in the menu.lst?  I pretty sure I know, I just want to make sure I do it right.  Could you post your menu.lst maybe?

---

### Post by ac3raven on 2008-01-04
now when I try to save menu.lst, it says I'm trying to save on a read-only disk and it won't save the file.

---

### Post by Herman on 2008-01-04
Are you working in a Live CD?

---

### Post by ac3raven on 2008-01-05
yes, no OS to speak of.

---

### Post by Herman on 2008-01-05
Oh, okay then. Here is a link about how to mount your hard disk installed Ubuntu file system in a Ubuntu Live CD and access a few of the files, such as menu.lst, 
[                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000].
If you need specific help then let me know and post the output from 'sudo fdisk -lu' and the bottom part of the menu.lst file. That information is usually important for solving booting problems. Maybe a look at /boot/grub/device.map will help too.
Regards, Herman :)
[/COLOR][/COLOR]

---

### Post by ac3raven on 2008-01-05
Okay, I give up.  Last time I tried to dual boot XP and Ubuntu on my raid 0, I erased my xp partition, and ended up with error 21, hence no OS essentially.  Now, I try to install Ubuntu on a 500gb external usb hard drive, thinking it wouldn't touch my xp partition.  But it turns out that even though the live cd doesn't let me mount my raid array without dmraid, it is still being recognized as hd0,0, and there for when i install ubuntu on my 500gb hdd, it doesn't know to boot from that hdd rather than the raid array.  It automatically puts grub on the raid array because it sees that as the primary partition, thus overwriting the windows mbr, and producing error 21, or after a few terminal tricks, error 17.  So no OS, that is until I decided to put my xp pro disk in, delete the linux partition and create a xp partition on the 500gb, thus refreshing the mbr.  I'm not going to touch my raid array with ubuntu, but I haven't given up hope of installing it on a separate hdd and separate partition, and dual booting that way.  I'll just have to experiment and research and consider some options.

---

### Post by Herman on 2008-01-05
Oh, okay then. Sorry, I didn't know you were using RAID.
I usually try not to get involved with giving any advice to do with RAID because I haven't had any experience with the myself. I've only read about it a little and decided it's not something I'm that keen on.  There are too many different kinds of RAID for me to feel like even beginning to bother studying up on it or experimenting with it

Ubuntu wasn't really designed for installation in an external USB drive, at least not easily. It's designed as a replacement for Windows inside the computer in an internal hard disk.
Failing that we're welcome to dual boot for as long as we like, with the idea of deleting Windows eventually when we learn how to use Ubuntu. 
No-one really cares if you ever do or not, but that's the implied idea.
Many people do manage to install in an external hard drive though, but it takes a little extra knowledge to direct GRUB to the external hard drive's MBR, and configure GRUB.
If Ubuntu was meant to be installed in an external hard drive, they would make it simple, and give you a button to push to select that option and GRUB would install to the correct MBR for you. 

Installing Ubuntu in a separate hard disk sounds like a better idea. That's what most people do and it should be a lot simpler.
You are welcome to read some of my web pages in my signature links if you like. The GRUB page might interest you. If you understand GRUB a little you'll find that GRUB is actually very easy to control and direct to any MBR or boot sector you like. GRUB's quite simple really. It's just like anything else in life, when you take a little time to understand it it'll be useful to you and then you'll like it.
GRUB even supports RAID too if you know how, at least certain kinds of RAID, but like I said, I'm not the right person to give advice on that.

My website is about the 'Alternate' install CD, which give you the option to select where you want to install GRUB, and lots of other options as well. all the information is in my signature links if you want it.

Regards, Herman :)

---

### Post by ac3raven on 2008-01-06
thank you very very much.

---

### Post by MQMike on 2008-01-06
FWIW,
I feel the same way about RAID.  And the “experts” I hang out with (hardwareguys.com) say that it doesn't really offer any perceivable advantages on desktop systems (vs servers, where it can be useful).  It does, however, seem that where there's RAID on a desktop, there's problems and exceptions.

As for installing K/Ubuntu to external USB hard drive, it is a GRUB exercise and gets into drive shifting and so on.  I've done it often with Kubuntu and wrote up the how-to and tips on USB drive shifting at:
How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)
How to install K/Ubuntu 7.04 to an external USB hard disk drive (HDD), Reply #1
USB experiment: USB drive shifting  Reply #5
Simplifying your menu.lst and all the rest of it,  Reply #8
Super Grub Disk, GRUB, GParted & Puppy on a flash drive  Reply #10

From a GRUB standpoint, everything you do with external USB HDD applies to USB Flash Drive (UFD), as well.

---

### Post by Herman on 2008-01-06
There are lots of good videos about how to install Ubuntu and  what to do with it after you install it at  [http://screencasts.ubuntu.com/ ]("http://screencasts.ubuntu.com/")

One of them is about how to use the 'Alternate' CD, and that one discusses setting up Ubuntu with RAID. [Installing Ubuntu Part2]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2")

---

### Post by cmol on 2008-01-06
Hello

I just installed my new laptop (came with XP pro). Installed Ubuntu on it along with the XP pro.

Everything worked fine!
Then i thought: i want to make my storage ntfs instead of fat 32, so i partitioned it to ntfs, and then i got grub error 17.......

I been reading things all night long.. editing my menu.lst file from using root to rootnoverfy, and still it makes errors.

I have the fear, that grub data was stored en the MBR of my 'storage drive', but i dont really know what to do.

here is my fdisk -lu output

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    21109409    10554673+   7  HPFS/NTFS
/dev/sda2        21109410    32820794     5855692+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3        32820795   109338389    38258797+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4       109347840   117195119     3923640   12  Compaq diagnostics
Partition 4 does not end on cylinder boundary.
/dev/sda5        32820858    36820979     2000061   82  Linux swap / Solaris
/dev/sda6        36821043   109332719    36255838+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

the sda1 is my windows xp partition
sda2 ubuntu

then it gets a little weird (for me), course the real order is : extended with SWAP and storage drive, and then this weird ibm recovery drive in the end.... But thats not outputs here, but that maybe just my stupidity..

here is my menu.lst

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b6a510c-e3d6-4f74-bce1-dbccf5f2245c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b6a510c-e3d6-4f74-bce1-dbccf5f2245c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Can anybody help?

---

### Post by Herman on 2008-01-06
It looks to me like the partition editing program has changed your partition numbers.
It has shifted your partitions off the cylinder boundaries too.

Try changing your menu.lst to have Ubuntu as (hd0,1) instead, because fdisk says it's /dev/sda2 now.
I think that's the first, and biggest problem.
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,**1**)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=6b6a510c-e3d6-4f74-bce1-dbccf5f2245c ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,**1**)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=6b6a510c-e3d6-4f74-bce1-dbccf5f2245c ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,**1**)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```
Try that first and tell me if if helps or not.

Regards, Herman :)

---

### Post by Herman on 2008-01-06
Probably you'll need to re-install GRUB too. Because your partition numbers have changed, and edit /etc/ftab as well, after you get it booted.

To re-install GRUB, you use the LiveCD and do,
```
sudo grub
```
```
root (hd0,1)
```
```
setup (hd0)
```
```
quit
```

---

### Post by cmol on 2008-01-07
Wuhu.. Up and running :)

I booted up my system, and everything seemed to work fine. Everything was mounted right, and i had all the access i needed...

Thanks for the help :)

---

### Post by Herman on 2008-01-07
:)  Ah, excellent! Well done! 

Just make sure you remember to definitely make a good backup before you touch your hard disk with another partition editor next time. The fact that this has happened, and that some of your partitions don't end on cylinder boundaries could imply a glitch in your partition table somewhere.

Use only good 'Parted based partition editors like GParted, QTParted, Partman.

Regards, Herman :)

---

### Post by cmol on 2008-01-07
Yeah..

I think it's a little shitty that gparted can't partition into ntfs, now that ubuntu do have the ntfs-3g support. So I was forced to use another program, and make the think over 2 times.

But thanks again :)

---

### Post by Herman on 2008-01-07
What makes you think GParted can't partition NTFS? :confused:

---

### Post by cmol on 2008-01-07
> **Herman said:**
> What makes you think GParted can't partition NTFS? :confused:

I hade no NTFS in the list of filesystems when i made my system in the beginning...

---

### Post by Herman on 2008-01-07
[IMG]http://gparted.sourceforge.net/screens/gparted_10_small.jpg[/IMG]

GParted can do everything with NTFS, detect, read, create, grow, shrink, move, copy and check.
However it does also leave a marker in the file sysetm that makes Windows run CHKDSK on it if it is part of a Windows system, GParted Documentation, [How to resize and NTFS partition]("http://gparted.sourceforge.net/larry/resize/resizing.htm").
I have created partitions myself and formatted them with the NTFS file system with GParted, so I am sure. 
Normally I don't use NTFS for anything, but it was to try to find out hoe to help someone use TestDisk to recover a deleted operating system. But I kept the NTFS file system for a long time afterwards and stored data in it too, and never had any problems with it. That includes writing to it from Ubuntu too. :)

Anyway, I hope you have good luck with your partitions and I hope you like Ubuntu too. If you have any more problems let me know and I'll give you a hand again anytime. :)
Regards, Herman :)

---

### Post by cmol on 2008-01-07
> **Herman said:**
> [IMG]http://gparted.sourceforge.net/screens/gparted_10_small.jpg[/IMG]

GParted can do everything with NTFS, detect, read, create, grow, shrink, move, copy and check.
However it does also leave a marker in the file sysetm that makes Windows run CHKDSK on it if it is part of a Windows system, GParted Documentation, [How to resize and NTFS partition]("http://gparted.sourceforge.net/larry/resize/resizing.htm").
I have created partitions myself and formatted them with the NTFS file system with GParted, so I am sure. 
Normally I don't use NTFS for anything, but it was to try to find out hoe to help someone use TestDisk to recover a deleted operating system. But I kept the NTFS file system for a long time afterwards and stored data in it too, and never had any problems with it. That includes writing to it from Ubuntu too. :)

Anyway, I hope you have good luck with your partitions and I hope you like Ubuntu too. If you have any more problems let me know and I'll give you a hand again anytime. :)
Regards, Herman :)

I must have been really tired when i installed my system :P

Well, something allways will come up, and I'll remember to contact you if i can't solve it :)

Like my ubuntu? This is my 4th in one year! I love it :D

---

### Post by Herman on 2008-01-07
Ubuntu is a lot of fun. Have you visited [**Ubuntu Screencasts.com**]("http://screencasts.ubuntu.com/") and had a look at all the great videos you can download for free?
One of them is about how to customize your Ubuntu Desktop.
There are a few others there too that have some pretty neat tips and tricks in them that I didn't know about before too.

Regards, Herman :)

---

### Post by rrcs on 2008-01-08
Hello.

New Ubuntu user; just installed two days ago, next to Windows XP. All was going swimmingly, when the system seemed to freeze completely, so I tried to manually reboot. Have been suffering from Grub error 17 since.

I am trying to follow the instructions [here]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux"), but am getting stuck at step 4/5 in [Mounting Ubuntu with a 'Desktop' LiveCD and editing important files]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD"):

In step 4, the terminal would not accept /media/ubuntu - assuming /Documents/ubuntu will work just as well, I am stuck on step 5: According to the results of the "sudo fdisk -lu" command, the correct partition name of my installed filesystem is /dev/sda3. When I enter the command, with /dev/sda3 substituted, I get the following message:
 
> mount: wrong fs type, bad option, bad superblock on /dev/sda3, missing codepage or helper program, or other error
> In some cases useful info is found in syslog - try dmesg | tail or so
 
I have no clue what this means - halp :( ?

---

### Post by Herman on 2008-01-08
Hm, okay, I wonder if there's a file system problem here,
>  the system seemed to freeze completely, so I tried to manually reboot. Have been suffering from Grub error 17 since.Is it Ubuntu Gutsy Gibbon?
Because I'm fairly sure is you do have the Ubuntu Gutsy Gibbon Live CD, then it will have the latest version of GParted Partition Editor in it.
GParted  Partition Editor contains a file system check option, (something like 'scandisk';, or 'CHKDISK').

Now, what you do is boot the Live CD and find 'Partition Ediitor', I'm pretty sure it's under 'System'-->'Adminsitration', there somewhere.
Start GParted Partition Editor and you should see a view of your hard disk, (partitions).
Does the Ubuntu one have a warning triangle on the line underneath describing it? 
Anyway, regardless of whether it does or not, just right-click on the Ubuntu partition, and click 'Check' from the right-click menu.
Then click 'Apply' up on the tool bar above.
A confimation screen will pop up, click 'Apply' again.
In a few minutes you file system check will be completed.
You can click on the triangular buttons to view the report, there are several of those to see the full report, maybe it won't mean anything to you though.
Hopefully it will say somewhere that 'changes were made to your file system, (it found something wrong and fixed it).
In any case, try rebooting and see if it helped.
It won't do any harm to try that, and if it doesn't work it wil still be good for your file system anyway.
I have a pretty strong hunch that that might fix it, judging from the clues in your story.

I'll be here, I might doze off for a while, but I'll be back to check before too long to see what happened.
Regards, Herman :)

---

### Post by rrcs on 2008-01-08
Yes, it is Gutsy Ribbon; yes, there is a warning triangle (and "unknown" under Filesystem, and "boot" under Flags), but when right-clicking, "Check" is not active/clickable (Delete, Format to, Manage flags, and Information are - Information further says Status is "Not mounted", if that means anything).

---

### Post by Herman on 2008-01-08
:-k Hmmm, Okay, I see.   Well there's our problem then. It seems to be the file system alright. 
But don't give up yet. there a quite a tricks we can try next.
We'll be doing some work from the command line now. 

Open your terminal, in the Ubuntu Live CD, and providing your Ubuntu file system is really /dev/sda3, copy this command and paste it into your terminal and press 'Enter',
```
sudo e2fsck -C0 -p -f -v /dev/sda3
```That's just the same command as we wanted to have GParted run for us. It's usually the right command to fix most problems but this time you might have a special problem.  This might not fix anything, but it even if it doesn't, I'm hoping it will spit out an error message that will give us some clues about what command to try next.
Or maybe iof we're really lucky it will fix it, we'll have to try it and see.

Try that for a start and if you can get a copy of the feedback or error message, if you can post that it's be great. :)

By the way, if you have other operating systems you need to be able to boot in the meantime, until we get this fixed, you would be able to boot with [Super Grub Disk]("http://sgd.benjamin-butschko.de/") if you like.

Regards, Herman :)

---

### Post by rrcs on 2008-01-09
Here's the error message I got:

e2fsck: Bad magic number in super-block while trying to open /dev/sda3
/dev/sda3:
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
     e2fsck -b 8193 <device>

If at this point it looks like something not easily fixed, you don't have to waste time on it - before the system crashed, I had set up the mail account and fetched mails from the server, but not read, but I can get hold of some of them again, and the rest will just have to re-mail if it's that important :)

So if it's not easily fixable, would it be possible/easy enough to reinstall Ubuntu (or is it doomed to go wrong again)?

---

### Post by Herman on 2008-01-09
:)  It is easily fixable, don't worry, at least it should be easily fixable.
There are quite a few backup copies of the superblock which are strategically placed at regular intervals throughout your file system. 
All you need to do is use the command that has been already suggested to restore your superblock from the first available backup and it will be all fixed! :)
Just go ahead and enter the command like this, 
```
sudo e2fsck -b 8193 /dev/sda3
```If you want to see a list of all the spare superblocks you have, take a look with this command,
```
sudo dumpe2fs /dev/sda3 | grep -i superblock
```You can restore from any of those backups, use a third one or fourth one if you want, they are all the same.

Your data is safe with the Linux ext3 file system.

After it's working again I'll show you how to use smartmontools to check to make sure your hard disk is in good health. 
It's up to you. but if your hard disk supports S.M.A.R.T. technology it should have log files in the hard disk's own special memory that may have recorded an error message that we can read.  It won't take very long and might save you from a lot of trouble later on possibly, or maybe it will reassure you that everything's fine and it was just a little hiccup. :)

Otherwise we can just run a badblocks test, that's another way to check and see if your hard drive seems to be okay. 

Regards, Herman :)

---

### Post by indianballer24 on 2008-01-09
I have installed ubuntu on an external hard drive (sdb). But whenever I try to boot from it says grub error 17. I want to install grub on the mbr of my external hard drive. Not on my internal hard drive. Currently I use the supergrub cd to boot into ubuntu. Any help is greatly appreciated. If you need any additional information please tell me. 



My device.map says the following:

(hd0)	/dev/sda
(hd1)	/dev/sdb

sudo fdisk -l says the following

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6c8c6c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         766     6144862+   5  Extended
/dev/sda2   *         767        9729    71995297+   7  HPFS/NTFS
/dev/sda5               2         766     6144831    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9585    76991481    7  HPFS/NTFS
/dev/sdb2   *        9586       19083    76292685   83  Linux
/dev/sdb3           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris

---

### Post by Herman on 2008-01-09
I think you'd find everything would work out a lot easier if you turn the external drive into a data drive, make it NTFS or FAT32 so either operating system can read and write to and from it.  That's how I use my own external USB hard drives, but I use ext3 because it's not important to me to have them read/writable from Windows.

The when you move enough data from your internal hard drive, run the Ubuntu installer and resize a partition in that, and install Ubuntu inside your computer.
Install GRUB to MBR, it will detect Windows and set itself up automatically for you in 99.999% of cases, and then you'll have a good enough set-up until you have learned enough to be able to delete Windows and make more room on your hard drive.
In the meantime, you can use Ubuntu for all your email and internet browsing so you won't be exposing your Windows system to any harm from the internet. :)

External hard drives are designed for use as data storage devices, they don't have the ventillation required to keep them cool over long periods of sustained use such as when they are running an operating system.
There is also a danger when the disk is spinning so much more of the time, of shock damaging the hard drive inside an external USB caddy. Computer hard disks are fastened inside a computer with screws and people don't move their computer case too often while the computer is running.
With an external hard drive, it can be bumped and be knocked off a desk or accidentally dropped more easily and if this happens while the discs are spinning it can cause a head crash and possibly ruin the hard drive inside.

External hard drives are great for backing up and storing data in. That's what they're made for. You plug them in for a few minutes while you transfer your files in or out, then you unmount them and unplug them. They will last for a long time that way.

Ubuntu is not a Linux distribution that is really designed to be installed in an external hard drive. Some Linux distros are made for that, but Ubuntu isn't. If it was they would make it easy for you and make it one of the choices during the install and then it would be automatic.
You can set Ubuntu up in an internal hard drive. Many people do, but it's something best left to the experts, and not the best idea for all day everyday use in any case.

I recommend installing Ubuntu in an internal hard drive, inside the computer.

Regards, Herman :)

---

### Post by indianballer24 on 2008-01-09
I understand that ubuntu is meant to be installed on an internal hard drive, but I use many computers and I like using the same hard drive. Ive been using it for about 1 year now without any problem except grub not working. Ive always had to use supergrub disk to boot. 


Do you know if there's any way to fix my problem? My motherboard supports booting from a usb device. All my information is pasted above if you need it. Any help is greatly appreiated.

---

### Post by Herman on 2008-01-10
Well, this is seriously contrary to my usual adherance to Stallmanistic   habits, (even if I do have a dual boot website), but since I don't really want to be seen as a cranky old troll today, just for this one occasion, and only because you are insisting here's what to do.

Just re-install whatever boot loader you had in the hard disk to MBR in the hard disk, use FIXMBR if you had Windows XP's bootloader in your internal hard disk,  there are lots of way listed on this page: [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm") .

Now, if you want to install the USB's GRUB to the USB's MBR, (and you might as well do the boot sector too while you're at it, just to be extra sure, you can look at [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") and [How to add GRUB to your USB thumb drive]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.") and [How to Make your Super Grub USB Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk") .

Now, don't go telling anyone else I told you, okay?
(Keep it quiet).

Regards, Herman :)

---

### Post by rrcs on 2008-01-10
I get the same error message - I have made a screenshot (including results of fdisk -lu and dumpe 2fs, etc.) - [http://www.sendspace.com/file/8iwkjl](http://www.sendspace.com/file/8iwkjl)

I have a working laptop, so it is not the end of the world if this cannot work.

---

### Post by Herman on 2008-01-10
You're sure this was an ext3 file system, not reiserfs or something else? :)

---

### Post by rrcs on 2008-01-10
> **Herman said:**
> You're sure this was an ext3 file system, not reiserfs or something else? :)
I'm sorry, I have no clue (I'm not at all computer-savvy on this level of things) :confused:

---

### Post by Herman on 2008-01-10
Hmmm, well I guess we can presume it was an ext3 file system, because that's the default for Ubuntu.
I haven't seen or heard of anything like this before, *all *the superblocks gone apparently. :confused: Hmmm.

Is the rest of your data on this hard disc backed up?

I think the next step should be to run smartmontools on it or sudo badblocks see how the rest of your hard disk is.
You're not having any problems with any other operating systems in this hard disk eh? 

Probably the quickest and simplest would be just to run 'sudo badblocks', form the Ubuntu Live CD again,
```
sudo badblocks -n -v /dev/sda3 
```You'll need to wait a while for that to finish. Hopefully you'll get no output. It'll make you hard drive light come on for quite a long time. It it starts printing out lists of numbers then something's wrong with the surface of your hard drive. If nothing much happens and your ubuntu@ubuntu :~$ prompt is returned then you hard disk has passed. :)
EDIT: It'll say 'Testing with random pattern: Pass completed, 0 bad blocks found.'

Another way test your hard disk is to install smartmontools in the Ubuntu live CD. You run smartctl as illustrated in my Knoppix Page, here, [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With"). 
Smartmontools is in Knoppix and also System Rescue CD. If you already have one of those CDs you can use one of them instead. Otherwise it only takes a few minutes to install smartmontools in your Ubuntu Live CD but it will only remain for the duration of one session, when you reboot it will disappear.
Smartmontools can tell you (if your hard disk supports S.M.A.R.T.), just about everything you want to know about your hard drive, not only the disc surface.
To install smartmontools in the Live CD, you just do this,
```
sudo apt-get install smartmontools
```When it's installed, you can start going through some of the commands on that Knoppix Page, like,
> sudo smartctl -H /dev/sdaI could just advise you to re-install, it will only take you half an hour to re-install.
However, for the sake of the your other data, I think you should run some tests on your hard drive sometime soon. 

Of course, it's entirely up to you, you can just re-install and hope everything will be fine.
I don't want to waste your time. But I want to try to help you  in the most responsible way. In the end, it's up to you.

If there was any important data we'd look at TestDisk and PhotoRec, but as you said it's a new install and you can have the emails resent, then it's probably not worth bothering with.
Thanks for your patience so far.

Regards, Herman :)

---

### Post by rrcs on 2008-01-10
>Thanks for your patience so far.
I do believe that is my line :) !

Yup, long list of numbers being returned (it is not even done yet). I am going to assume it means the harddrive is defective beyond help (worth spending time or money on, at any rate).

Thank you so much for all your time and help, though, I really appreciate it! The instructions on both your site and here have been clear and easy to follow, even for me :) !

---

### Post by indianballer24 on 2008-01-10
Thanks for the reply herman. I tried to understand your guide but I could not figure out what to do. If you have time, could you tell me what to do for problem by telling me what commands to put into the terminal.

---

### Post by Herman on 2008-01-10
Hello rrcs,> Yup, long list of numbers being returned (it is not even done yet). I am going to assume it means the harddrive is defective beyond help (worth spending time or money on, at any rate).:( Okay, wow, you should rescue all your data from that hard drive and replace the hard drive I think.
Hard drives are not very expensive these days and your data can be worth a lot. It's not worth it to waste your time with a hard drive that's not 100%.
All hard drives, even brand new ones, have a few bad blocks, and a few more do appear over the life of the drive. (Kind of like potholes in a road). The new hard drive has comes with a percentage of extra surface that's  held in reserve, and normally, the hard drive silently 'hides' and bad sectors by swapping them out electronically, so the user doesn't need to deal with any issues at all. When these bad blocks do start to show up like this, it's because the reserve area is already used up, the drive can no longer hide it's faults. So your hard drive probably hasn't got very much life expectancy left. 
Definitely back up all your information and start shopping for a new hard drive.
> Thank you so much for all your time and help, though, I really appreciate it! The instructions on both your site and here have been clear and easy to follow, even for me :) !No problems and thank you, it is when I am able to work with people like you that I am able to keep coming up with ideas to improve the site. Sometimes people let me know if there's something I haven't bothered to explain well enough and I'm able to correct it or keep it up to date, so it is better for the next time.
It's always a pleasure when people like yourself take the time to type back some feedback to me, so I know if I was on the right track or not. By sticking with me rather than getting impatient and leaving, you helped me at the same time, so thank you again.
Enjoy your Ubuntu when you get it up and running again! :)

Regards, Herman :)

---

### Post by Onderhil on 2008-01-10
Yet another way of running into Grub error 17.

I have an Open  Question #21827 on Launchpad, asked on 2008-01-09, titled "Triple boot XP Ubuntu and Kubuntu on USB-HD" but this thread seems livelier and more to the point.

For some three weeks I have a new Iomega 500 GB USB-HD (/dev/sda) for back-up purposes. On my desktop I have XP and Ubuntu as a fully functional dual-boot system (/dev/hda and /dev/hdb).

I added Kubuntu at the back of the 500 G - as I didn't like the way Ubuntu and Kubuntu mess up each other and I wanted to try out the AMD 64 bit system (I know I shouldn´t install a system on an USB-HD, but I think I'll  use it only for half an hour or so for some time, as in the meantime I'm using Ubuntu as my Linux distro).

A straight install of Kubuntu 7.10 on the USB-HD worked, and booting from the 500 G with /grub/menu.lst from the Kubuntu installation worked too - after setting the prios right in BIOS.

My /boot/grub/device.map (from the Kubuntu-install) shows (edited):

```

(hd0) /dev/hda --> WinXP and Some Data
(hd1) /dev/hdb --> Data and Ubuntu
(hd2) /dev/sda --> Even more Data and Kubuntu

```

But I didn't want to do that: the USB-HD might not be present. 
When the USB-HD is attached, I want to be able to select a Kubuntu system, so I edited /boot/grub/menu.lst from the Ubuntu 7.10 install on the desktop HD (on /dev/hdb), incorporating the lines from Kubuntu-menu.lst as I thought fit.

Selecting Kubuntu with the USB-HD present grub complains with Error 17: Cannot mount partition.


----- menu.lst with comments edited out ------:

```

default 4
timeout 40
color cyan/blue yellow/blue

### BEGIN AUTOMAGIC KERNELS LIST
# kopt=root=UUID=98e85ac8-9e9f-4caf-b683-ac473c59745d ro
# crashdump=0
# groot=(hd1,4)
# alternative=true
# lockalternative=false
# defoptions=quiet splash vga=791
# lockold=false
# xenhopt=
# xenkopt=console=tty0
# altoptions=(recovery mode) single
# howmany=all
# memtest86=true
# updatedefaultentry=false
# savedefault=false
## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,4)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=98e85ac8-9e9f-4caf-b683-ac473c59745d ro quiet splash vga=791
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=98e85ac8-9e9f-4caf-b683-ac473c59745d ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd1,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

## ## Start Kubuntu Default Options ##

# These entries automatically added by the Debian installer for an existing linux installation
title Kubuntu 7.10, kernel 2.6.22-14-generic AMD64
root (hd2,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c7b43bf6-3c8e-4aed-ab72-939fd682d928 rootdelay=10 ro quiet splash vga=791
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing linux installation
title Kubuntu 7.10, kernel 2.6.22-14-generic AMD64 (recovery mode)
root (hd2,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c7b43bf6-3c8e-4aed-ab72-939fd682d928 rootdelay=10 ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing linux installation on /dev/sda2.
title Kubuntu 7.10, memtest86+ AMD64
root (hd2,1)
kernel /boot/memtest86+.bin
savedefault
boot

```

All triple boot solutions I have seen so far deal with XP and Vista and Ubuntu, or Mac and XP and Ubuntu (or any other Linux variety), but none with USB as auxiliary drive. Some say to include rootdelay=10 to give the system time to see the USB, but no - nothing but error 17.

Jim Hutchinson suggested yesterday on Launchpad: 

> 
The Kubuntu root (hd2,1) line is probably wrong. The BIOS seems to change drive names depending on what's connected. Try changing that line to

root (hd1,1)

or

root (hd0,1)

and see what happens. I actually just did a little how to on this. Slightly different from your situation but may offer some help. I consider it a beta how to as it needs some testing but may be useful. [http://ubuntukids.org/blog/?p=69](http://ubuntukids.org/blog/?p=69)


but alas, both suggestions (edited on the fly) yielded error 17. I think (hd2,1) should be OK.

So perhaps, (another suggestion I came across) do I have to edit the modules file to make sure USB support is added/loaded during Ubuntu startup (as suggested in [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)) ???

Here is the output of the fdisk:

```

moem@Jabberwock:~$ fdisk -lu
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4c2127f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   958341509   479170723+   7  HPFS/NTFS
/dev/sda2       958341510   976768064     9213277+   6  FAT16

moem@Jabberwock:~$ fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4c2127f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       59654   479170723+   7  HPFS/NTFS
/dev/sda2           59655       60801     9213277+   6  FAT16

moem@Jabberwock:~$ sudo vol_id -u /dev/sda2
[sudo] password for moem:
c7b43bf6-3c8e-4aed-ab72-939fd682d928

moem@Jabberwock:~$ sudo fdisk -lu /dev/hdb

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ef84f84

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    40981814    20490876    5  Extended
/dev/hdb2        40981815   276494714   117756450    7  HPFS/NTFS
/dev/hdb3       276494715   488392064   105948675    7  HPFS/NTFS
/dev/hdb5             126    23005079    11502477   83  Linux
/dev/hdb6        23005143    33527654     5261256   83  Linux
/dev/hdb7        33527718    38989754     2731018+  83  Linux
/dev/hdb8        38989818    40981814      995998+  82  Linux swap / Solaris
moem@Jabberwock:~$ sudo fdisk -lu /dev/hda

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe7cfe7cf

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   155637719    77818828+   7  HPFS/NTFS
/dev/hda2       155637720   312576704    78469492+   f  W95 Ext'd (LBA)
/dev/hda5       155637783   307194929    75778573+   7  HPFS/NTFS
/dev/hda6       307194993   312576704     2690856    b  W95 FAT32

```

What did I do wrong?
Can someone point me in the right direction?
Thanks 
Mark

---

### Post by Herman on 2008-01-10
The best way is to install you USB's GRUB to the MBR in the USB disk and write a chainloader command to boot the USB MBR from your internal hard disk's GRUB.

All the information has been already well written out already and well explained in the link already given. 

You can also use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). - GRUB is almost a miniature operating system in it's own right.
Try booting it up from the command line a few times and you'll easily be able to find out that way what details you need to put in your menu.lst.

When dual booting Linux installations you shouldn't really use direct specific kernel commands otherwise you need to manuallty update your menu.lst each time there's a kernel update. It's better to boot the other Linux's GRUB with a  chainloader comamnd or a configfile command.

In other words, to be more specific for Onderhil, you would probably just use:
```
root (hd2)
chainloader +1
```And that would be all you need to boot the MBR of your USB disk when it has been plugged in prior to boot-up. (So the BIOS has detected it.)

indianballer24, you need to install GRUB to the MBR in your hard disk too, but you'll have to boot from your BIOS, here's how I do it, [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).

---

### Post by Herman on 2008-01-10
indianballer24, try this, 
```
sudo grub
```
```
root (hd1,1)
```
```
setup (hd1,1)
```
```
setup (hd1)
```
```
quit
```

---

### Post by Herman on 2008-01-10
Onderhil,
I can't predict anything with yours, you'll need to use GRUB's Command Lini Interface, here's how, if you get a [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). first and then follow the instructions in this link,  [**Chainloader Boot**]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot"), you'll be able to get your Kubuntu GRUB installed to MBR in your USB disk.

Then delete all those direct kernel boot entries for Kubuntu in the bottom of your Ubuntu' menu.lst.
Replace them with a chainloader entry to boot the USB's MBR. 
When Ubuntu's GRUB chainlaod's the USB's MBR it will hand over control to your Kubuntu's GRUB and you Kubuntu menu will come uo and boot Kubuntu.
You can set the timer down to have a shorter countdown before it boots if you like.
Kubuntu's menu.lst is probably already correct for Kubuntu, and Kubuntu will update it's own menu automagically when it has a kernel update. 

Regards, Herman

---

### Post by Onderhil on 2008-01-14
Dear Herman,
Sorry for the late response, but the weekend interfered. Everything worked, though it took me some time to discover that I really had to use ```
root (hd2)
``` as you suggested, instead of```
 root (hd2,1)
``` as I thought: the MBR was written to the disk and not to the partition by Kubuntu (through "Advanced" --> /dev/sda). 

Everything is now as I want it to be. I suppose that I can use the same trick  in the menu.lst that Kubuntu constructed to get back to Ubuntu: ```
root (hd1,4)
chainloader +1
boot
``` in order to get rid of the Ubuntu-kernel specific entries in the Kubuntu menu.lst.
(Regarding the timer: I tend to walk away when (re)starting, thus giving me time to interfere when I get back)
Once more thanks,
Regards, Mark

---

### Post by indianballer24 on 2008-01-14
> **Herman said:**
> indianballer24, try this, 
```
sudo grub
```
```
root (hd1,1)
```
```
setup (hd1,1)
```
```
setup (hd1)
```
```
quit
```

Thank you for that advice herman, but it did not work. I still get the same error. Am I supposed to run these commands from the live cd? Once again, thank you for your help.

---

### Post by Herman on 2008-01-14
>  My device.map says the following:

(hd0)    /dev/sda
(hd1)    /dev/sdb

sudo fdisk -l says the following

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6c8c6c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         766     6144862+   5  Extended
/dev/sda2   *         767        9729    71995297+   7  HPFS/NTFS
/dev/sda5               2         766     6144831    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9585    76991481    7  HPFS/NTFS
/dev/sdb2   *        9586       19083    76292685   83  Linux
/dev/sdb3           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris:)
Hello indianballer24,
I'm sorry if that didn't work, it should have worked if the information you provided in an earlier post is still correct. Possibly something has changed, maybe it depends on whether the USB was already plugged in prior to boot-up, or if it was plugged in sometime later, whether the internal hard drive will be registered in the BIOS as the first hard drive or the USB will. Most of the itme it would make sense that the first hard drive should be number1  hard drive (hd0), and the USB will be number2 (hd1).

Try doing the same thing I suggested for Onderhil then, and follow my how-to and learn how to work with GRUB at the command line, here is the link again, [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). 
I have been doing some work on that article, and I am trying to make it as easy for people to understand as possible, but still make it so anybody can do anything with it.
Please let me know if you have any trouble. 
It might not work as well in all computers. Not all computers can boot a USB drive either.
If you read the link I just gave you and try our the tricks I showed you there and then do this part, [**Chainloader Boot**]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot"), your USB should have GRUB installed in it's MBR and it should boot for you.

You can get GRUB's Command Line Interface from anything that has GRUB in it, If you have [Super Grub Disk]("http://sgd.benjamin-butschko.de/") you can always get GRUB's Command Line Interface. 
Actually, adrian15 has added a new feature to Super Grub Disk that you might find handy, it's called 'swap hard drives and boot', useful for people booting a USB drive.

Regards, Herman :)

---

### Post by indianballer24 on 2008-01-14
Herman, here is some background on my problem. I have ubuntu installed on an external hard drive. sdb1 is a fat32 partition I use for storage. sdb2 is an ext3 partition where ubuntu is installed. sdb3 is and extended partition and sdb5 is the linux-swap partition. Attached is a screenshot of my partition editor screenshots.

 I am on my linux system on the external hard drive right now. If I use the super grub cd to boot into my external hard drive it works fine but I cannot boot from the external hard drive without it. I want to be able to boot from the hard drive without having to put in the super grub cd every time. I have tried to install grub to my external hard drive's mbr using the super grub cd but it has not worked. I still continue to get error 17. I am sure my motherboard supports booting from a usb device. I tried doing what you told Onederhill but it did not work. My usb hard drive has been connected since boot. Do I have to run the commands that you gave me from a live cd or the ubuntu installed on my external harddrive?  If you need any more information just tell me. Thank you so much for your help so far with this issue. 

**[SIZE="5"]Here is my menu.lst file[/SIZE]**

(hd0)	/dev/sda
(hd1)	/dev/sdb


**[SIZE="5"]Here is the output of fdisk -l[/SIZE]**

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9585    76991481    b  W95 FAT32
/dev/sdb2   *        9586       19083    76292685   83  Linux
/dev/sdb3           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris


**[SIZE="5"]Here is a copy of my device.map file[/SIZE]**

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c3a2e28c-3618-42ec-bc7b-b34e39d94051 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3a2e28c-3618-42ec-bc7b-b34e39d94051 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3a2e28c-3618-42ec-bc7b-b34e39d94051 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

---

### Post by Herman on 2008-01-14
Well what I have told you is already correct. I don't know what more I can do.
Regards, Herman :)

---

### Post by indianballer24 on 2008-01-14
Well, thanks for your help.  One last question, were those commands you gave me supposed to be run from the live cd or on my ubuntu installation on my external hard drive?

---

### Post by Herman on 2008-01-15
> One last question, were those commands you gave me supposed to be run from the live cd or on my ubuntu installation on my external hard drive? It shouldn't make any difference at all. GRUB can be used from any drive to install any other GRUB to any other drive.

Are you sure you have your BIOS set up properly for booting your USB drive?

Are you using your F8 or F12 keys when you try to boot up, for a list of bootable drives?

Regards, Herman

---

### Post by indianballer24 on 2008-01-15
yes, its the F10 key on my computer. I guess ill just stick to using the super grub cd to boot. Thanks for your help.

---

### Post by DeepSix on 2008-01-30
I received this error after I deleted two blank partitions using Vista's disk management. By blank I mean they had no title, no letters, nothing of that sort. Both were given total space and space available, both were at 100%. To explain away some of the stupidity with my choices, I recently got a new hard drive and thought perhaps that those two blanks were the reason why it not was showing up in the management screen.

Anyway I think its safe to assume those deletions effected grub and perhaps/probably Ubuntu itself. Is this situation salvageable or am I looking at reinstalling ubuntu?

---

### Post by Herman on 2008-01-30
Hello DeepSix,
Can you boot the Ubuntu live CD and post the output from 'sudo fdisk -lu' here please? ```
sudo fdisk -lu
``` You might also take a look at it with GParted Partition Editor in the Ubuntu Live CD or in the standalone GParted LiveCD if you have one of those. 
How much data did you have an how important is it to you? If you didn't have any important data then it might not matter if you just re-install. If you have put a lot of work into setting up your system(s), or/or have some project in there that you have invested a lot of time into and isn't backed up somewhere recently then it might be worth some work to try to recover everything or at least some of it. Sometimes it only takes one or two commands, other times it can be quite a long and comlplicated process to get things working again, it depends on exactly what's wrong.

Regards, Herman :)

---

### Post by DeepSix on 2008-01-31
results of sudo fdisk -lu:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x079bcd93

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    66043214    33021576    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ce0db70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xafcbc485

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    36255806    18127872    7  HPFS/NTFS
/dev/sdb2        70686000    72292499      803250    5  Extended

What am I supposed to do in GParted Partition Editor? About my data, well I'd prefer not to have to re-install.

---

### Post by Therion on 2008-01-31
Just thought I'd post up my own experience with GRUB Error 17 in case it helps someone else.  

I run a dual hard-drive system with mixed-drives (one SATA [Master], one PATA [Slave]).  As I assume most anyone with this setup probably realizes, having mixed drives can be troublesome; mainly because the BIOS (I have Phoenix BIOS) wants to give boot priority to the IDE/PATA hard drive.  

During last my last install of Ubunutu, I left both drives physically connected while I did the reformat and reinstall on the SATA drive.  Upon booting from the hard drive I got the dreaded GRUB Error 17.

**Solution Part I:**  I shut down the PC and disconnected the secondary (IDE) hard drive (meaning I physically removed the power cable from the back of the drive), boot up, and reinstalled Ubuntu from the ground up.  I suppose I could have gone through and manually changed the required settings to straighten out GRUB, but seriously, Ubuntu takes so little time to install and I like the idea of GRUB installing *correctly* right from the get go; so this is the route I decided on.  So the reinstall goes off without a hitch and now I'm running Ubuntu just peachy, but using the SATA drive only at this point, since slave-drive's power cable is still disconnected.  Time to fix that...

**Solution Part II:**  I shut down the PC, reconnected the power cable to the slave-drive, rebooted and went straight into the BIOS settings.  As I have discovered, mainly through trial and error, my Phoenix BIOS wants to boot from any IDE drive it finds on my system by default and will make it the primary boot device if left to its own devices.  IDE drives, it seem, takes precedence in the BIOS over SATA drives no matter what, and now that the IDE (PATA) drive is reconnected to it's power source, the BIOS wants to boot from it. Obviously this is no good, since I have Ubuntu installed on the SATA drive.

I have to change **two** things in my (Phoenix) BIOS, both under the "Boot" option to make this happen.  Step 1 is to make sure both drives are being recognized and too assign the SATA drive as Drive 1 and the IDE/PATA drive as Drive 2.  This is a critical step that's easy to miss in my opinion.  Step 2 is to change the boot *sequence* of the hard drives so that the SATA drive is the second device in the boot sequence -- right after the CD/DVD drive.  F10 to Save the changes, exit the BIOS and continue booting.   *voila!*... Problem solved.  

Hopefully this will save someone else a little trouble and heartache.  GRUB errors kinda freak me out, personally.

---

### Post by Herman on 2008-01-31
Hello DeepSix,
I can see that you have three hard disks, the first is a 40 GB PATA disk with an NTFS partition, and  two of them are SATA type hard disks, 160 GB and 37 GB.

I am only guessing, but it looks like probably you deleted your Ubuntu partition and swap area from disk 3, your second SATA disk, would that be right?

The good news is, it looks like your partition tables are still okay, at least as far as I can tell.
You should be able to run 'Parted, (the command line version of 'Parted), and recover the partitions you deleted,  this page tells you how,  [COLOR=#c0c0c0][COLOR=black] [DataRecovery]("https://help.ubuntu.com/community/DataRecovery")[/COLOR][/COLOR]
Here is a link to the Parted Manual in case you want it, [Parted User's Manual]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.gnu.org%2Fsoftware%2Fparted%2Fmanual%2Fhtml_mono%2Fparted.html&ei=kBWiR6jqO6CqpwTKvODRBA&usg=AFQjCNFF1cLDH65uEmm6wzXfAJHav_e1GA&sig2=yLUDLoZqT257jV0fuJBlmg")
Parted is in the Ubuntu Live CD and almost any Linux Live CD.

You can also recover them with TestDisk, here is a link that should help you with that, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html"). It contains a couple of examples (demonstrations) of how to use TestDisk to recover lost partitions.
You will be able to install TestDisk in the Ubuntu LiveCD and it will be able to be used as long as the LiveCD is booted, use the command 'sudo apt-get install testdisk'. Or install TestDisk with Synaptic Package Manager.
TestDisk is also featured in [System Rescue CD]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.sysresccd.org%2F&ei=-xaiR46VN4mypgTnpLXiBA&usg=AFQjCNHLezgCI1IM3RH_amPHKhYtEeiaEQ&sig2=vCtDr1-38tFD2C26dxZrYA") and [Knoppix ]("http://www.knoppix.net/")CDs and other good rescue CDs.

Either of those two methods should work, maybe the Parted method will be simpler. Try whichever way seems the easiest for you.

Regards, Herman :)

---

### Post by DeepSix on 2008-02-01
Thanks Herman. TestDisk did it for me.

However an hour or so after I fixed it, I physically broke the drive. So I'm thinking maybe this drive really didn't like me this week. :(

---

### Post by Herman on 2008-02-01
"*First the good news and then the bad news*" eh? 

Thanks for the feedback, it's always nice to hear back when something works for people and that helps me decide what to recommend for others in the future too sometimes.
I'm sorry to read your disk ended up with physical damage somehow though. Sometimes I have days like that too.
Regards, Herman :)

---

### Post by toucansam99 on 2008-02-06
I do not have more than one hard drive, but I am getting the grub 17 error everywhere.

it started when I installed by booting from a flash drive ( i always got io error when i tried cds or dvds).  The flash drive boot worked after some screwing around with the bios (i had to detect it is a floppy).

I made two partitions, sda1 is swap, and sda2 is the root mount.  It installed (thankfully) and i rebooted.

grub error 17.

ok so i try booting from the usb again

grub error 17

damn ok now the cd

grub error 17

i turn everything off.  stormed around for a sec.  then came back.  booted from cd

it worked!!!

so I'm following your tutorial, and I realize that I only have one hard drive so i shouldn't have a problem.  hd0 points to sda1.  in the menu.lst file it pointed to (hd0,1) which was right cause it's the second partition (i think thats what the 1 meant).  so i reboot with the hd.

grub error 17

ok restart and reboot from the cd

grub error 17

flash drive?

grub error 17

so whenever i boot and get the grub error 17, i have to totally shut down before it can boot anything else.  This is frustrating.  please help me.

---

### Post by Herman on 2008-02-07
Post deleted.

---

### Post by toucansam99 on 2008-02-07
um sorry i got carried away.  edited.

---

### Post by Herman on 2008-02-07
:) Hello toucansam99,
I think the easiest way for you to solve your problem would be to use [GRUB's Command Line Interface.]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
If you get a GRUB menu you just press your 'c' key from any GRUB menu to go into command line GRUB.
Command line GRUB is useful because it's interactive, (well for most BIOSes it is).
If you don't see a GRUB menu from your hard disk installation or from your flash memory stick then it might be necessary to download a copy of the latest [Super Grub Disk]("http://sgd.benjamin-butschko.de/"), which is free and only a small download and is probably something every Linux user should have anyway. Super Grub Disk is available for CDs, USBs or for floppy disks. 
It doesn't matter where you get a GRUB Command Line Interface from, as long as you get one somehow. Since you said you had I/O errors with the CD drive, I'll presume for example that you are able to get a GRUB CLI from your memory stick.

Now, the confusion comes about when there is a USB flash memory device plugged in during the Ubuntu installation because that is detected by your BIOS as another hard drive, and not only that, but to make matters even worse, it may have been temporarily seen as hard drive number 1 by your BIOS, which has confused your GRUB set up and installation.

To solve this problem we just need to re-install GRUB and fix your /boot/grub/menu.lst file.

It's possible to install GRUB from any device to any other device. I mean you can install your hard disk's grub to your USB stick or your USB stick's GRUB to your hard drive. 

What we want to do is make sure you install your hard drive's GRUB to your hard drive.

From the grub >_ prompt, enter the following command,
```
find /boot/grub/stage1
``` You might get the answer back '(hd0,1)', but if you are using your flash memory stick for the GRUB Command Line Interface, maybe you'll get two answers, (hd0,0) and (hd1,1) or maybe something a little different even.

If you get more than one answer, we need to decide which one is the hard disk's GRUB, so we use the 'geometry' command.
You do something like this,
```
geometry (hd0)
```Feedback from that command should give you some clues about which disk your BIOS thinks is (hd0).

Now try running the geometry command on whichever other disk you had a /boot/grub/stage1 file in,
```
geometry (hd1)
```Feedback from that command should give you some clues about which disk your BIOS thinks is (hd1).

You should be able to judge by the size reported for the two disks and the partition details which is your hard disk and which is your  flash memory stick.

In one of my computers the hard drive is shown as (hd0) and I have a flash memory stick detected as (hd1), but I presume yours will be the opposite, since you are having this problem.
Let's say your hard disk will be (hd1) for the purposes of this exercise, and Ubuntu in your hard disk is in (hd1,1).
You 'root' GRUB to  (hd1,1).
```
root (hd1,1)
```Where: (hd1,1) is your Ubuntu / (root) partition, please replace the numbers with whatever is appropriate for your particular set-up, which should be apparent from the feedback from the commands above.

Now we're going to install your hard drive's GRUB to MBR in your hard drive,  we use the 'setup' command for that, and we want to set up GRUB to the same device, (your hard disk),
```
setup (hd1)
```Where: (hd1) is your hard disk, please replace the numbers with whatever is appropriate for your particular set-up, which should be apparent from the feedback from the commands above.

By now I hope we're certain we have your hard drive's GRUB installed to your hard drive's MBR and not the flash memory stick,  or vice versa.

to be continued...

---

### Post by Herman on 2008-02-07
... continued

Now if your only problem was that GRUB was installed to the wrong MBR, of the wrong GRUB was installed to MBR, you might be able simply boot okay now.
Try rebooting with the USB flash memory stick removed and see what happens.

If you can boot okay now then you're finished.

If you still can't boot the normal way then you might need to use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") once again and do a [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").
I hope it will be explained well enough in that link. If you have any trouble, please ask me and I'll elaborate.
You should be able to boot your hard disk's installed Ubuntu that way regardless of whether you have any problems in your Master Boot Record  (which I think we fixed earlier), or any problems in your /boot/grub/menu.lst file.

Once you have booted, open your /boot/grub/menu.lst file,
```
gksudo /boot/grub/menu.lst
```Edit your /boot/grub/menu.lst file to make sure your boot entries for Ubuntu are set for (hd0,1), something like in the example portion of menu.lst file shown below.
If you needed to make changes, don't forget to also make the same changes to your 'groot' line, so that the changes you made will remain persistent over a kernel update.
If you don't, you'll get GRUB error 17 back again at the next kernel update and you need to do this all over again.
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=[COLOR=Sienna]**(hd0,1)**[/COLOR]

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root      [COLOR=Sienna]**  (hd0,1)**[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        [COLOR=Sienna]**(hd0,1)**[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root      [COLOR=Sienna]**  (hd0,1)**[/COLOR]
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```I hope that will have all your problems sorted out by now, but if you still have trouble or if there's anything you're not sure about then please ask me and I'll give you more help as necessary.

Regards, Herman :)

---

### Post by toucansam99 on 2008-02-07
ok so here's how it went

downloaded the super grub cd

booted from it, and got a plethora of choices to do things (i love that word)

I kept choosing what made sense, then decided to just hit 'c' like you said.

ran the commands, it was on hd0 partition 1.  I rebooted and it said it couldn't find the disk, so I pressed 'c' and 'cat /boot/grub/menu.lst' and found that groot = (hd1,1) so i rebooted and pressed 'e' this time and changed root to hd0, booted.

then it worked (!!!) and i changed the menu.lst file to say hd0 instead of hd1.  (originally tried with the text editor but it needed to be authenticated to save it, so i just used vim.

Thanks a lot, me and all the little children around me ;) thank you dearly.

---

### Post by Herman on 2008-02-07
:) Okaaay! 
Thanks for the feedback and I'm glad you got it working! Well done!
Regards, Herman :)

---

### Post by rahul_bhise on 2008-02-08
please help Herman
i have one hard disk of 80gb. on which booth window xp (with 4 partition c: d: e: f:) and ubuntu 7.10 (with separate /home partition and swap partition )are there 
i deleted e: partition and joined it to d: partition. since then at start up i get error 
grub loading stage 1.5.
grub loading, please wait
error 17
now i am on live cd ubuntu 7.04

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/sda2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2434        4879    19647463+   b  W95 FAT32
/dev/sda6            7300        9729    19518943+   b  W95 FAT32
/dev/sda7   *        6083        7241     9309636   83  Linux
/dev/sda8            7242        7299      465853+  82  Linux swap / Solaris
/dev/sda9            4880        6082     9663066   83  Linux
```



```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by rahul_bhise on 2008-02-08
my screen shot of gparted

---

### Post by Herman on 2008-02-08
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,[COLOR=Sienna]**6**[/COLOR])

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,[COLOR=Sienna]**6**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,[COLOR=Sienna]**6**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd0,[COLOR=Sienna]**6**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,[COLOR=Sienna]**6**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,**[COLOR=Sienna]6[/COLOR]**)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```:) Hello rahul_bhise,
I think you just need to change your partition number in your boot entries from (hd0,7) to (hd0,6), if your /dev/sda7 is your Ubuntu root partition.

Also , you have more than one boot flag, you should get rid of one of those using a partition editor such as GParted.

Regards, Herman :)

---

### Post by rahul_bhise on 2008-02-09
i did change the partition number as you said but still have the same problem. and dev/sda7 is my ubuntus /root


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/sda2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2434        4879    19647463+   b  W95 FAT32
/dev/sda6            7300        9729    19518943+   b  W95 FAT32
/dev/sda7   *        6083        7241     9309636   83  Linux
/dev/sda8            7242        7299      465853+  82  Linux swap / Solaris
/dev/sda9            4880        6082     9663066   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
```

i will see if removinf the flag from /dev/sda7

```

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2aabd8fd-57bd-4a71-8239-5a0d78ee3ac0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Herman on 2008-02-09
That should have worked.

You mentioned having done some work on your partitions just before the error started and obviously whatever partitioning program you used has changed your partition numbers.
Maybe you should do a file system check now and see if that helps, [                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")
GRUB error 17 has been solved in some cases in the past by running a file system check so that might work, and it won't hurt. It's always good to run a file system check.

Regards, Herman :)

---

### Post by rahul_bhise on 2008-02-09
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda7
                                                                               
  172790 inodes used (14.82%)
    4018 non-contiguous inodes (2.3%)
         # of inodes with ind/dind/tind blocks: 7819/88/0
 1024047 blocks used (44.00%)
       0 bad blocks
       1 large file

  134605 regular files
   18494 directories
     133 character device files
      26 block device files
       2 fifos
     509 links
   19517 symbolic links (18001 fast symbolic links)
       4 sockets
--------
  173290 files
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda9
                                                                               
   39593 inodes used (3.27%)
    1133 non-contiguous inodes (2.9%)
         # of inodes with ind/dind/tind blocks: 3087/56/0
  704108 blocks used (29.15%)
       0 bad blocks
       1 large file

   36963 regular files
    2546 directories
       0 character device files
       0 block device files
      22 fifos
       0 links
      53 symbolic links (53 fast symbolic links)
       0 sockets
--------
   39584 files
ubuntu@ubuntu:~$ sudo e2fsck -y -f -v /dev/sda7
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  172790 inodes used (14.82%)
    4018 non-contiguous inodes (2.3%)
         # of inodes with ind/dind/tind blocks: 7819/88/0
 1024047 blocks used (44.00%)
       0 bad blocks
       1 large file

  134605 regular files
   18494 directories
     133 character device files
      26 block device files
       2 fifos
     509 links
   19517 symbolic links (18001 fast symbolic links)
       4 sockets
--------
  173290 files
ubuntu@ubuntu:~$ sudo e2fsck -y -f -v /dev/sda9
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   39593 inodes used (3.27%)
    1133 non-contiguous inodes (2.9%)
         # of inodes with ind/dind/tind blocks: 3087/56/0
  704108 blocks used (29.15%)
       0 bad blocks
       1 large file

   36963 regular files
    2546 directories
       0 character device files
       0 block device files
      22 fifos
       0 links
      53 symbolic links (53 fast symbolic links)
       0 sockets
--------
   39584 files
ubuntu@ubuntu:~$
``` 
 

now i am restarting

---

### Post by rahul_bhise on 2008-02-09
the problem is still not solved now what next should i do

---

### Post by Herman on 2008-02-09
Since your partition number has been changed, probably you need to re-install GRUB.

If you have a [Super Grub Disk]("http://sgd.benjamin-butschko.de/") you can use that to re-install GRUB, that's the quickest and easiest way.  
1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3. Gnu/Linux
   4. Fix Boot of Gnu/Linux (GRUB)
   5. select your Linux partition
   6. see message, 'SGD has succeeded'
   7. you're done! reboot

If you have the Ubuntu Live CD you can also re-install GRUB easily by opening a terminal in the Ubuntu Live CD operating system and typing 'sudo grub', for a [GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell").
```
sudo grub
```
When you have a GRUB shell, you type:
```
root (hd0,6)
``````
setup (hd0)
``````
quit
```After that, try again to boot and if you can boot, you may find that booting stops at the file system check with a black screen with white text.
Hopefully you will be able to get past that and continue booting by pressing 'Enter', and then pressing 'Ctrl' +  'd' keys.
Once your system has booted then probably it will be a good idea to open your /etc/fstab file in your hard disk installed Ubuntu operating system and make sure the file system UUID numbers in there are okay.
If the hard disk partitioner that changed your partition number has also changed your file system UUID number, you may need to update /etc/fstab.
Here is how to do that, [                          About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with").

If you can't boot because of the /etc/fstab file system UUID problem, you might need to use your Ubuntu Live CD again and do this, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000] .
Use the method explained in that link to gain access to your hard disk installed Ubuntu /etc/fstab file, and fix your /etc/fstab file and fix your /etc/fstab file as explained in this link, [/COLOR][/COLOR] [                          About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with").

Regards, Herman :)

---

### Post by gard195 on 2008-02-09
i have the same problem. but i cant get into bios.

---

### Post by Herman on 2008-02-09
> i have the same problem. but i cant get into bios.:)  Okay, what's the output from 'sudo fdisk -lu' please?
```
sudo fdisk -lu
```
And also, what does the bottom half of your /boot/grub/menu.lst look like?
```
gksudo gedit /boot/grub/menu.lst
```
You can boot Ubuntu directly to get the above information if you have a [Super Grub Disk]("http://sgd.benjamin-butschko.de/").
Another good way is to use your Ubuntu Live CD to do it, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000].

[/COLOR][/COLOR] Regards, Herman :)

---

### Post by rahul_bhise on 2008-02-09
now i get the grub menu and boot in the windows xp well.
but when i choose the ubuntu option ti goes half way and says
```

the super block could not be read or does not describe a correct ext2 file system.
 if the device is valid and it really contain an ext2 filesystem 
(and not swap or ufs or something else), then the superblock is corrupt, 
and you mite try running e2fsck with an alternate superblock:
e2fck -b 8193 <device>

fsck died with exit status 8

brltty[5173]: mounting usbfs: /etc/brltty/usbfs
*file system check failed
a log is being saved in /var/log/fsck/checkfs if that location is writable.
 please repair the file system manually
*a maintenance shell will now be started.
control-d will terminate this shell and resume system boot.
give root password for system maintenance.
(or type control-d to continue):********
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: dircolors: command not found
bash: the: command not found
root@uhome:~#

```

---

### Post by Herman on 2008-02-10
:) Okay rahul_bhise,
Don't worry, you are almost there, I was worried that might happen, here is what you can do about it,> If you can't boot because of the /etc/fstab file system UUID problem, you might need to use your Ubuntu Live CD again and do this, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000] .
Use the method explained in that link to gain access to your hard disk installed Ubuntu /etc/fstab file, and fix your /etc/fstab file and fix your /etc/fstab file as explained in this link, [/COLOR][/COLOR] [                          About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with"). After you do that your system will boot normally again.

Oh, there is one more thing, I'm not sure, but if you had to do that then you probably will also need to change the UUIDs in your /boot/grub/menu.lst as well. [Operating System Entries]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries"). I am sure you are almost finished and your system will be back to normal very soon.

Regards, Herman :)

---

### Post by Xephyrind on 2008-02-10
> **mbwardle said:**
> I got this error after installing the Ubuntu 7.10 release candidate.

The error usually happens because Linux and your BIOS detect your hard disks in different orders.  GRUB tries to translate between the two using the device.map file in /boot/grub/device.map, which is automatically generated.  Chances are, it guessed wrong.

In my case, I have three SATA hard disks.

My BIOS sees them as:
HDD1 - 80 GB - Windows
HDD2 - 80 GB - Linux
HDD3 - 250 GB - Media

Linux sees them as:
/dev/sda - 80 GB - Windows
/dev/sdb - 250 GB - Media
/dev/sdc - 80 GB - Linux

So it generated device.map assuming that order was correct, i.e.:
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

When the installer installed GRUB using that data, it tried to install the first part of GRUB on /dev/sda and told it to look for the OS on /dev/sdc.  Unfortunately, this translated to "install on (hd0) then look for the OS on (hd2)", so it was looking for the OS on the wrong drive.

To fix it, you have to teach GRUB which order the BIOS uses.  To do this, follow these steps:

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"
8) Edit device.map (using vi or another text editor)

In my case, my new device.map was:
(hd0)    /dev/sda
(hd1)    /dev/sdc
(hd2)    /dev/sdb

which told GRUB that sdc was really the second hard drive, not the third.

9) Run "grub --device.map=device.map"
10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)

You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that.  This is what we want.

12) Edit menu.lst

You need to change references from (hd2,0) to (hd1,0), or whatever your Linux boot drive was autodetected as to whatever it is according to your BIOS.

If you get this step wrong, you'll see an error message something like:
Error 17: Cannot mount selected partition

meaning it's looking for a Linux file system on that partition, but it can't find one (because the drive device number is wrong in menu.lst).

13) Reboot

14) Celebrate or complain in this thread!

MBWARDLE Thanks. I took your suggestion and followed your route with all the crazy linux commands, which a noobie linux dude like me goes lllo_Oa *lost. In short I followed upto opening the file and stuff then I was lost. Nonetheless, I took note in what you said and I decided to do it the other way, which is since I don't know how to play around with grub, I will play with my BIOS. In the end, I swapped the BIOS hard drive list and the GRUB error 17 Magically went away. Oh by the way, I would appreciate it if you could add more details to each step of your operation please? Some steps are a bit overly advanced for a n00b like me. I don't even know what a text editor is and stuff. I even have a hard time finding where my downloaded programs are located in. In short, I am quite interested in understanding how exactly your method works. Hope you will read this message Thanks!~

Best Regards~

---

### Post by rahul_bhise on 2008-02-11
it took too long as i was being very caution as nothing should go wrong.
i first red everything you told me [hea]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")r and [hear ]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")
but all went ok now i could login to windows xp and ubuntu as well 
about editing grubs menu.lst you already told me[ hear]("http://ubuntuforums.org/showpost.php?p=4294620&postcount=177")
you have a really good information at bigpond.net which i am going to read from start to end afterwards.
and one more thing should i reconfigure my xserver asyou said in your website.
also how to remove this extra boot flag. i did tried in gpardit right clickinf and then manage flag and unselicted on boot but it again appears after a restart
```
brahul@uhome:~$ sudo fdisk -l
[sudo] password for brahul:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ab40ab3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/sda2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2434        4879    19647463+   b  W95 FAT32
/dev/sda6            7300        9729    19518943+   b  W95 FAT32
/dev/sda7   *        6083        7241     9309636   83  Linux
/dev/sda8            7242        7299      465853+  82  Linux swap / Solaris
/dev/sda9            4880        6082     9663066   83  Linux

Partition table entries are not in disk order
```

---

### Post by Herman on 2008-02-11
:) Hello rahul_bhise,
> all went ok now i could login to windows xp and ubuntu as well Good!
>  you have a really good information at bigpond.netThank you.
>  and one more thing should i reconfigure my xserver asyou said in your website No, if your computer is working okay you should not need to do that.  Some people get a black screen after they install a new system because they have some kind of special new hardware such as a very big monitor or something that Ubuntu has trouble setting itself up for automatically. Or if you want to remove your hard drive and put it in a different computer and boot with a different monitor and keyboard and mouse and so on.
> also how to remove this extra boot flag. i did tried in gpardit right clickinf and then manage flag and unselicted on boot but it again appears after a restart Normally that should work. Maybe try removing both of the boot flags then and see what happens. Linux doesn't need the boot flag. GRUB will make you a new boot flag for Windows with it's 'makeactive' command when you boot Windows.
Regards, Herman :)

---

### Post by spookman on 2008-02-22
I hope some one can help me,

I have 3 HDD

Under windows

Disk 0 = MEDIA
Disk 1 = WIndows
Disk 2 = Linux

Under Linux
HD0 = MEDIA
HD1 = Windows
HD2 = Linux


I install windows and then turn on my media drive windows boots fine with this configuration and I can see my media drive a D: on Disk 0
I then insall ubuntu 7,10 from the live CD and when it's about to install I change the boot loader to install at hd1, as hd1 is my first booting device. Once ubuntu completes and I reboot it boot fine into Ubuntu but when I select in the grub menu to boot to XP I get an error,

I have tried : 
map (hd0) (hd1) 
map (hd1) (hd0)
rootnoverify (hd1,0)
makactive 
chainloader +1

I get grub error 17
and the closest I get is missing NTLDR, 
 any ideas

The system is detecting my media drive as the first drive because it's a Riad controller with 5disks in RIAD-5 config.

---

### Post by dhimate on 2008-02-23
Hi,

I was also facing Grub Error 17, after I installed Ubuntu on my Windows XP operated laptop. As mentioned in this thread before, I tried grub shell and fixed the Grub Error 17. Now I can access Windows XP but I cannot access Ubuntu. In the Grub Loader, when I select Ubuntu, it says, "mount error" 

As mentioned above I tried checking /etc/fstab file, But it seems correct. Can someone help me in this regard here?

I could collect following information:

fdisk -lu content:

```
ubuntu@ubuntu:/media/ubuntu$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2   *      160650    37849139    18844245    7  HPFS/NTFS
/dev/sda3        37849140   306279224   134215042+   f  W95 Ext'd (LBA)
/dev/sda4       306279225   312576704     3148740   db  CP/M / CTOS / ...
/dev/sda5        67585518    98430254    15422368+   7  HPFS/NTFS
/dev/sda6   *    37849266    66235994    14193364+  83  Linux
/dev/sda7        66236058    67585454      674698+  82  Linux swap / Solaris
/dev/sda8        98430318   165999644    33784663+   7  HPFS/NTFS
/dev/sda9       165999708   233520839    33760566    7  HPFS/NTFS
/dev/sda10      233520903   301042034    33760566    7  HPFS/NTFS
/dev/sda11      301042098   306279224     2618563+  dd  Unknown

Partition table entries are not in disk order

```

UUID:-


```

ubuntu@ubuntu:/media/ubuntu$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 r
ubuntu@ubuntu:/media/ubuntu$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 200 2008-02-23 20:42 .
drwxr-xr-x 6 root root 120 2008-02-23 20:41 ..
lrwxrwxrwx 1 root root  11 2008-02-23 20:41 035A63BB23095C10 -> ../../sda10
lrwxrwxrwx 1 root root  10 2008-02-23 20:41 03ab0030-d90b-4696-940e-078e8d03694b -> ../../sda6
lrwxrwxrwx 1 root root  11 2008-02-23 20:42 07D7-0A17 -> ../../sda11
lrwxrwxrwx 1 root root  10 2008-02-23 20:41 141C432055FEB8F9 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-02-23 20:41 33a917f8-a6f6-4200-8e6a-d239c494446f -> ../../sda7
lrwxrwxrwx 1 root root  10 2008-02-23 20:41 4F7CC7285390E524 -> ../../sda8
lrwxrwxrwx 1 root root  10 2008-02-23 20:41 B2D8C01ABC060391 -> ../../sda9
lrwxrwxrwx 1 root root  10 2008-02-23 20:41 F800BDEF00BDB54A -> ../../sda2

```


Contents of /etc/fstab file
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=03ab0030-d90b-4696-940e-078e8d03694b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda11
UUID=33a917f8-a6f6-4200-8e6a-d239c494446f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Contents of Menu.lst 

```
ubuntu@ubuntu:/media/ubuntu/boot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=03ab0030-d90b-4696-940e-078e8d03694b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,10)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=03ab0030-d90b-4696-940e-078e8d03694b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,10)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=03ab0030-d90b-4696-940e-078e8d03694b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,10)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda9
title           Microsoft Windows XP Embedded
root            (hd0,8)
savedefault
makeactive
chainloader     +1

``` 

Is reinstalling or deleting Ubuntu is my only  resort?

---

### Post by Herman on 2008-02-23
```
ubuntu@ubuntu:/media/ubuntu$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2   [COLOR=Red]*** **[/COLOR]     160650    37849139    18844245    7  HPFS/NTFS
/dev/sda3        37849140   306279224   134215042+   f  W95 Ext'd (LBA)
/dev/sda4       306279225   312576704     3148740   db  CP/M / CTOS / ...
/dev/sda5        67585518    98430254    15422368+   7  HPFS/NTFS
/dev/sda6   *    37849266    66235994    14193364+  83  Linux
/dev/sda7        66236058    67585454      674698+  82  Linux swap / Solaris
/dev/sda8        98430318   165999644    33784663+   7  HPFS/NTFS
/dev/sda9       165999708   233520839    33760566    7  HPFS/NTFS
/dev/sda10      233520903   301042034    33760566    7  HPFS/NTFS
**[COLOR=Sienna] /dev/sda11      301042098   306279224     2618563+[/COLOR]  [COLOR=Red]dd  Unknown[/COLOR]**

Partition table entries are not in disk order
```According to fdisk the file system is unknown. I am presuming /dev/sda11 is your new Ubuntu installation, is that correct?

Or is it /dev/sda6 ?

If your Ubuntu system is in /dev/sda11, first, try running a file system check with Gnome Partition Editor if you have the Ubuntu Gutsy Gibbon LiveCD or later. [                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")
Or try with [GParted -- LiveCD]("http://gparted.sourceforge.net/"). 

I don't know if that will work at all since the file system doesn't seem to be recognized at all, but it should be worth a try.

:-k Hmm, if this is a brand new installation it probably would be easier to just try again and delete the partition, reformat it and re-install.
Be sure to back up your data before using any hard disk partitioning program.

If your Ubuntu partition is really /dev/sda6, then all you need to do is edit your /boot/grub/menu.lst entries and change all mentions of (hd0,10)  to (hd0,5) instead.

Regards, Herman :)

---

### Post by david2004 on 2008-02-23
Hi everyone,

i am also getting this error 17, I switched off the laptop a week ago (everything was working) and now I am back and get this grub error. I had installed Ubuntu 7.10 over the Vista install, there was no double boot (at least planed this way).

I am getting this information now:

[PHP]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   483153920   488394751     2620416    c  W95 FAT32 (LBA)
/dev/sda2       476246925   488392064     6072570    5  Extended
/dev/sda5       476246988   488392064     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 100 2008-02-23 21:21 .
drwxr-xr-x 6 root root 120 2008-02-23 20:14 ..
lrwxrwxrwx 1 root root  10 2008-02-23 20:14 04d316fe-76cf-4daf-9367-c4600beddb0a -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-02-23 20:14 381C-CAD7 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-02-23 21:21 B8D6-E2FB -> ../../sdb1
ubuntu@ubuntu:~$ /media/ubuntu/boot/grub$ cat menu.lst
bash: /media/ubuntu/boot/grub$: No such file or directory
ubuntu@ubuntu:~$ 

[/PHP]

I am using a liveCD Ubuntu 7.10 and started GParted which shows me 
dev/sda (232.88 GiB) as unallocated

When I look at the total number of sectors and the number of blocks in the device list, I am
getting the bad impression that a whole bunch of blocks are missing :(.

Is there anything else I can run to give you more information? There is only one harddrive installed and when I type 
geometry (hd0, TAB
I get 
Partition num: 0 Filesystem is fat, partition type 0xc
Partition num: 4 Filesystem is unknown, partition type 0x82

Please help!

Thanks to everyone, it's the first time I am installing Linux on a PC,

David

---

### Post by Herman on 2008-02-23
> i am also getting this error 17, I switched off the laptop a week ago (everything was working) and now I am back and get this grub error. I had installed Ubuntu 7.10 over the Vista install, there was no double boot (at least planed this way). Ah, very good, well done! I like you, everyone should install Ubuntu over Vista and not bother dual booting. I agree!   :)

Okay, your partition table does look very unusual to me. 
Normally, the first partition should start at sector number 63, yours starts at [COLOR=#000000][COLOR=#0000bb]476246925 [/COLOR][/COLOR]which seems a little strange, unless you just have a lot of free space there at the start of your disc for some reason. 

The other thing that looks unusual to me is I can't see where you have your Ubuntu partition. Normally Ubuntu is installed in an ext3 or reiserfs file system, which would show up as 'Linux' in your fdisk output. 
I can only see a '[COLOR=#000000][COLOR=#0000bb]c  W95 FAT32 [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]LBA[/COLOR][COLOR=#007700])[/COLOR][/COLOR]'file system, that wouldn't be likely to be your Ubuntu installation? If it is, that could be your main problem, you should re-install and use the ext3 file system or reiserfs next time.

Do you have any data saved in there yet?
If you don't have any data in there that you care about, you might use either Gnome Partition Editor in the Ubuntu Live CD, or [Gnome Partition Editor]("http://gparted.sourceforge.net/") in it's own LiveCD to set a new disc label and install again.
Warning: When you 'set a new disc label', that give you a new empty MBR, so you will lose access to all your information on your hard disc, so back up all your data first!!!

Then you should be able to install Ubuntu with a fresh MBR and no errors, maybe Windows has messed up your partition table somehow.

Regards, Herman  :)

---

### Post by david2004 on 2008-02-24
Dear Herman,

indeed, the whole disk looks strange, when Ubuntu was running, I had nearly the whole disk for Ubuntu (around 230 GB), I might have formated it as FAT32 (I don't remember now).  There are indeed some files I would like to get back from the disk before reinstalling.

Is there a way to get to the data? I could take out the drive of the laptop and put it in an external USB case and connect it to a running linux or winXP machine.

Thanks again,

David

I just found [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
and tried 
sudo parted /dev/sda
when I try
check 0 or check 1... I get "Can't have overlapping partitions"
I get the same error message with print
It looks like something terrible has happened to my partitions??

---

### Post by Herman on 2008-02-24
:) Hello david2004,
You could try to mount the file system in your Ubuntu Live CD, I guess as a FAT32 file system, but I'm not sure.
Then you could copy your data to be rescued into your USB disk, (just drag 'n drop would probably be all you'd need to do, that's the easy part).

Mounting your hard disk installed file system is not really all that difficult either, once you've done that sort of thing once or twice, here's my [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")  which tries to explain that in a way that should be easy to understand I hope.
```
sudo mkdir /media/ubuntu
``````
sudo mount -t vfat /dev/sda1 /media/ubuntu
```If mounting it as a FAT32 file system doesn't work and you remember making it as an ext3 file system then try 
```
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```If neither of those work we might need to look at some other programs for getting your files back.
fdisk or cfdisk can be used to fix your partition table sometimes, or TestDisk.

Regards, Herman :)

---

### Post by david2004 on 2008-02-24
Thanks Herman,
before reading your post, I did following:
download testdisk (6.6.1) on a usb stick
and launched ubuntu 7.10 live CD and installed the package testdisk

I then launched testdisk and it managed to fix my partition and I could boot from the HD again!

I now have
[PHP]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476246924   238123431   83  Linux
/dev/sda2       476246925   488392064     6072570    f  W95 Ext'd (LBA)
/dev/sda5       476246988   488392064     6072538+  82  Linux swap / Solaris
[/PHP]

and
[PHP](parted) print all                                                        

Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  244GB  244GB   primary   ext3         boot 
 2      244GB   250GB  6218MB  extended               lba  
 5      244GB   250GB  6218MB  logical   linux-swap       [/PHP]

I have absolutely no clue why this has happened, the system sometimes was not able to shut down properly, had to push the on/off button long enough :( to switch off, probably damaged the partition?

When you look at above partitions, do you think I configured the system optimally, or should I create a large data partition or two and keep the system in 20 to 40 GB?

Thanks a lot,

I knew I can rely on the community ;)

David

PS: now my wifi is not working, but I guess I can fix it

---

### Post by MWRMWR on 2008-02-24
> **AmericanYellow said:**
> :
1. Enter BIOS
2. Make sure all HDD's are detected.
* *Take note of (write down) the current settings just in case you need to set things back later**
3. Search for the HDD that has Ubuntu installed and set its MODE to AUTO (not LBA, large, or normal)
4. Also, if you have this option available, set TYPE to USER, but don't change any of the figures that were automatically detected.
5. And you are done!
Just in case this doesn't work, then:
6. Set all drives to TYPE --> USER and MODE --> AUTO (not LBA, large or normal)
 ...
I spent ages trying to resolve Error 17, (mis-!)read this article and eventually applied the BIOS change and it worked. 
I undid the BIOS change and error returned. So I re-applied it and went through my 4 Grub-MBR OS startups.
(as far as I can tell by both Drake and Windows Disk Manager), I have 
part 1  32-bit XP
Extended part containing [Part 2 64-bit XP] [Part 3 Vista Ult] 32-bit]
Part 4 Linux Swap
Part 5Linux ext3

OK, I first started the Vista after the change and it did a prolonged "active hang" as if it was trying to fix a fault. I brutally restarted after an hour.
I then tried the XPs and they started by wanting to fix their own disk partition ...at first I skipped this.
After some risk assessment (no,I hadn't backed anything up yet ...but it was all fairly new after wiping the disk!), I decided to let the disk fixing have its way for any OS that felt it wanted to do it.

I ended up with 4 working systems.:)

BUT, it was all working before, so how did I get to this ?
My 64-bit XP partition needed some more space - so I decided to steal it from the Vista partition.
I have often used Partition MAgic 7 before and have my own paid-for copy but I have often had
incidences when inconsistencies are reported by OS and PM7 seems to always get out of step although "things seem to keep working". So, I thought I'd get with it on these highly regarded Linux Tools for amending partitions and burnt myself a PCLinuxOS2007 CD.
Eventually, I managed to figure out how to resize the Vista partition (though the feedback from the tool was less enthusiastic and less informative than PM7) from a LiveCD. I still have to figure out how to move the shrunken partition up but that's a different issue.
It _*was only after applying this change *_and rebooting that Error 17 hit me](*,)

So.. I remain very suspicious of Drake partition Tool.

BUT WORSE:
I had read this post and the copy on the Grub posting and the reason I was reluctant to try was because I read it as requiring me to change from Auto+Auto (which is what I HAD on my BIOS) to some manual setting.
Indeed, that is what I did and I had changed MODE _to _LBA !!
I come back here and read_ that's what it shouldn't be _and I've gone the other way.

fyi, this is with a GA K8NF-9 which is a fairly recent motherboard, so I'd have thought the Auto+Auto was good.

:confused: :confused:

---

### Post by dhimate on 2008-02-24
> Or is it /dev/sda6 ?

Yes it is /dev/sda6

> If your Ubuntu partition is really /dev/sda6, then all you need to do is edit your /boot/grub/menu.lst entries and change all mentions of (hd0,10) to (hd0,5) instead.
Bingo. I verified from /etc/fstab file and the uucode listing, that Ubuntu was really available on /dev/sda6. Modifying menu.lst file and changing (hd0,10) to (hd0,5) worked fine. : :popcorn:

After working for a whiile in Ubuntu, I installed those updates, again it failed in the Grub loader. :confused: But modifying menu.lst file worked very much for me. I am wondering why is it modifying menu.lst file after software updates and reflecting wrong partition there? ](*,)

Anyways. Thanks Hermon. Working on Ubuntu is great fun. Why did I go for Windows in first place :mad:

---

### Post by confused57 on 2008-02-24
> **dhimate said:**
> Yes it is /dev/sda6


Bingo. I verified from /etc/fstab file and the uucode listing, that Ubuntu was really available on /dev/sda6. Modifying menu.lst file and changing (hd0,10) to (hd0,5) worked fine. : :popcorn:

After working for a whiile in Ubuntu, I installed those updates, again it failed in the Grub loader. :confused: But modifying menu.lst file worked very much for me. I am wondering why is it modifying menu.lst file after software updates and reflecting wrong partition there? ](*,)

Anyways. Thanks Hermon. Working on Ubuntu is great fun. Why did I go for Windows in first place :mad:
Your entry for groot:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)
```
needs to be changed to:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)
```

Here are instructions from Herman's website:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

Sorry Herman, you weren't logged in when I replied.

---

### Post by Herman on 2008-02-24
:) Hello dhimate,
> Bingo. I verified from /etc/fstab file and the uucode listing, that Ubuntu was really available on /dev/sda6. Modifying menu.lst file and changing (hd0,10) to (hd0,5) worked fine.
:) Great!
>  After working for a whiile in Ubuntu, I installed those updates, again it failed in the Grub loader. :confused: But modifying menu.lst file worked very much for me. I am wondering why is it modifying menu.lst file after software updates and reflecting wrong partition there? ](*,)
 Check your 'groot' line in your debian automagic kernels section of your /boot/grub/menu.lst file.
Whenever we receive a new Linux kernel in an update, a script called 'update-grub' is run. The update-grub script refers to our debian automagic kernels list area for information and it generates a new /boot/grub/menu.lst from that, with entries in it for the latest (newly installed) Linux kernel.
So, if you have the wrong information in your debian automagic kernel list, your new GRUB menu will be wrong too. :)
Look for a line like this, (click the link), [groot=]("http://users.bigpond.net.au/hermanzone/p15.htm#groot") (grub root device) - if you changed the partition number, make it persistent here.
You should be able to edit that to (hd0,5) , I guess it likely has (hd0,10) or some other number there?
>  Anyways. Thanks Hermon. Working on Ubuntu is great fun. Why did I go for Windows in first place :mad: No Problem, it's my pleasure to be able to help. ... and I agree! Ubuntu rules! :)

Regards, Herman :)

---

### Post by dhimate on 2008-02-25
> **confused57 said:**
> Your entry for groot:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)
```
needs to be changed to:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)
```

Here are instructions from Herman's website:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

Sorry Herman, you weren't logged in when I replied.


Thanks confused57 and Herman. I will try it. Lets hope, I won't need to modify menu.lst next time when there is update needs to be installed. But I am really wondering, whether will it matter changing this entry. I thought it is a commented one and provided as a sample. 
I might sound very stupid here. :confused:

---

### Post by Herman on 2008-02-25
> But I am really wondering, whether will it matter changing this entry. I thought it is a commented one and provided as a sample. That's a fair enough remark. Normally a hash mark in front of a line makes the operating system ignore it and turns the line into a comment. 
For some reason the debian automagic kernels list is special and it needs the single hash marks there, (I don't know why), and it takes two hash marks to turn a line into a comment in that part of the menu.lst file).
Maybe some day I'll learn enough to be able to explain why that is, but at this stage it's just one of those peculiarities that we just accept and think "oh well, progammers are erratic". :lolflag:

Your edit will effective in spite of the single hash mark.

Regards, Herman :)

---

### Post by mrund on 2008-03-02
I have two SCSI drives in my desktop machine, the master and the slave. For years I have booted WinXP from the master drive and used the slave (which is much larger) for data. The other day I installed Ubuntu Gutsy onto a new partition on the slave drive: I did everything automatically and received no error messages. Now GRUB is confused and won't boot either operating system. It gives me no start menu, just an error 17. Super GRUB hasn't helped me either. Even if I liveswap, I can't boot anything off either drive.

On my master drive SDA I now have a confused GRUB,a a small FAT16 partition (sda1) and a large NTFS partition containing WinXP (sda2).

On my slave drive SDB I now have a large NTFS partition with some data (sdb1), a small EXT3 partition containing Gutsy (sdb2) and a small SWAP partition created by Gutsy (sdb5).

Following Mbwardle's suggestions from page 1 of this discussion, I've managed to come as far as:

*10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)*

Here I don't know what numbers to use. Whatever numbers I put in I just get "Error 21: Selected disk does not exist".

I could really use some help!

---

### Post by Herman on 2008-03-02
:)
Please post the output from 'sudo fdisk -lu' here to begin,
Regards, Herman :)

---

### Post by mrund on 2008-03-02
I\m afraid all it says is:

cannot open /proc/partitions

---

### Post by mrund on 2008-03-02
Re-booted and retried, and then I got some info:

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d0675bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+  de  Dell Utility
/dev/sda2   *       64260   117178109    58556925    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b546f54

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   420886934   210443436    7  HPFS/NTFS
/dev/sdb2   *   420886935   486898019    33005542+  83  Linux
/dev/sdb3       486898020   488392064      747022+   5  Extended
/dev/sdb5       486898083   488392064      746991   82  Linux swap / Solaris

---

### Post by Herman on 2008-03-03
> *10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)*

Here I don't know what numbers to use. Whatever numbers I put in I just get "Error 21: Selected disk does not exist". ```
/dev/[COLOR=Sienna]**sdb2**[/COLOR]   *   420886935   486898019    33005542+  83  Linux
```[Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System"). 
```
root (hd1,1)
```:) (hd1,1) should be equivalent in GRUB terms to Linux's /dev/sdb2.

Thank you for the fdisk output.

We have found (thanks to meierfra in this thread), that when there are only two hard disks it is better to [reverse the hard disk boot priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") in the BIOS and [re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"). That has helped several people already that I know of.

---

### Post by mrund on 2008-03-03
My Dell machine's BIOS doesn't offer the opportunity to change boot priorities. I could however switch the physical jumpers on my two SCSI drives to swap master/slave. Would that be a good idea? Wouldn't Windows be likely to get confused if it wasn't on the bootable drive any more?

---

### Post by Herman on 2008-03-03
> My Dell machine's BIOS doesn't offer the opportunity to change boot priorities. I could however switch the physical jumpers on my two SCSI drives to swap master/slave. Would that be a good idea? Yes, it would be worth a try.
> Wouldn't Windows be likely to get confused if it wasn't on the bootable drive any more?No because if GRUB has already set itself up and configured everything upside down then it will already have a pair of 'map' commands in place to trick Windows into thinking it's in  the  first hard drive. (Which it is, but GRUB doesn't think so).  Ubuntu will be set up as if it's in the first hard drive. That's normally why you get GRUB error 17. Then when you switch the hard drive around so they will really be upside down, it makes GRUB right and the error message goes away.

Are you confused yet?

Never mind, it does solve the problem for most computers we've tried it in.

Regards, Herman :)

---

### Post by mrund on 2008-03-03
OK, I swapped the two drives, which of course led to a situation where the computer found no bootable drive at all (since the old buggy grub stage was now on HD2). This was as expected.

Then I booted the Gutsy CD, modified menu.lst and device.map accordingly, installed grub on the new HD1, and rebooted.

And now I have *another* boot disk that starts grub and bugs out with error 17. :confused:

This whole process has been complicated by a mysterious tendency for the drives to become unavailable, as if they entered some kind of power-saving mode really quickly after boot. No such behaviour has ever occurred before.

---

### Post by Herman on 2008-03-03
> OK, I swapped the two drives, which of course led to a situation where the computer found no bootable drive at all (since the old buggy grub stage was now on HD2). This was as expected. Yes, that's what I thought too. Good.
>  Then I booted the Gutsy CD, modified menu.lst and device.map accordingly, installed grub on the new HD1, and rebooted.
And now I have *another* boot disk that starts grub and bugs out with error 17. :confused: Sorry, that's not what is supposed to happen, it should have then been able to boot properly after just re-installing GRUB and without any modifications to /boot/grub/menu.lst and not /boot/grub/device.map either. 
> This whole process has been complicated by a mysterious tendency for the drives to become unavailable, as if they entered some kind of power-saving mode really quickly after boot. No such behaviour has ever occurred before.:confused: Hmmm....

---

### Post by mrund on 2008-03-03
I'm now thinking that I might

1. Disconnect my old HD2 (the current HD1) physically from the machine, taking Gutsy with it.
2. Reinstall a normal Windows MBR (how do I do that?) on the remaining drive so I can boot WIndows.
3. Install Gutsy on a small partition on that drive.
4. Pray that the two operating systems will coexist happily in a system with only one drive.

If this works:

5. Reinstall the secondary drive.
6. Remove the dead Gutsy partition on the secondary drive.
7. Use the secondary drive for data only.

How does that sound?

---

### Post by Herman on 2008-03-03
I am thinking it's a little unusual for someone to get GRUB error 17 with two scsi disks, usually it occurs when we have a mixture of scsi and IDE hard drives.
It' s also strange that [Super Grub Disk]("http://sgd.benjamin-butschko.de/") couldn't even help you. :-k

250 GB is quite a large hard drive, and your Ubuntu installation is close to the end of it. I am just wondering if your BIOS can address that whole disk okay.

I think it might be worth trying a few tests using [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to try to find out what's wrong there.
How about booting your Super Grub Disk and press your 'c' key to go to GRUB's command line?
Try this series of commands.
```
find /vmlinuz
```Grub should reply '(hd0,1)', but if it comes back with something different then use that answer for the partition number in the next command,
```
root (hd0,1)
``````
find /sbin/init
```Grub should reply '(hd1,1)'again, but if it comes back with something different then once again use that answer for the partition number in the next command,
 [Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System").  ```
kernel /vmlinuz root=/dev/sda2
``````
initrd /initrd.img
``````
boot
```Ubuntu should now boot.

If GRUB could not find /vmlinuz or /sbin/init and you could not complete this sequence of commands then possibly your BIOS has a 137 GB hard drive addressing limit. 
If that proves to be the case you should be able to get Ubuntu working if you delete your Ubuntu partitions and resize the NTFS partition to fill the disk again.
Then, re-install Ubuntu but this time make your Ubuntu partitions at the beginning of your hard disk instead of at the other end.
Normally the BIOS hard drive limit would give GRUB error 18 though, so I'm not sure, this is strange.

Maybe we need to[ try a file system check]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem"). 
Or maybe you have a hardware problem or a problem with the way you hard disks are detected and set up in your BIOS.
Anyway let me know how you get along so far and then we'll decide what to do next.

Regards, Herman :)

---

### Post by Herman on 2008-03-03
> I'm now thinking that I might

1. Disconnect my old HD2 (the current HD1) physically from the machine, taking Gutsy with it.
2. Reinstall a normal Windows MBR (how do I do that?) on the remaining drive so I can boot WIndows.
3. Install Gutsy on a small partition on that drive.
4. Pray that the two operating systems will coexist happily in a system with only one drive.

If this works:

5. Reinstall the secondary drive.
6. Remove the dead Gutsy partition on the secondary drive.
7. Use the secondary drive for data only.

How does that sound?1. There should be no need to disconnect drives, you can if you want but it shouldn't do anything, (no logical reason for it).
2. Use Super Grub Disk or something on this page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
3. Yes, and that will re-install GRUB again, so #2. was a waste of time. But that's okay.
4. They should and they do for almost everyone else, you are just having some unusual bad luck, keep on trying!
5. 6. 7. As you like. 

Good luck with it, I think that should work fine. Let me know if it doesn't

Regards Herman :)

---

### Post by mrund on 2008-03-03
Herman, I gotta tell you I really appreciate your help!

But somethings clearly very wrong here.

"find /vmlinuz" resulted in
"Error 15: File not found"

"root (hd0,1)" resulted in
"Filesystem type unknown, partition type 0x83

"find /sbin/init" resulted in
"Error 15: File not found"

The machine showed no strange behaviour before I installed Gutsy the past weekend. And judging from the moments when I can access the disks without trouble, I know that their contents are intact.

---

### Post by mrund on 2008-03-03
But the 137 gig addressing limit is definitely interesting here. I've never had reason to mess around with the >137 gig address space before.

---

### Post by mrund on 2008-03-03
And I found out that there are two conflicting ways to tell the machine which drive is master and which is slave: each drive can be jumpered as master, slave or "cable select". The third alternative is for when you have one black and one grey connector on your drive cable. Which I have, Yet only the slave drive has been jumpered as cable select before.

---

### Post by mrund on 2008-03-03
Phew, I got it all to work. I installed Gutsy on a small partition on the primary drive, I managed to set up the various partitions correctly by hand, and I have now booted both my old WInXP installation and a new Gutsy installation without any trouble.

On my secondary drive, I still have a couple of unnecessary partitions from the failed Gutsy installation, but I can get rid of them later.

---

### Post by Herman on 2008-03-03
That's good.
There's nothing wrong with having all your operating systems in one hard drive and having all your data in another one. I have one computer with Ubuntu Gutsy in the first hard drive plus Feisty, Debian and Open Suse. They all have a mount point in the /home/username directory for the data disc. I find that arrangement quite convenient.
I have another hard drive in the same computer with a new upgrade to Ubuntu Hardy Heron, that one mounts the data hard disk as well, so I can access the same data no matter which of the five operating systems I decide to boot into.
I'm glad you managed to get it working, I suppose it doesn't really matter what was wrong, and you can always try some experiments some day when you have time if you're curious and see what it was.
In the meantime, happy Ubuntuing! 

Regards, Herman :)

---

### Post by Nibblyn on 2008-03-05
Hi!

Having the same problem here. Grub starts but halt immediately (error 17). Tried to install the bootloader on a Floppy. Result: Error 18: Selected cylinder exceeds maximum supported by BIOS.

Now: I'm not an expert but.. IMHO:

Everything on your comp IS working fine, it's a BIOS fault. My comp has 8 years and only the HD is new (250gb). Old BIOS just can't boot from a partition that starts beyond the 1024 (??) border. So, no problem for the first OS, but troubles for the second. It's not an Ubuntu fault.

Well, it can be also because the old BIOS was not built to support that big drives (eg only XP SP2 support more that 137GB drives natively, but I think Ubuntu does the same). However, I will try with a /boot partition but BEFORE the 1024's cylinder limit. But how?

1. /boot of 200Mb as first primary, NTFS as second primary starting before that 1024 cylinder limit. Will Win starts as it seems to require to be on the first?

2. a small Win partition at the beginning, with ext3 starting before the 1024 limit.

Please, let me know if you find something more. No time to review my bad english, hope you understand.

Thank you.
Nibblyn

---

### Post by Herman on 2008-03-06
:) Hello Nibblyn,
If you want to create a /boot partition before the 1024 cylinder limit you probably can.

I made quite a few experiments with Windows and disc partitioning in one of my computers. 

I found out that it didn't matter at all, (at least in my computer), whether Windows XP was first on the hard disk or not. My Windows partition could be 'moved' by GParted (Gnome Partition Editor) anywhere in my 80.0 GB hard disk and it would still boot fine as long as the partition number isn't changed.

If the partition number does get changed somehow, I could also boot Windows XP on any primary partition after editing boot.ini in Windows XP with the correct (new) partition number.
As most people probably won't enjoy having to edit boot.ini, it is best to use only Gnome Partition Editor (GParted), or QTParted, Partman or any LibParted based partitioner, as these will try not to change your partition numbers or interfere with your file system UUID numbers unless you ask them to.

If you think you have an 8.45 GB BIOS hard drive limit you could 'move' your Windows partition slightly to the right with Gnome Partition Editor and make room for a /boot partition at the start of the hard disk for Ubuntu.
I would allow a little more room, say 500 MB, since you have a large enough hard disk to be able to spare a little bit of extra space and I have read a few threads here recently where people have had their /boot partition filled up with new kernels and have run out of space. 500MB should be plenty.

Now, even though your new /boot partition will be in first place in your hard disk, it will be allocated whichever primary partition number is vacant and available, and moving Windows a little to the left should not cause it's partition number to be changed at all, providing you use a LibParted based partitioner.  Windows will still be partition number 1, even though it has been moved to second position on the hard disk.

The partition number your new /boot partition will be given depends on what other primary partitions you may already have. If you already have three primary partitions and an extended, you might have difficulties because you can only have a maximum of four primary partitions, or three primaries and one extended. If you haven't used up your first four partition numbers you should be fine.

If Ubuntu is already installed, you can [make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition"), but if it's a new installation anyway, re-installing Ubuntu would be much faster and easier, making sure to mount your new /boot partition as /boot during installation. (You would choose manual partitioning during installation and do that).

Regards, Herman :)

---

### Post by Commonsensia on 2008-03-08
[QUOTE=AmericanYellow;2650872]After installing Ubuntu on my hard drive( dual booting with Windows XP) I got the Grub 1.5  Error 17 message. Spent 2 days pulling my hair out trying to figure out why I got the error. Browsed the Ubuntu forums, saw good advice, but nothing help. I was just about to give up on Ubuntu, until I just started messing around with my PC and surprisingly :) :) :) :guitar:  the error was gone! Here's what I did:

First a thank you, as this at least pointed me in the right direction :) and thus it only took the hour or so I wasted before bothering to come look for answers. Only took 2 reboots and I was underway after seeing this. Although I had to change the part listed below.

Just wanted to add to this that in the AwardBios there is also the option of setting the Boot HD0,0 to manual or not, this MUST be set to auto as well or you get the same error.
Thanks

---

### Post by SNIPE_M on 2008-03-13
I still have a problem w my laptop & the grub 17 error:( !

 I have the phoenix bios but i used Generic UNetbootin Loader & don`t know how to change the mode to auto for my disk either:confused:.

 And no my disk has no auto option. any help?

 (also it has a OEM copy of windows on it)

---

### Post by Herman on 2008-03-14
:) Hello SNIPE_M,
I can't really help you right now, because I don't have the output from 'sudo fdisk -lu' yet or a copy of the bottom portion of your /boot/grub/menu.lst file.

Do you get GRUB error 17 when trying to boot Windows or when trying to boot Ubuntu?

GRUB error 17 [When trying to boot Linux]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux")                                         (if you only have one hard disk)

GRUB error 17 [When booting Windows]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Windows") (if you only have one hard disk)

From the GNU/GRUB Manual,
> 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.
If you're getting GRUB error 17 when trying to boot either operating system, it might be a good idea to try running a file system check on the Ubuntu partition,
[                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user freindly GUI method, or [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line. That might fix it.

Regards, Herman :)

---

### Post by SNIPE_M on 2008-03-15
I got the error at startup right after installing Ubuntu.
and I installed it on the same drive.:(
(yes my laptop`s C:/ drive can hold Windows [COLOR="Black"]XP[/COLOR] & Ubuntu at the same time but i don`t know how!
:confused:)
I had no live disk when i installed
And if the creator of grub knows error 17 then why dosen`t he fix it anyways

it says on startup stage1.5
 
and i have no dos because it`s xp to fix it internaly

---

### Post by Webdragun on 2008-03-15
> **mbwardle said:**
> I got this error after installing the Ubuntu 7.10 release candidate.

The error usually happens because Linux and your BIOS detect your hard disks in different orders.  GRUB tries to translate between the two using the device.map file in /boot/grub/device.map, which is automatically generated.  Chances are, it guessed wrong.

In my case, I have three SATA hard disks.

My BIOS sees them as:
HDD1 - 80 GB - Windows
HDD2 - 80 GB - Linux
HDD3 - 250 GB - Media

Linux sees them as:
/dev/sda - 80 GB - Windows
/dev/sdb - 250 GB - Media
/dev/sdc - 80 GB - Linux

So it generated device.map assuming that order was correct, i.e.:
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

When the installer installed GRUB using that data, it tried to install the first part of GRUB on /dev/sda and told it to look for the OS on /dev/sdc.  Unfortunately, this translated to "install on (hd0) then look for the OS on (hd2)", so it was looking for the OS on the wrong drive.

To fix it, you have to teach GRUB which order the BIOS uses.  To do this, follow these steps:

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"
8) Edit device.map (using vi or another text editor)

In my case, my new device.map was:
(hd0)    /dev/sda
(hd1)    /dev/sdc
(hd2)    /dev/sdb

which told GRUB that sdc was really the second hard drive, not the third.

9) Run "grub --device.map=device.map"
10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)

You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that.  This is what we want.

12) Edit menu.lst

You need to change references from (hd2,0) to (hd1,0), or whatever your Linux boot drive was autodetected as to whatever it is according to your BIOS.

If you get this step wrong, you'll see an error message something like:
Error 17: Cannot mount selected partition

meaning it's looking for a Linux file system on that partition, but it can't find one (because the drive device number is wrong in menu.lst).

13) Reboot

14) Celebrate or complain in this thread!

First off let me say this is an excellent solution and gives hope to new users like me. :)
however.. I'm having this same issue but only have 1 sata drive w/ multiple partitions.. how can you tell how linux sees the partitions vs how windows sees them?  any help would be greatly appreciated!

---

### Post by Herman on 2008-03-15
:) Hello SNIPE_M,
>  And if the creator of grub knows error 17 then why dosen`t he fix it anyways :lolflag: Hey, that's a great idea! Why didn't I think of that? And right after that we can just solve the energy crisis and make peace in the middle east and end global warming and... :)

:) Actually, it is because there are so many different computers with different BIOSes, that GRUB can't easily be made to suit every different kind of hard disk and partitioning arrangement in every computer, but it tries hard.

A man named Erich Boleyn, [http://www.uruk.org/~erich/]("http://www.uruk.org/%7Eerich/") is the original developer of GRUB, but he gave it to everyone who uses Gnu/Linux so now it's called GNU/GRUB. 
[GNU/GRUB]("http://www.gnu.org/software/grub/") is what we're using now, but it's not being developed any more either, the GRUB developers are concentrating on [GRUB2]("http://www.gnu.org/software/grub/grub-2.en.html") now. Maybe GRUB2 will be better.

Error 17 isn't just caused by one thing either, it can be caused by a number of  different factors, as you would realize if you read my collection of information on it that I've gathered so far. [     Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17"). So more information is needed to find out what's causing it in your computer and then we can try to decide how to fix it.

>          I got the error at startup right after installing Ubuntu.
and I installed it on the same drive.:sad:
(yes my laptop`s C:/ drive can hold Windows & Ubuntu at the same time but i don`t know how!
:confused:)
I had no live disk when i installed :) Okay, sorry about that, I guess maybe you have no CD drive then and can't use a USB stick or a floppy disk?
Will it be any help to get Unetbootin Super Grub Disk from[SourceForge.net: Files]("http://www.google.com.au/url?sa=t&ct=res&cd=4&url=http%3A%2F%2Fsourceforge.net%2Fproject%2Fshowfiles.php%3Fgroup_id%3D198821&ei=ZU7cR4-WBo3CgwOMuMG-Cw&usg=AFQjCNHyHEi4tyIhfPhcDeCCjX_QzZaWzg&sig2=Xq8kD3jPLaDygDG9HVn3kQ")? I don't know much about Unetbootin, I imagine you need to boot somehow first do you? That would be a classic catch22 situation.
Super Grub Disk should be able to boot your computer for you if you are able to use it somehow.

You probably installed Ubuntu on the same hard drive, but you shrank your 'C'  partition (called a 'C' 'drive' in Windows language). So Windows is in one partition and Ubuntu Linux is in another partition in your hard disk.

Let me know if you can't do anything, maybe you'll have to take your hard disk out and put it in another computer that has a CD/DVD drive so you can fix it, I'm not sure.
What drives does your computer have?

Regards, Herman :)

---

### Post by Herman on 2008-03-15
:) Hello Webdragun, 
I don't know what happened to **mbwardle, **just busy or away somewhere maybe I hope.> I'm having this same issue but only have 1 sata drive w/ multiple partitions.. how can you tell how linux sees the partitions vs how windows sees them? any help would be greatly appreciated!  Well if you only have one hard drive, it wouldn't have anything to do with your /boot/grub/device.map. Editing that only seems to be useful if you have three or more hard disks.
For two hard disks, we can reverse the hard disk boot priority in the BIOS, and that fixes GRUB error 17 in most cases. [    Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").
         
When you only have one hard disk, it probably has a lot to do with your /boot/grub/menu.lst file not matching your partition information, or you need a file system check.

If you can boot a Live CD and open a terminal in it and run the command 'sudo fdisk -lu', that will show us how Linux sees your hard disk(s) and partitions. It doesn't matter how Windows sees your partitions.
```
sudo fdisk -lu
```If Ubuntu won't boot you'll be able to use your Live CD to [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") and copy of the bottom section of your /boot/grub/menu.lst file and post it here please.

Then I or another Ubuntu Web Forums member will be able to help you edit it with the correct partition numbers, if that's what the problem is.
We nearly always need at least those two pieces of information before we be much help at all.

Regards, Herman :)

---

### Post by power.mom on 2008-03-19
I have been dealing with Error 17 for a week now; I've tried my BIOS settings, but don't have an automatic setting to switch to.  I've tried many options on this forum

right now I am stuck because when I go to /boot/grub/menu.lst file there is nothing in the file to edit or copy.  :confused:

Help??

---

### Post by Herman on 2008-03-19
:) Hello power.mom,
Do you have one hard disk or more than one?
Did you install Ubuntu by itself or dual booting with some other operating system(s)?

If you have Ubuntu by itself on a single hard disk it might just need a file system check.
You can run a file system check from your Ubuntu Live CD in either of two ways.
Either 
1)[Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user freindly GUI method.
Or
2) [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

Other than that GRUB error 17 in a single hard disk computer, if it happens when you're trying to boot Ubuntu, usually means there's a [simple mistake in your /boot/grub/menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux") file.

If you are getting an empty /boot/grub/menu.lst it either means that you made a spelling mistake when you typed 'gksudo gedit /boot/grub/menu.lst', or if you are using the Ubuntu Live CD you have to mount your hard disk installed Ubuntu system first.

Typing 'gksudo gedit /boot/grub/menu.lst' in the Live CD will always give you an empty file, because there is no /boot/grub/menu.lst in the live cd.
Bit if you mount the hard disk installed Ubuntu file system in /media/ubuntu first, then when you type 'gksudo gedit /media/ubuntu/boot/grub/menu.lst', you should actaully get your hard disk installation's /boot/grub/menu.lst file.
That link I just gave you should lead you to other links that explain that in case you aren't sure.
If you're still not sure, don't be shyto ask and I'll explain more.
If you need more help, please post the output from 'sudo fdisk -lu'
```
sudo fdisk -lu
```, and if possible, the bottom of your /boot/grub/menu.lst file.

:) Regards, Herman

---

### Post by Nibblyn on 2008-03-20
Hello Herman!

Dropping a line to confirm that everything is up and running. I see I'm not the only one having that "bad" hobby installing Ubuntu to other users...

I used SystemRescueCD which permitted me to use GParted in a graphical environment while having on hand some other useful tools if needed. Because the machine is equipped with only 256Mb of ram, I added another 256Mb module (512 in total) just to speed up things until installation is finished. I checked, defragged, resized (now 30Gb) and moved slightly to the right the windows partition, cleared the rest of the HD. At the beginning of the drive I made an 1Gb /boot partition but windows remained partition number 1 even if it is the second partition of the drive. The rest of the HD consist of an extended with a /swap, a /user and /root partitions. Installed Ubuntu without problems. Grub works fine now.

Thanks for your help. Good html pages of yours, lots of useful things in there.
Nibblyn

---

### Post by Tiamats_Chosen on 2008-03-20
ok my error 17 is wierd   all i did was replace my dvdrom wiht a dvd-rw and got the message.   when i switched them back out it works just fine.  i didnt think the the dvd drive has any affect on grub.

i went in and checked BIOS and with the DVD-RW pluged in it doesnt show anything on that IDE cable(the dvd-rw and my linux HD)

---

### Post by Herman on 2008-03-20
:) Hello Nibblyn,
Cool! Thanks for taking the time to come back and share your good news. 
Happy Ubuntuing! :)

:) Hello Tiamats_Chosen,
Your CD/DVD drive sure can affect GRUB alright, because the way you plug in IDE (PATA) hard drives and the jumper settings tell the BIOS which hard drive is number 1 or Primary Master, and which is Primary Slave, (number 2 hard drive), and so on.
Most new drives come jumpered as Master, by default, and when you install a new IDE drive, you need to check the jumper setting when you install the hard disk or CD/DVD drive and make sure you setr it right for your computer.
If you have the old kind of IDE cables, you need to set one drive as master and one as slave on the primary cable, and one as master and the other as slave on the secondary IDE cable.
If you have the modern 'Cable-Select' type of IDE cables, you should set your jumpers all to 'Cable-Select'. The Blue end of the cable plugs into the motherboard, the black end is for the Master, and and grey end is for a slave drive.

Change your jumper settings or the way your discs are plugged in to get GRUB back working again with your new DVD-RW drive.
[Guide to Installing IDE devices]("http://freepctech.com/pc/001/installing_ide_devices.shtml") 

[Hard Drive Installation Guide - PCSTATS.com]("http://www.pcstats.com/articleview.cfm?articleID=1059") 

[IDE Standard]("http://www.ele.uri.edu/courses/ele408/s2001/projects/roland_ide/ide.html") 


Sometimes you can [Change the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") in your BIOS and cure GRUB error 17 that way instead.

Regards, Herman  :)

---

### Post by SNIPE_M on 2008-03-21
I need help on how to boot the live cd so i can skip the grub error 17 on my laptop.Since my dvd drive is broken

---

### Post by planbskate123 on 2008-03-21
help i am getting the same error as you but i think it is a different problem.  i wanted to delete linux from my hd (i have both xp and ubuntu installed) so inwindows i went to disk managment and deleted the partition that i had linux on.  I restarted my computer and now i cant get to either xp or linux i just get this grub error.  Will reinstalling linux help at all or is there any other way to fix this?? please help!!!

---

### Post by Webdragun on 2008-03-21
Thanks Herman,

I have since ran the recovery disk for the laptop to start fresh.. which then gave a grub error 22.. i took this to mean that windows vista does not automatically rebuild the boot loader. after some searching and downloading.. i was able force vista to rebuild the loader.  the laptop is back to a vista only machine for now.  thanx for you're reply though.. i have noted it for when i try again.

in the mean time I have successfully installed ubuntu 7.1 on my desktop and it loads fine.. got some issues with wireless and sound, but that's best suited for another thread i guess.

thanks again!

-Webdragun

---

### Post by Herman on 2008-03-21
:) Hello SNIPE_M,
> I need help on how to boot the live cd so i can skip the grub error 17 on my laptop Normally, booting a LiveCD is easy, take a look at this page and see if anything there helps you, [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm").



:) Hello planbskate123,
> help i am getting the same error as you but i think it is a different problem. i wanted to delete linux from my hd (i have both xp and ubuntu installed) so inwindows i went to disk managment and deleted the partition that i had linux on. I restarted my computer and now i cant get to either xp or linux i just get this grub error. Will reinstalling linux help at all or is there any other way to fix this?? please help!!!Okay, look in this web page for the answers, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").

:) Hello Webdragun,
> in the mean time I have successfully installed ubuntu 7.1 on my desktop and it loads fine..
Okay, cool! It won't take you very long to get used to GRUB and Ubuntu, I'm glad you didn't give up. Congratulations and keep on Ubuntuing! :)

Regards, Herman :)

---

### Post by william_lee on 2008-03-24
I just wanted to thank the poster who supplied the link to Supergrub as a fix for this error.  I was trying not to panic after receiving it unexpectedly, but it is always disconcerting to not have a drive boot.   Anyways, Supergrub fixed the issue painlessly and I am breathing again!

Thanks for the info.

---

### Post by Nylink on 2008-04-08
I have a massive problem. My patience is wearing on me because I think something might have messed up pretty bad.

I installed Ubuntu a while ago, got it running smoothly. I started up my computer this morning, and I got the Error 17 message. I tried reinstalling grub, and I now see the list; however, I cannot boot into ubuntu or windows from my hard disk (whenever I try to get into windows, I get a message saying I should reinstall hal.dll, whatever that is).

Also, when I try installing super grub (setup hd1 in the grub menu), it gives me the Error 17 again, telling me I cannot mount the drive. It is so frustrating.

when I run 'sudo fdisk -lu', I get this:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   166079969    83039953+   7  HPFS/NTFS
/dev/sda2       166079970   268414019    51167025    f  W95 Ext'd (LBA)
/dev/sda3       268414020   625137344   178361662+   7  HPFS/NTFS
/dev/sda5       170080218   209712509    19816146   83  Linux
/dev/sda6       209712573   268414019    29350723+   7  HPFS/NTFS
/dev/sda7       166080096   170080154     2000029+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798272 bytes
32 heads, 62 sectors/track, 1015 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(392205, 19, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(967563, 8, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(85024, 30, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1060845, 20, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(942480, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1918301, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?  2885681152  2885736650       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1454476, 12, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1454504, 11, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

I went ahead and put supergrub on a bootable CD. Followed the instructions, but I can't even choose ubuntu in the list anymore. It goes straight to windows, but I can't boot windows because of that .dll error.
My luck sucks just a bit now.
Any idea on how to fix this, or is it unrecoverable?

---

### Post by Herman on 2008-04-09
:) Hello Nylink,
My first thought is that it seems likely to be some kind of hardware problem. I am only guessing, but it seems that way because of the way you said the computer was working okay when you shut it down, and it wasn't when you went to restart it again later. (Without any other events happening that you can remember). Another thing is, even Super Grub Disk can't boot anything.

You forgot to say which hard disk Ubuntu and Windows is in, I guess you mean they are in the first hard disk?
Your fdisk output looks okay for the first hard disk.
If your fdisk output looks okay then it's a sign that your hardware is probably okay. If the hard disk wasn't working it wouldn't show up in fdisk.

The fdisk output for the second hard disk looks very strange. Can you tell me more about your second hard disk?
> Also, when I try installing super grub (setup hd1 in the grub menu), it gives me the Error 17 again, telling me I cannot mount the drive. It is so frustrating. Do you want to install GRUB to your first hard disk or to your second hard disk?
Most people want to install GRUB to their first hard disk, and the way to do that is to type 'setup (hd0)', because GRUB starts counting from zero.
> Any idea on how to fix this, or is it unrecoverable?      Well I don't like to give up easily. I like to test things to try to find out what the problem is exactly and try experiments to see if we can get it to boot.

How about booting your Super Grub Disk again and press your 'C' key from a menu and get [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
Type in a few commands like,
```
find /boot/grub/stage2
``````
root (hd0,4)
``````
kernel   /vmlinuz   root=/dev/sda5
``````
initrd    /initrd.img
``````
boot
```Try those commands and see if Ubuntu will boot, or if you get some error messages, please let me know what they are.

Regards, Herman :)

---

### Post by Nylink on 2008-04-09
Thanks for your help Herman. I really appreciate it. The second disk was a usb key that I had plugged in. I left the info there by accident, sorry to confuse you.

I only have 1 HD (I think it is HD 0), partitioned quite a bit, as you can probably see.
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   166079969    83039953+   7  HPFS/NTFS
/dev/sda2       166079970   268414019    51167025    f  W95 Ext'd (LBA)
/dev/sda3       268414020   625137344   178361662+   7  HPFS/NTFS
/dev/sda5       170080218   209712509    19816146   83  Linux
/dev/sda6       209712573   268414019    29350723+   7  HPFS/NTFS
/dev/sda7       166080096   170080154     2000029+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
From the code you gave me, I was able to boot into ubuntu without error. Restarting the system is the problem for me since I can't access Ubuntu or Windows through the boot menu.  I'm still able to access my files, so that's one saving grace. Thanks.

---

### Post by Herman on 2008-04-09
:) Okay then, that's very good. :)
If you can boot into Ubuntu using GRUB's Command Line Interface, then you will also be able to boot into Ubuntu, and Windows too I think, in the normal way by editing your /boot/grub/menu.lst file in Ubuntu.

Which partition is your Windows installation(s) in?

Can you please boot into Ubuntu and post here a copy of the bottom half of your /boot/grub/menu.lst file?
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Nylink on 2008-04-09
My windows installation is on a seperate partition from my files, it should be /dev/sda6

Here is the bottom half of the /boot/grub/menu.lst file:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
I don't really understand all of this, but shouldn't the root of XP be (hd0,6) since that's where my windows install is, and the root of ubuntu should be (hd0,4)?  I'm not too worried about the windows partition, I just want to get ubuntu back lol. Am I confused with the above guesses?

Thanks for all the help

---

### Post by unutbu on 2008-04-09
Herman, when you have a moment, would you please read
[http://ubuntuforums.org/showthread.php?t=750255](http://ubuntuforums.org/showthread.php?t=750255)
Thanks! :)

---

### Post by Herman on 2008-04-09
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0****)
savedefault
makeactive
chainloader    +1
```Yes, you are exactly correct, your Ubuntu installation is now (hd0,4), so we need to change the entries in /boot/grub/menu.lst accordingly and Ubuntu should boot okay from the GRUB menu from now on.

:confused: So your Windows installation is in /dev/sda6?
How did it get there?
In most computers, Windows is in the first partition, /dev/sda1. 
It's interesting that GRUB was even getting as far as the hal.dll error when trying to boot Windows when you had the (hd0,0) number in your menu.lst entry for Windows. You must have some Windows files in partition 1 then? An old installation?
I'll need to find out more about what's going on there to help you get Windows to boot. 
Your hal.dll error usually means GRUB has done it's job and chainloaded Windows okay and Windows is trying to boot, but is confused about what partition number it has. You probably need to edit boot.ini in Windows to tell Windows what partition number it's in. 
Here's my collection of information about that, [hal.dll is missing or corrupt.]("http://users.bigpond.net.au/hermanzone/p15.htm#hal.dll_is_missing_or_corrupt")
I'm not sure if we'll be able to get Windows to boot in a logical partition (the partition number 6 tells me this Windows installation is in a logical partition). Windows can boot in a logical partition but as far as I know it needs to boot via another Windows installation in a primary 'boot' partition (hd0,0) probably. 
It would be interesting to try to get it to boot, are your Windows boot files in (hd0,0)?
Maybe we just need to edit boot.ini in partition number 1 to get Windows in partition 6 to boot.
More information will be needed so I can help you with that. :)

Regards, Herman :)

---

### Post by Nylink on 2008-04-09
> Yes, you are exactly correct, your Ubuntu installation is now (hd0,4), so we need to change the entries in /boot/grub/menu.lst accordingly and Ubuntu should boot okay from the GRUB menu from now on.
What should I change in menu.lst?

> :confused: So your Windows installation is in /dev/sda6?
Hmm, long story. Basically, I started using windows first, but split my HD into 3 partitions. I used the middle of the three partitions to install Windows on, then further along the line, I split my first partition to install ubuntu/linux swap. I don't know how the boot got on that partition, it shouldn't be there I think.

> It's interesting that GRUB was even getting as far as the hal.dll error when trying to boot Windows when you had the (hd0,0) number in your menu.lst entry for Windows. You must have some Windows files in partition 1 then? An old installation?
Nope, there isn't an old installation there, but there is a boot.ini file and seems like some windows files. I can't remember what I did to cause that problem, but I didn't install Windows on that partition. I knew i screwed up somewhere :rolleyes:

I can only find boot.ini in the first partition (hd0,0 it seems), not in the one Windows (HD0,6) is installed in. Here is what it says:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
```
From the site you linked, I think I can figure out the rest on my own with windows. So I'll give that a go.

I'm not too worried about windows though. I'd like to learn what I need to know to fix ubuntu/not to cause this error again. Thanks a lot.

Edit: Didn't fix windows, so I'll try using the recovery console.
Edit 2: Using the recovery console didnt work either, I give up on Windows.

THanks for the help

---

### Post by Herman on 2008-04-09
You need to change your menu.lst from having a '6' for your Ubuntu partition, to a '4' instead.
Before:
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,[COLOR=Red]**6**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,[COLOR=Red]**6**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd0,[COLOR=Red]**6**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd0[COLOR=Red]**,6**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,[COLOR=Red]**6**[/COLOR])
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```After:
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3aeafbe4-5b1d-4476-b4b1-c6f24e63b95c ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,[COLOR=Sienna]**4**[/COLOR])
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```I was hoping you had NTLDR, NTdetect.com and boot.ini in your first partition.

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition([COLOR=Red]**3**[/COLOR])\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR=Red]**3**[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition([COLOR=Sienna]**6**[/COLOR])\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR=Sienna]**6**[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

I know for sure those aren't the only files you need in there to get Windows in a logical partition to boot. I have read you need a 'boot sector image' file,  (copy of the boot sector there too), named 'bootsect.dos'.
Maybe you already have one but it is an old one and you need a new boot sector image file.
Since the Windows boot loader can't understand systems like GRUB does, the boot sector is needed to store the location of the other important files needed to boot or else Windows won't be able to find all its parts. 
If you're interested and you have time maybe we can work on getting your WIndows to boot after all. It's up to you.
It might be a waste of time. I am curious about it, because so far I haven't heard of anyone being able to do it and if we succeed in doing so it will help others in the future who get stuck with this problem, but who are under stress about losing Windows.
We will need to study this page, [http://www.goodells.net/multiboot/principles.htm](http://www.goodells.net/multiboot/principles.htm)
I have to go right now in a hurry, but I'll be back later. :)

---

### Post by Nylink on 2008-04-10
Ah, thanks. I forgot to edit the menu.lst before. Everything is okay now it seems.

With my boot.ini file, I have autoexec.bat, config,sys, IO.sys, MSDOS.sys, NTDETECT.com and ntldr included in the same folder. No sign of bootsect.dos.

Edited the boot.ini again, hopefully it works.

Edit: It didn't. Ubuntu boots fine though.

The Windows error I get is:
"Windows could not start because of a computer disk hardware configuration problem. 
Could not read from the selected boot disk.
Check boot path and disk hardware"

When I open gparted, my sda1 (HD0,0) I think it is, is labelled boot. Don't think I've seen that labelled as boot before.

It then goes on to say that I should check windows documentation and stuff.

---

### Post by Herman on 2008-04-10
:) Okay, I want to try mounting your /dev/sda1 and your /dev/sda6 partition, (if that's your Windows XP partition), in Ubuntu and copy the important Windows boot loader files NTLDR, NTdetect.com and boot.ini from /dev/sda1 to your Windows partition, (/dev/sda6).
You can leave the original copies in /dev/sda1, but paste a copy of them into /dev/sda6 for me please.

Then, try chainloading /dev/sda6 with GRUB and see if it'll boot or at least try to boot on it's own.

You can do that by typing the commands into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") or you can edit your /boot/grub/menu.lst, whichever you think will be the easiest.

To use GRUB's Command Line Interface, you would do it like in this link, [**Chainloading Windows the simple way**]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way").
Except you would replace where it has '(hd0,0)', with '(hd0,5).

Try that and see if it helps. :)

---

### Post by Herman on 2008-04-12
:) Okay, after a day of experimenting and being messed around, I believe I have solved the problem of how to boot Windows in a logical partition without any primary Windows 'boot' partition.

The main problem is that Windows needs the boot flag set on the partition to be booted and no boot loaders I know of can put the boot flag in a logical partition.
:) Happily, I discovered that GParted can do it.
So you need to use GParted to set the boot flag for the Windows logical partition. Once it is set, no boot loader can touch it, so it will remain there and not need any further attention.

The next problem is, GRUB gives error 12 after the 'makeactive' command. and fails to complete the boot-up sequence. 
It is necessary to delete or hash out the 'makeactive' command from the /boot/grub/menu.lst stanza for booting the Windows installation concerned (in the logical partition).
If there are any other Windows installations in the computer, it is necessary to use [GRUB's hide and unhide commands]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk") to make the correct Windows system boot, (if you haven't done so already).

The Windows operating system in the logical partition will have a normal boot sector, but it will have no ntldr, NTDETECT.COM, or boot.ini file. 
Those vital Windows booting files will need to be copied from another partition or another computer with Windows XP in it or from the CD you can download from the following website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"). 
If security settings permit, those can simply be pasted in from Ubuntu into the root of drive C: in Windows.

You will probably need to edit boot.ini with the correct partition number.
You can do that from Ubuntu too, providing security settings permit that.
It's okay to edit a few numbers in the file from Ubuntu, but avoid any major changes, particulary avoid adding new lines. Ubuntu's gedit text editor makes line breaks differently to Windows (when you press 'Return', and that will corrupt the boot.ini file as far as Windows is concerned.
If you corrupt a boot.ini file, Windows might begin to boot, and then blue-screen with the message 'autocheck program not found - skipping AUTOCHECK', and reboot suddenly.
Don't worry though, a brand new boot.ini file can be generated from a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), by running the command 'bootcfg /rebuild' (when logged in to the appropriate drive).
For some people that might be easier than editing the boot.ini file from Ubuntu.

So from now on if some poor soul has deleted their primary Windows 'boot' operating system and is left with an unusable but newer version of Windows in a logical partition, we know how to help them. :)

Regards, Herman :)

---

### Post by Nylink on 2008-04-13
Thanks Herman for taking the time out to post about this.

After spending a day or so away from my computer, I came back to do what you posted. 

I moved the necessary files to sda6, tried editing grub through the command prompt, and I got grub error 12 as you stated in your second post. I removed the makeactive command from menu.lst, flagged my windows install on sda6 as boot, copied over my boot.ini file from the partition it was in. I rebooted, and I got the same error I did before: "Windows could not start because of a computer disk hardware configuration problem." So I popped in my XP DVD (took a lot of working finding it first lol), and ran the bootcfg /rebuild command. bootcfg spit out another error, saying I must use the chkdsk command to see if anything is wrong. I did run the chkdsk command, only to get a really depressing message: "This volume appears to contain one or more unrecoverable problems"

I think that message ended my journey for now. I'm thinking about buying a new drive or something, or maybe formatting this drive and starting over, that is, if it works. Thanks again for putting all this work into my problem.

---

### Post by charbilas on 2008-04-13
Hello
I installed ubuntu 7.04 on a computer that has a harddrive 160 GB.Bios doesn't see it as 160 GB but as 136GB. I think that for this bios is the limit. In this harddrive I allready had install winxp on a partition of 136 GB so I made an ext3 partition and a swap partition to the other 13.2 GB as it said.
Linux copied the files but when the computer rebooted grub wouldn't start with error 17. I tried super grub but when I asked to go to the boot of linux it said error 18.
Then I searched in the forum and I found out that its a problem of bios and that I should move the boot record in the beginning of the harddrive. Is this possible without losing the data that I allready have on the windows partition?
Thanks 
Christos

---

### Post by Herman on 2008-04-14
:) Hello charbilas,
You should be able to resize your Windows partition with a hard disk partitioning program like GParted in the Ubuntu Gusty Gibbon or Hardy Heron Live CD, or with GParted in it's own LiveCD.

You should always make a backup before using any hard disk partitioning program on a hard disk, although GParted is as safe if not safer than any other hard disk partitioning program and is quite capable of working with NTFS.
If you make a backup to some separate media then it's highly unlikely that you will possibly lose data.

You can resize Windows from either end, it shouldn't matter. 
If your Windows has the NTFS file system, and GParted can't resize it, run CHKDSK /R from a  [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and try again and then GParted should be able to work with it. Run CHKDSK /R on it again afterwards too.

Make a small partition that is within the 137 (136) GB hard drive limit, around a quarter of a GB to half a GB should be big enough, or make it 1.0 GB if you want to be sure. You can format it with an  ext2 or ext3 file system.

Then you need to mount both your hard disk installed Ubuntu and your new /boot partition in your Ubuntu LiveCD operating system, (or GParted LiveCD).
See this link if you don't know how, [Mounting Linux  ext3 or reiserfs filesystems]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem")  and mount your new /boot partition's file system.

For example, if my new /boot partition will be /dev/hda4, and I'm using a Ubuntu LiveCD, so I need to use the sudo command,
```
sudo mkdir /media/boot
``````
sudo mount -t ext3 /dev/hda4 /media/boot
```Where: hda4 is the right partition designation for the new /boot partition, if not then substitute this number for something else, like /dev/hda1 or /dev/sda3 or whatever is right for your computer.

Now mount your Ubuntu hard disk installed operating system the same way,
```
sudo mkdir /media/ubuntu
``````
sudo mount -t ext3 /dev/hda2 /media/ubuntu
```Where: /dev/hda2 is the hard disk installed Ubuntu's partition designation. Otherwise feel free to replace this number for something else, like /dev/hda4 or /dev/sda5 or whatever is right for your particular computer.

Copy all the files from the /boot directory in the installed system into the new empty partition.
Do not copy the directory itself, just all the stuff inside it.
You will probably need to use a sudo command for that,
```
sudo cp -r /media/ubuntu/boot/* /media/boot/
```You would also need to add a line for the new partition in your /etc/fstab file, registering it as /boot. You can edit your installed operating system's /etc/fstab file from the Ubuntu Live CD too, the link here explains a little about that, see [                                Mount a different Linux filesystem (ext3) in Ubuntu]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu"). When you have looked at that link so you'll know what you're doing, come back here and run this command to get your /etc/fstab file for editing,
```
gksudo gedit /media/ubuntu/etc/fstab
```Maybe it will look something like this, 
BEFORE:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>       <type>           <options>                <dump>  <pass>

   proc          /proc               proc             defaults                  0       0

# /dev/hda2       
UUID=61e29deb-c5c3-4401-8557-81482aedc839  /   ext3    defaults,errors=remount-ro 0       1

# /dev/hda5
UUID=a08d44f6-d681-4901-a7cc-345fc9fa9eb6 none  swap     sw                       0       0

#[COLOR=#000000][FONT=Bitstream Vera Sans Mono]/dev/hda1     
[/FONT][/COLOR][FONT=Bitstream Vera Sans Mono]UUID=[/FONT][FONT=Bitstream Vera Sans Mono][COLOR=#33ccff][COLOR=Black]285F98566380864A[/COLOR][/COLOR][/FONT][COLOR=#000000][FONT=Bitstream Vera Sans Mono]/media/windows  ntfs ro,umask=0002,nls=utf8      0         0[/FONT][/COLOR]

/dev/cdrom      /media/cdrom0     udf,iso9660         user,noauto                 0       0

/dev/fd0        /media/floppy0      auto             rw,user,noauto               0       0

```AFTER:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>       <type>           <options>                <dump>  <pass>

   proc          /proc               proc             defaults                  0       0

[COLOR=Sienna][B]# /dev/hda4
UUID=9e9e5184-127f-45d2-bf4a-e6f0a112f180   /boot  ext3 defaults,errors=remount-ro  0       1[/B][/COLOR]

# /dev/hda2       
UUID=61e29deb-c5c3-4401-8557-81482aedc839  /   ext3    defaults,errors=remount-ro 0       1

# /dev/hda5
UUID=a08d44f6-d681-4901-a7cc-345fc9fa9eb6 none  swap     sw                       0       0

#[COLOR=#000000][FONT=Bitstream Vera Sans Mono]/dev/hda1     
[/FONT][/COLOR][FONT=Bitstream Vera Sans Mono]UUID=[/FONT][FONT=Bitstream Vera Sans Mono][COLOR=#33ccff][COLOR=Black]285F98566380864A[/COLOR][/COLOR][/FONT][COLOR=#000000][FONT=Bitstream Vera Sans Mono]/media/windows  ntfs ro,umask=0002,nls=utf8      0         0[/FONT][/COLOR]

/dev/cdrom      /media/cdrom0     udf,iso9660         user,noauto                 0       0

/dev/fd0        /media/floppy0      auto             rw,user,noauto               0       0

``` You need to add your own line in your /etc/fstab file something like that, with the correct file system UUID number.
It won't be too hard if you read that link I gave.
See also: [                          About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")
```
sudo vol_id -u /dev/hda4
```Where: /dev/hda4 is the partition to be mounted as the /boot partition on start-up from now on. 

You will  also need to edit your /boot/grub/menu.lst file with the new partition information with the new path for your Linux kernel,
```
gksudo gedit /media/boot/grub/menu.lst
```When your /boot/grub/menu.lst file is open, scroll down to around the bottom of the file and look for your Ubuntu boot entries. 
It should look something like mine, below,
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,[COLOR=Red]**1**[/COLOR])
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=61e29deb-c5c3-4401-8557-81482aedc839 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```Change this (above),

to this (below),
```
title        Ubuntu, kernel 2.6.20-15-generic
 root        (hd0,[COLOR=Sienna]**3**[/COLOR])
 kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=61e29deb-c5c3-4401-8557-81482aedc839 ro quiet splash
 initrd        /boot/initrd.img-2.6.20-15-generic
 quiet
 savedefault
```Where: (hd0,3) will be the GRUB notation for your new /boot partition (dev/hda4 in my example). 
See: [A Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")
NOTE:  Since the new /boot partition doesn't have a directory named /boot in it, I removed the '/boot' from the path to the kernel and initrd.img in the two middle lines.

And don't forget to make the 'root (hd0,1)' change persistant during kernel updates when update-grub automatically generates a new /boot/grub/menu.lst file.
You do that by editing your 'groot' line, in the debian automagic kernels list area of our /boot/grub/menu.lst file. Scroll up to somewhere closer to the middle of the file to look for that. Refer to this link for more information, [# groot=(hd0,1)]("http://users.bigpond.net.au/hermanzone/p15.htm#groot")
Change this part of your /boot/grub/menu.lst
BEFORE:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,[COLOR=Red]**1**[/COLOR])

```AFTER,
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,[COLOR=Sienna]**3**[/COLOR])

```Where: (hd0,1) was my old GRUB designation for the partition my kernel lives in and (hd0,3) is the GRUB designation for where I want any new kernels installed from now on. 
Make sure you find out the right partitions for your computer and replace these example numbers with whatever is correct for your special machine.
Don't forget to save your menu.lst file before closing.

You will need to re-install GRUB, see: [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD
                                                                 You will need to set your new /boot partition as the root device in GRUB and install GRUB to MBR in your first hard disk.
```
sudo grub
``````
find /grub/menu.lst
``````
root (hd0,3)
```> [FONT=Bitstream Vera Sans Mono]setup (hd0)[/FONT]> [FONT=Bitstream Vera Sans Mono]quit[/FONT] That's it, all finished, you should be able to reboot and remove the Ubuntu Live CD and boot into your hard disk installed Ubuntu operating system.

Regards, Herman :)

---

### Post by charbilas on 2008-04-14
Hello and thanks for all the information
Actually I put another hardrive as primary slave where I reinstalled ubuntu and everything works fine
I'll do what you said and see what happens
Sorry but I'm very new to linux

---

### Post by Herman on 2008-04-14
That's okay, as long as you have Ubuntu working and you're happy then I'm happy too, no matter how you did it. :)

Happy Ubuntuing,
Regards, Herman :)

---

### Post by RobbieCrash on 2008-04-15
I'm having quite a bit of difficulty getting this all set up.

I've got a new system which is currently set up as follows:

IDE0 HDA
IDE2 HDB
SCSI (SATA) 0 SDB
PCI IDE card 0 CDROM
PCI IDE card 1 SDA

On SDA partitions are as follows:

0 = /
1 = /var
2 = /usr
3 = /home
4 = /tmp
5 = swap

My motherboard's BIOS does not have the IDE card's drive listed in it's drive table, but does allow it to be a selected device in the boot order. Currently I have it set as the first HDD to boot from.

I'm trying to install server 7.10

The install sees all the disks fine, and Grub comes up, then goes off to Error 17.

After booting into a 8.04 live CD and mounting /dev/sda1 to /ubuntu and then chroot'ing to /ubuntu I've edited my device.map, but grub is apparently not a valid program. I'm assuming that this is probably because I don't have var on the same partition as root?

Would it make more sense to install everything onto one partition and then move it off to separate partitions as needed, after the fact? Or am I totally wrong about what's causing the issue?

To add to problems, I'm adding further hard drives to the problem in the next week or two, to get this actually running as a file server. Everything is going to be RAID 0, my motherboard supplies hardware RAID, the IDE card relies on software, so switching the IDE card drives to the motherboard is not an option.

I'm unable to run fdisk -ul, again I'm thinking probably because /var is on a different partition? 

What other information do you need? Or are there any other suggestions?

---

### Post by Herman on 2008-04-15
Well I'd say try this,

Boot your computer to your GRUB menu.
Press your 'c' key from your GRUB menu to switch into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

If your computer doesn't have a GRUB menu on boot-up then download a copy of [Super Grub Disk]("http://sgd.benjamin-butschko.de/")
 and burn it to CD or make a floppy disk or USB device, depending on what kind of Super Grub Disk file you choose.
Boot the computer with Super Grub Disk, and after the first one or two menus, press your 'c' key to switch into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

After the grub> prompt:
1. type a test command to learn where GRUB detects your linux kernel, 
```
find /vmlinuz
```2. Then you need to use the output from the above command as the input for the following command,
```
root (hdx,y)
```Where: (hdx,y) is the output from the 'find /vmlinuz' command, above, replace the 'x' with a hard drive number and the 'y' with a partition number.
Remember, GRUB starts counting from zero. 

3. Type a test command to find out where GRUB detects your /sbin/init,
```
find /sbin/init
``` 
4. Now use the output from the above command for the input after the 'root=/dev/?d??' part in the command below, you can use the table in the following link to help you convert from GRUB's (hdx.y) type of numbering system to Linux's '/dev/?d??' style of numbering,  [Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")
Remember, GRUB starts counting from zero, but Linux starts counting with one. 
```
kernel   /vmlinuz   root=/dev/?d??
```Where: '/dev/?d??' is the linux equivalent of the hard drive and partition number given in GRUB notation as the output from the 'find /sbin/init' command. 

5. Issue the initrd command,
```
initrd    /initrd.img
```
6. Issue the boot command,
```
boot
```Your computer should boot, and when it has booted, edit your /boot/grub/menu.lst with the same partition numbers you just used to boot with.

Regards, Herman :)

---

### Post by jespdj on 2008-04-15
I haven't read all the 26 pages of this topic, but I've also had a random GRUB error 17 or 18 a few times on my desktop PC.

In my case, it looks like the cause was the SATA cable with which my harddisk is connected to the motherboard. After disconnecting and reconnecting the cable, and laying it out differently in the case of the computer, the GRUB errors went away.

It looks like the cable wasn't inserted properly or there was maybe interference because the cable was too close to some electronic component. Strangely I never had any disk errors in Windows or Ubuntu, I only had GRUB errors.

---

### Post by ryseshan on 2008-04-16
I have both xp and Ubuntu 7.10 in same hard disk wkhich is 160 GB IDE.   Windows XP using 20 GB as NTFS partion.  Rest as Unix 127 GB as Unix and 1.8 GB as Swap.  Now Unix partion is visible and can be done anything from live cd but the File-system is gone how to get back the File-system without disturbing the data.

As per previous messages when i try to mount it is asking the filesystem.  from windows showing unknown filesystem.

After Error 17.  I am foreced to rebuild the Windows for the recovery. Now grub error is not appearing also.

---

### Post by Herman on 2008-04-17
:) Hello ryseshan,
GRUB error 17 can be causd by a damaged file system in Ubuntu.
Windows will never be able to 'see' Linux, (unless you install specail drivers), so don't worry about that.

To repair your ext3 file system for Ubuntu, you can boot a Ubuntu Live CD and open a terminal and run 'sudo fdsik -lu' or look at your partitions with GParted (Gnome Partition Editor) to see what the partition numbers are.

Maybe for example, you will find out that Windows is in partition number /dev/hda1, and Ubuntu is in /dev/hda2, and probably swap is /dev/hda5.

From your Ubuntu live CD, if you have the ext3 file system in Ubuntu like most of us, you would run,
```
sudo e2fsck -C0 -f -p -v /dev/hda2
```
Where: /dev/hda2 is your Ubuntu partition

That will fix most problems in your ext3 file system without losing any files. 
You can run that command as often as you like, it will always be good for the file system and won't hurt it.
That command will almost always be enough to fix your file system.
If it can't fix your file system it will tell you and it will also give you more information about what other comand you can run next.

If your file system is has a problem that the above command can't fix, then it might tell you to run e2fsck without the -a or the -p options.
You should back up your data first if you still can.
Then you might run another command, but this command might move some of your files to the /lost+found directory, where you will require a little more knowledge to get them back, and some may not be fully useable again. You might use a command like this,
```
sudo e2fsck -y - f -v /dev/hda2
```
After that if you are lucky, you will have most of your files back and your system will work okay. If you are not lucky, you might need to re-install Ubuntu, but at least you can recover almost all of your files now.

If the output from the first command says it cant find a valid ext2 or ext3 superblock, then you can normally fix your file system without losing any files.
There are lost of spare copies of the superblock in an ext3 file system, for a list, use this command, 
```
sudo dumpe2fs /dev/hda2 | grep -i superblock
```
Then you can use a command like this to restore your superblock from a backup,
 ```
sudo e2fsck -b 32768 /dev/hda2
```
Where '32768' is a sector number of a backup copy of your ext3 superblock from the output of the previous command.

I hope that helps you, ryseshan, and I hope your problem is easy to fix.

Regards, Herman :)

---

### Post by artirana on 2008-04-19
_**from the neighbourhood**_..... :)

Hi, 
trying to copy all the files from a storage hard drive(with file system FAT32 with no OS) 20g to the master 80g (file system ext3 with Debian only installed), wanted to remove physically the 20g from the system. did use the code: 

dd if=/dev/hdb1 of=/dev/hda1 

start working.... and then 15 minutes later the screen turn black and you can see only the pointer of the mouse. 

shooted down, and reboot....right a way got an error: 

Grub... 
Error 17 

Is this fixable or I have to re install debian ?? 

Thanks

---

### Post by Herman on 2008-04-19
I'm not sure, but try booting up a Live CD and running a file system check on it it you haven't done so already,
```
sudo e2fsck -C0 -p -v -f /dev/hda1
```

Regards, Herman :)

---

### Post by unutbu on 2008-04-19
I'm sorry, artirana, the answer is not pleasant.

The 'dd' command copies data bit-for-bit, overwriting anything else which might have been stored on /dev/hda1. It is not like 'cp' which copies files into free space.

If your /dev/hda drive had Debian only installed, /dev/hda1 probably was used for either the '/' root partition or '/boot' partition (though I'm not familiar with Debian).
Unfortunately, this probably means important system files got overwritten.

15 minutes is long enough for dd to overwrite a lot. I'm guessing on the order of  gigabytes. The semi-good news is no more than 20gb could have been overwritten on your 80gb drive, so there might be salvagable data left on the 80gb drive.

What you need is a way to recover the old filesystem structure. That information is held in superblocks. 

The first thing you want to do if you want to recover as much data as possible is to make a complete backup image of the drive as it now stands. That means 
hooking up an external hard drive with >80gb, or something equivalent, and
dd'ing the entire /dev/hda1 onto another partition. Then you do all your recovery work from either the copy or the original. I know this sounds daunting and impractical, but this is technically the best way. It depends on how serious you are about recovering your data.

Next, you have at least two options:

First, you might want to try TestDisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
I've never used it, but it looks promising, and is probably written by someone who knows a heck of a lot more about recovery than I do.

The second option is one that I've had personal experience with. I've managed to salvage some data from a partition I borked by doing, essentially, the following:

Boot from a rescue disk like a Live CD, and type

```
dumpe2fs /dev/hda1 | grep -i superblock
```

The output hopefully will look something like

Primary superblock at 0, Group descriptors at 1-1
Backup superblock at 32768, Group descriptors at 32769-32769
Backup superblock at 98304, Group descriptors at 98305-98305
Backup superblock at 163840, Group descriptors at 163841-163841
Backup superblock at 229376, Group descriptors at 229377-229377
Backup superblock at 294912, Group descriptors at 294913-294913

(See [http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html)
for more on superblocks)

Then you can run
fsck -b <superblock> /dev/hda1

where you replace <superblock> with the superblock number you found above (e.g. 32768, 98304, 163840, 229376, etc.)

fsck will try to recover the old filesystem using the old superblock whose location you provided. 

Best wishes and good luck.

---

### Post by Herman on 2008-04-19
Yes, I think unutbu is probably right.

Try Photorec too, if you need it, that's another program that comes with TestDisk and it's for 'file carving', (recovering files from your hard disk even if you can't restore the partition or the file system).

The Ubuntu Rescue Remix CD has a lot of useful programs in it, if you don't mind working from the command line. [URL="http://ubuntu-rescue-remix.org/"]http://ubuntu-rescue-remix.org/
[/URL]

---

### Post by artirana on 2008-04-19
Yes, is gone...... but were no important data there, so I gess I will start from scratch again...:(
Good exaple though.
Thank you guys, really appriciate your time.

PS
Did try the superblock....

[FONT="Century Gothic"][SIZE="2"]$ dumpe2fs /dev/hda1 | grep -i superblock
dumpe2fs 1.40-WIP (14-Nov-2006)
dumpe2fs: Permission denied while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
$[/SIZE][/FONT]

---

### Post by unutbu on 2008-04-19
Hm, maybe it should have been
```
sudo dumpe2fs /dev/hda1 | grep -i superblock
```

---

### Post by DD_Malenfant on 2008-04-20
I had the same error: "error 17: disk cannot be mounted" and tried everything these forums had offered. well after doing the terminal thing with root (hd0,0), setup (hd0), and quit and nothing was working. I just started messing around with it seeing what I could learn.

How I fixed my error 17 was when I got to the promt to decide which os to start, I pressed "e" on the on ubuntu, then came up with another promt with root being one of the choices, press "e" on that as well and I seen the root set as (hd0,1) instead of hd(0,0), so I pressed "e", corrected it and now my system healthy again and I am happy.

Quick directions:
OS prompt ->select OS-> press "e" -> select root -> press "e" -> IF YOUR (hd#,#) does not match what you are supposed to start from, press "e" and correct it.

---

### Post by jmw86069 on 2008-04-20
BTW I had the GRUB error 17 just yesterday... noob mistake but still, we're all noobs at one point.

My issue, I was trying to install from USB, which by the way uses ISOLINUX as its boot loader instead of GRUB. (The GRUB error should've tipped me off.) But for some reason, a certain commandline tutorial didn't include the switch to overwrite any pre-existing MBR. (I updated that page.)

So I had GRUB there, it didn't get its boot loader overwritten, I then put ISOLINUX files onto the USB drive, and it broke. I.e. GRUB stage 1 in the MBR tried to find GRUB stage 1.5 outside the MBR and it could not. Thus GRUB Error 17.

If you have this situation, specifically trying to use SYSLINUX or some variant (ISOLINUX, etc.) then make sure to include the switch for the MBR: -m

If you don't, sorry I couldn't help. :-) But it may be a clue, and a relatively simple thing to try perhaps?

There's a Wiki topic describing the [Ubuntu boot process]("https://wiki.ubuntu.com/Booting"), specifically the section on Finding the Kernel and initrd. I also found some love from this topic on [Customizing an Install CD]("https://help.ubuntu.com/community/InstallCDCustomization").

---

### Post by van_Zeller on 2008-04-24
Hello everyone

Same problem here. I read pretty much all the info on this thread, and i'm sure my problem is simple to fix. That said, I have tried some times and still can't do it on my own, somehow. So here goes:

```
fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67bcabbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    32772599    16386268+   7  HPFS/NTFS
/dev/sda2        32772600    48966119     8096760   83  Linux
/dev/sda3        48966120   486383939   218708910    7  HPFS/NTFS
/dev/sda4       486383940   488392064     1004062+  82  Linux swap / Solaris

```

Bottom of the menu.lst (after some desperate messing around)

```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d8c9ca11-3bc1-47e4-99d7-97df64b7f4e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d8c9ca11-3bc1-47e4-99d7-97df64b7f4e2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

The smaller ntfs partition is for WinXP and the larger one is for the documents. The computer is a new hp pavillion with a single 250GB sata drive which should be healthy.

Hope you can help me and thanks

van_Zeller

---

### Post by unutbu on 2008-04-25
In the output of fdisk -lu, note the Linux partition is /dev/sda2.
The 2 in 'sda2' indicates that Linux is on the second partition, and the a indicates its on the first harddrive. 

```

/dev/sda2        32772600    48966119     8096760   83  Linux

```

In GRUB's terminology, /dev/sda2 is (hd0,1). 
The 0 in (hd0,1) indicates the first hard drive, and the 1 in (hd0,1) indicates the second partition.
The weirdness exists because GRUB starts counting with 0, while /dev/sda* startings counting with 1.

So as a start, you should edit your menu.lst, changing all occurrences of (hd0,2) to (hd0,1), and the (hd0,1) to (hd0,0).

---

### Post by van_Zeller on 2008-04-25
hi unubtu, thanks for the help
I tried what you said, but I'm still getting the same error 17 message!

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67bcabbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    32772599    16386268+   7  HPFS/NTFS
/dev/sda2        32772600    48966119     8096760   83  Linux
/dev/sda3        48966120   486383939   218708910    7  HPFS/NTFS
/dev/sda4       486383940   488392064     1004062+  82  Linux swap / Solaris

```

Heres the full menu.lst

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d8c9ca11-3bc1-47e4-99d7-97df64b7f4e2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d8c9ca11-3bc1-47e4-99d7-97df64b7f4e2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d8c9ca11-3bc1-47e4-99d7-97df64b7f4e2 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```I wasn't worried before, but now I am maybe a little......

---

### Post by Herman on 2008-04-25
Try running a file system check, it looks like everything else is right now.

Boot your Ubuntu Live CD and run,
```
sudo e2fsck -C0 -p -v -f /dev/sda2
```That won't hurt it and might fix it, error 17 has quite often been cured by running a file system check, especially when it looks like there's nothing else wrong.

Regards, Herman :)

---

### Post by kgriff on 2008-04-26
I also had an issue Grub error 17.  Here was my solution:  Simple, relatively quick, and it has worked twice now, on two different systems.

On both systems I have an SATA drive that I am installing Linux on.  On both systems I also have an IDE drive that will be used only for data backup.  Upon installing Ubuntu 8.04, I got Grub Error 17 on the first reboot.  I shut the system down, unplugged the IDE drive, and reinstalled Ubuntu.  Grub worked perfectly.  After booting into Ubuntu once to make sure Grub was functioning, I shut down again, and plugged the IDE drive back in.  Grub is still good.

---

### Post by caedeskhan on 2008-04-26
I'm having a bit of an issue with GRUB and error code 17 right now. My notebook has two hard drives (my first hard drive has Vista and an HP recovery partition), and Ubuntu is installed on the second one. There was also one regular data storage partition, D:, on that second drive, along with some unallocated space. I created a new partition in that unallocated space yesterday (H:..about 20 GB), and when I booted up this morning, I get this error. I was luckily able to boot using the Ubuntu CD (obviously). 

Hopefully this is a simple problem, and I'd greatly appreciate the assistance. 

Here is what I got when I ran ubuntu@ubuntu:~$ sudo fdisk -lu:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   295097984   147548961    7  HPFS/NTFS
/dev/sda2       295097985   312576704     8739360    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x722e2d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   156264254    78132096    7  HPFS/NTFS
/dev/sdb2       156264255   271610954    57673350   83  Linux
/dev/sdb3       271611904   312578047    20483072    7  HPFS/NTFS


Thanks in advance!

---

### Post by Herman on 2008-04-26
Hello caedeskhan,

:) I'm only guessing, but it seems to me likely that whatever hard disk partitioning software you used to create your new partition H: took it upon itself to tidy things up for you and re-arrange your hard drive numbers for some reason. 
Probably you just need to edit your /boot/grub/menu.lst now, with the current correct partition number for Ubuntu and Ubuntu will boot normally again.

You can use your Ubuntu Live CD to gain access to your /boot/grub/menu.lst file in your hard drive installed Ubuntu system, you just need to mount it first.
With your Ubuntu Live CD booted up,
```
sudo mkdir /media/ubuntu
```
```
sudo mount -t ext3 /dev/sdb2 /media/ubuntu
```
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```
sdb2 = (hd1,1) in GRUB's numbering scheme, check and see if your Ubuntu boot stanza in your /boot/grub/menu.lst has 'root (hd1,1)' in it or not, and if not then edit it to that and save the changes before closing the file.
If that doesn't seem to be your problem, (maybe I guessed wrong), or if you need more specific help, then please copy the bottom half of the menu.lst file and post it here and I or someone here will take a look at it for you and help you with it.

By the way, I also notice that you don't have any swap area. Maybe you don't need one because your computer has lots of RAM? 
Did you know that it's possible to make a swap file inside Ubuntu if you want, rather than having a swap partition? If you're interested I'll find out how to do that for you, it might make Ubuntu a little faster for you. Or maybe it'll make no difference, I'm not sure.

Regards, Herman :)

---

### Post by unutbu on 2008-04-26
Edit: I would listen to Herman; he knows more than I do.

I am just a novice myself, so it would be good if you read the documentation ([http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html) and [http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html))
and/or independently confirm the correctness of these commands:


From the Live CD, open a terminal and run
```

sudo grub
```

Then at the grub prompt,

```
grub> root (hd1,1)
```

If you have grub installed on the primary hard drive, then type

```
grub> setup (hd0)
```

If you have grub installed on the secondary drive, type

```
grub> setup (hd1)
grub> quit

```

Reboot.

---

### Post by caedeskhan on 2008-04-26
Hey guys,

Unfortunately, neither of those worked. The root did need to be changed to (hd1,1).  I had used Vista's computer management to create the new partition. Thanks for all the help so far though.

Here is the code: 


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4c33ab2-128a-428f-a2ae-a02ca7a512c1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4c33ab2-128a-428f-a2ae-a02ca7a512c1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1




And when it comes to the swap space, I have 4 GB of ram, so that should be plenty.

---

### Post by caedeskhan on 2008-04-26
I just fixed MBR and deleted Ubuntu :( ...thanks for all the help though.

---

### Post by ma3cs on 2008-04-27
HEllo people ...

change on bios ahci mode for serial ata .. 

I make this and surprise ... grub run ... and kubuntu start but now is problems with windows ... must reinstall windows in ahci mode.

Try this [http://forums.pcper.com/showthread.php?t=444831]("http://forums.pcper.com/showthread.php?t=444831") maybe work for you !!!

---

### Post by AeroGT3 on 2008-04-27
[COLOR="Red"]This is an easy fix!!!![/COLOR]

Just go into the BIOS and change your hard driver order! MUCH easier than booting back and forth and editing confusing GRUB files.

Cheers,

---

### Post by ma3cs on 2008-04-28
change what ?

Kubuntu use sata ahci mode when detect sata hardware. By default windows not use ahci mode ... 
Of course ...change ahci for linux and change back setting for windows ... 
Not so nice solution but work ....

---

### Post by bratsche on 2008-04-30
First, I want to thank you Hermann, because it seems like you have helped many, many people with boot/GRUB errors. Your grub page is very useful, too. So thank you!

Second, yeah, I'm in a pickle too. Previously, GRUB would drop to the command prompt upon boot, so now that I see the menu and Error 17, I feel like I'm at least moving in the right direction. However, I'm not exactly sure what my menu.lst should look like. Here's my fdisk -l output

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48c848c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5722    45961933+   7  HPFS/NTFS
/dev/sda3           14087       14593     4072477+   5  Extended
/dev/sda4            5723       14086    67183830   83  Linux
/dev/sda5           14227       14593     2947896   82  Linux swap / Solaris
/dev/sda6           14087       14226     1124487   82  Linux swap / Solaris
```

and here is my menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST 
```

What should be my proper course of action? I realize I need to change the root settings in the menu.lst, but I also noticed that my UUID numbers are missing. Thanks so much in advance.

---

### Post by unutbu on 2008-04-30
bratsche, please post

```
ls -l /dev/disk/by-uuid/
```

---

### Post by bratsche on 2008-04-30
here it is. thanks, unutbu:

```
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-04-30 16:29 3A6C10046C0FBA21 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-30 16:29 64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-04-30 16:29 6aa2587b-c3dd-4e0b-b493-4a74364f4b47 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-04-30 16:29 772520cf-8946-648e-48e3-e288c8081cba -> ../../sda5

```

---

### Post by yamawho on 2008-04-30
> **AeroGT3 said:**
> [COLOR="Red"]This is an easy fix!!!![/COLOR]

Just go into the BIOS and change your hard driver order! MUCH easier than booting back and forth and editing confusing GRUB files.

Cheers,

I kind of did this my unplugging both hdd's then connecting the ubuntu hdd first, booted, then shutdown and attached the XP hdd.

Next time I'll try changing the boot order 1st  :)

---

### Post by unutbu on 2008-04-30
bratsche, copy your menu.lst just to be safe. 
Then save the following as your new menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,3)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,3)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Reboot. I don't know if this will completely solve your problem, but it should move you a step closer.

---

### Post by TheDro on 2008-04-30
YAY My system is once again bootable! Thanks for the link on the bigpond site. I've been using it for a while because it has some pretty good instructions for most things. 

What I had to do in my case was:
sudo grub
root (hd0,4)
setup (hd0)
I guess the installation disk didn't do it properly or I totally didn't give it the right instructions because I'm running grub on a dedicated grub partition.

Anyways, thanks for the links to the errors page.

---

### Post by bratsche on 2008-05-01
Thanks for the file, ununbt. I'm happy to report that it booted *once.* After that, I started updating my system, and had to reboot. Then, another GRUB error ocurred. If I selected the latest kernel to boot, Error 18 ("Invalid or unsupported executable format") was shown, and if I selected the older kernel, it told me Error 15: File not found.

Would it be possible to use a LiveCD, chroot into the system, and reinstall the kernel? Or would there be a better course of action?

Thanks again for your help.

---

### Post by unutbu on 2008-05-01
bratsche, I'm not sure why that's happened.
Could you please boot from Live CD, mount /dev/sda4, chroot to wherever you mounted /dev/sda4, and then post

```
ls -la /boot
cat /boot/grub/menu.lst

```

---

### Post by bratsche on 2008-05-01
```
root@ubuntu:/# ls -la /boot
total 16096
drwxr-xr-x  3 root root    4096 2008-05-01 07:21 .
drwxr-xr-x 23 root root    4096 2008-04-30 21:31 ..
-rw-r--r--  1 root root  422436 2008-04-08 00:01 abi-2.6.24-15-generic
-rw-r--r--  1 root root   85193 2008-04-08 00:01 config-2.6.24-15-generic
drwxr-xr-x  2 root root    4096 2008-04-30 21:31 grub
-rw-r--r--  1 root root 2554973 2008-02-13 10:14 initrd.img-2.6.22-12-generic
-rw-r--r--  1 root root 2901991 2008-05-01 07:21 initrd.img-2.6.24-15-generic
-rw-r--r--  1 root root 7532391 2008-04-05 01:46 initrd.img-2.6.24-15-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  904178 2008-04-08 00:01 System.map-2.6.24-15-generic
-rw-r--r--  1 root root 1911128 2008-04-08 00:01 vmlinuz-2.6.24-15-generic
```

and

```
root@ubuntu:/# cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,3)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I don't know if this has anything to do with it, but if I try and update the system via apt or dpkg, they both abort with errors. It seems there are many packages left configured. Here's the output:

```

root@ubuntu:/# apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@ubuntu:/# dpkg --configure -a
Setting up linux-image-2.6.24-15-generic (2.6.24-15.27) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing linux-image-2.6.24-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libldap-2.4-2 (2.4.7-6ubuntu3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libldap-2.4-2 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of cupsys:
 cupsys depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing cupsys (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.8.2-0ubuntu8); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of seahorse:
 seahorse depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing seahorse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2-4:
 libgconf2-4 depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing libgconf2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 2.22.1); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 evolution-data-server depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-cups-utils:
 hal-cups-utils depends on cupsys; however:
  Package cupsys is not configured yet.
dpkg: error processing hal-cups-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-open-terminal:
 nautilus-open-terminal depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing nautilus-open-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2.0-cil:
 libgconf2.0-cil depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libgconf2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mousetweaks:
 mousetweaks depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 mousetweaks depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing mousetweaks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 gnome-control-center depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gnome-control-center depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-control-center depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on gnome-mount; however:
  Package gnome-mount is not configured yet.
 gnome-volume-manager depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 libedataserverui1.2-8 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cups depends on cupsys; however:
  Package cupsys is not configured yet.
dpkg: error processing bluez-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdata1.2-1:
 libgdata1.2-1 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libgdata1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserver1.2-9:
 libedataserver1.2-9 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libedataserver1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-11:
 libcamel1.2-11 depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
 libcamel1.2-11 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libcamel1.2-11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-exchange depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 evolution-exchange depends on libecal1.2-7 (>= 2.22.1); however:
  Package libecal1.2-7 is not configured yet.
 evolution-exchange depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
 evolution-exchange depends on libedataserverui1.2-8 (>= 2.22.1); however:
  Package libedataserverui1.2-8 is not configured yet.
 evolution-exchange depends on libexchange-storage1.2-3 (>= 2.22.1); however:
  Package libexchange-storage1.2-3 is not configured yet.
 evolution-exchange depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 evolution-exchange depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs:
 gvfs depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gvfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-plugins depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 evolution-plugins depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
 evolution-plugins depends on libedataserverui1.2-8 (>= 2.22.1); however:
  Package libedataserverui1.2-8 is not configured yet.
 evolution-plugins depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on seahorse; however:
  Package seahorse is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdata-google1.2-1:
 libgdata-google1.2-1 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libgdata-google1.2-1 depends on libgdata1.2-1 (>= 2.22.1); however:
  Package libgdata1.2-1 is not configured yet.
dpkg: error processing libgdata-google1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 libedata-book1.2-2 depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
 libedata-book1.2-2 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-binfilter:
 openoffice.org-filter-binfilter depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-filter-binfilter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-data-server (>= 2.21.92); however:
  Package evolution-data-server is not configured yet.
 evolution depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 evolution depends on libecal1.2-7 (>= 2.22.1); however:
  Package libecal1.2-7 is not configured yet.
 evolution depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
 evolution depends on libedataserverui1.2-8 (>= 2.22.1); however:
  Package libedataserverui1.2-8 is not configured yet.
 evolution depends on libexchange-storage1.2-3 (>= 2.22.1); however:
  Package libexchange-storage1.2-3 is not configured yet.
 evolution depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 evolution depends on libldap-2.4-2 (>= 2.4.7); however:
  Package libldap-2.4-2 is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of notification-daemon:
 notification-daemon depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing notification-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-tools:
 gnome-system-tools depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gnome-system-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libecal1.2-7 (>= 2.22.1); however:
  Package libecal1.2-7 is not configured yet.
 libedata-cal1.2-6 depends on libedataserver1.2-9 (>= 2.22.1); however:
  Package libedataserver1.2-9 is not configured yet.
 libedata-cal1.2-6 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-common:
 totem-common depends on gconf2 (>= 2.10.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing totem-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.4.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.4.0-3ubuntu6); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted

```

---

### Post by unutbu on 2008-05-01
Notice:

```
-rw-r--r--  1 root root 2901991 2008-05-01 07:21 initrd.img-2.6.24-15-generic
-rw-r--r--  1 root root 7532391 2008-04-05 01:46 initrd.img-2.6.24-15-generic.bak
```

It looks like a new initrd.img-2.6.24-15-generic was being written, but was interrupted. (Its size is much smaller than initrd.img-2.6.24-15-generic.bak).

I would try the following:
Boot from Live CD, chroot to the system, then

```
cd /boot
cp initrd.img-2.6.24-15-generic initrd.img-2.6.24-15-generic-probably-broken
cp initrd.img-2.6.24-15-generic.bak initrd.img-2.6.24-15-generic
```

If this works for a week, then you can go back and delete initrd.img-2.6.24-15-generic-probably-broken.

---

### Post by unutbu on 2008-05-01
You don't have the file /boot/vmlinuz-2.6.24-12-generic. This is why you got the "File does not exist" error when asking GRUB to boot the older kernel.

You can delete these stanzas from menu.lst since they are useless:
```

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=64c13a25-8bd5-43aa-9007-12a4d8d9f0d8 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

```
Also, you might as well delete initrd.img-2.6.22-12-generic because you don't have the vmlinuz file that goes along with it.

Here is the safe way to delete these things:

```
sudo mkdir /tobedeleted
sudo mv /boot/initrd.img-2.6.22-12-generic /tobedeleted
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst

```
Then erase the two stanzas mentioned above. Save, reboot. 
If rebooting works fine for a week (with some of reboots), then you can remove the contents of /tobedeleted.

---

### Post by bratsche on 2008-05-01
After instituting the backup vmlinuz file, I still receive the Error 18 message - I'm wondering if it's corrupted somehow.

---

### Post by c-boy on 2008-05-06
Major credit to ma3cs for discovering the AHCI issue. This is what solved the problem for me. Even worked (knock on wood) to get the drivers in Vista to avoid BSOD but my AHCI enabled Win system is 5 minutes old so it's too soon to say anything for certain.

Is there any information on this weird issue of Grub? It seems Grub cannot find the disk unless AHCI is enabled. I didn't experience this with Gutsy...

---

### Post by togoshigekata on 2008-05-06
I had Grub Error 17 after installing: 
Ubuntu on a second hard drive
with Windows Vista already on the first.

After a few days frustration and searching I fixed it.

I manually restored grub while on the live Ubuntu CD
using the second tutorial in the first post of this link:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

After reboot I got Error 17 booting Ubuntu and Error 13 booting Vista
I went into Bios and switched the order of the hard drives remembering
reading a post by Herman.

Everything works now, thanks guys :biggrin:

---

### Post by mvashi on 2008-05-12
I did get the Error 17 too
I have on hd 1 -- Win XP and Hd 2 has Hardy

So after I get the error 17 I inserted live cd in the cd tray and rebooted
and on a whim I selected boot from first hard disk 
lo and behold I got the boot menu 
Selected Win XP 
Booted up fine into Win Xp
restarted the pc with Live CD and selected 
boot from first hard disk 
This time I selected Ubuntu 
that too loaded up fine 
restarted the pc again after removing the live cd
got the boot menu and here I am writing this post after logging on to Ubuntu
I am going to reboot again and check if it boots into Windows

---

### Post by mvashi on 2008-05-12
Well , I could boot into XP
Don't know what happened but booting from live cd and then selecting Boot from first hard disk seems to have resolved the issue

---

### Post by chandu_aka_sarath on 2008-05-17
i m new to linux and i also got this error 17. i have only a single harddisk which is 250 gb with sata interface and i got this problem in a weird way. i installed ubuntu n it was working fine, i installed d recent updates for my ubuntu 8.04 yesterday n when i restarted i booted xp 32 bit edition. in that i recovered my 14gb c drive which was allocated for my 64 bit xp. it was earlier a 50gb hard disk n due to weird installation done by my sister :( it got chopped to 14 and would not boot. and worse still was tat i could not see it in my xp even though it was in ntfs format. so i formatted d drive after saving data from it in ubuntu. and when i restart i have this error 17. can i kno what caused it and what is d solution

---

### Post by chandu_aka_sarath on 2008-05-17
this is how my harddisk details are
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x138f138f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    28386854    14193396    7  HPFS/NTFS
/dev/sda2   *    28386855   130785164    51199155    7  HPFS/NTFS
/dev/sda3       130785165   488375999   178795417+   f  W95 Ext'd (LBA)
/dev/sda5       130785228   233183474    51199123+   7  HPFS/NTFS
/dev/sda6       233183538   264478094    15647278+   7  HPFS/NTFS
/dev/sda7       264478158   332561564    34041703+  83  Linux
/dev/sda8       332561628   335581784     1510078+  82  Linux swap / Solaris
/dev/sda9       335581848   411360389    37889271    7  HPFS/NTFS
/dev/sda10      411360453   488375999    38507773+   7  HPFS/NTFS

---

### Post by Herman on 2008-05-17
> i m new to linux and i also got this error 17. i have only a single harddisk which is 250 gb with sata interface:) Okay, I can understand you up to here.
 > and i got this problem in a weird way. i installed ubuntu n it was working fine, i installed d recent updates for my ubuntu 8.04 yesterday n when i restarted i booted xp 32 bit edition.:) Yes, good.
 > in that i recovered my 14gb c drive which was allocated for my 64 bit xp. it was earlier a 50gb hard disk n due to weird installation done by my sister :sad: it got chopped to 14 and would not boot. and worse still was tat i could not see it in my xp even though it was in ntfs format. so i formatted d drive after saving data from it in ubuntu. and when i restart i have this error 17. can i kno what caused it and what is d solution:confused: I'm sorry, but the last part doesn't make very much sense, I can't understand what you are trying so tell me. 

Please explain the last part again in plain English, and using proper spelling (if English is your first language), so that I can understand you better.

Thank you for the fdisk output, I can understand that.

What partition numbers have Windows installed in them and which ones are just data partitions?
(When you say 'C' drive and 'D' drive, it means nothing to me at all).

---

### Post by chandu_aka_sarath on 2008-05-18
sorry for that english. too much of messaging. anyway, my sda1 is the drive which had the 64bit win-xp installed on it. sda2 is the drive which had xp32 bit installed on it. sda7 is my linux partition. what else do u want me to explain?

---

### Post by meierfra. on 2008-05-18
Boot from a Ubuntu Live CD. Open a terminal and type

```
sudo grub
```

at the "grub>" prompt:

```
root (hd0,6)

setup (hd0)

quit
```

You might also have the edit "menu.lst":
mount your ubuntu partion and open "menu.lst"

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda7 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst
```


Look for 

#groot (hd0,?)

change it to

#groot (hd0,6)

Next look for all ubuntu entries:

title ubuntu.....
root (hd0,?)

again change "root (hd0,?)"

to 

root (hd0,6)


Look for the windows entry:


title Windows ...
root (hd0,?)

change it  "root (hd0,?)" to

root (hd0,1)


Of course if some of the root staements are already correct you will not have to change them. Save the file and reboot.

---

### Post by raymondvillain on 2008-05-23
> **AmericanYellow said:**
> After installing Ubuntu on my hard drive( dual booting with Windows XP) I got the Grub 1.5  Error 17 message. Spent 2 days pulling my hair out trying to figure out why I got the error. Browsed the Ubuntu forums, saw good advice, but nothing help. I was just about to give up on Ubuntu, until I just started messing around with my PC and surprisingly :) :) :) :guitar:  the error was gone! Here's what I did:


1. Enter BIOS
2. Make sure all HDD's are detected.

* *Take note of (write down) the current settings just in case you need to set things back later**

3. Search for the HDD that has Ubuntu installed and set its MODE to AUTO (not LBA, large, or normal)
4. Also, if you have this option available, set TYPE to USER, but don't change any of the figures that were automatically detected.
5. And you are done!


Just in case this doesn't work, then:
6. Set all drives to TYPE --> USER and MODE --> AUTO (not LBA, large or normal)


I just took the time to post this because of the all the trouble I when through for something so simple to do. I hope that this post helps.....
Thanks so much!  I was going crazy, until I tried your fix.  IT WORKED!

---

### Post by The MAX on 2008-05-24
Hi all,
New to linux and as well am getting this dreadful error, but only when I restart in Ubuntu, not when I cold boot, or restart in XP.
I have a 250GB seagate with a 35 GB Ubuntu partition. Have tried to edit my menu.lst file and a couple of other things in this forum but am having no luck.
Here is my menu.lst, maybe you can see something I can't, after all I am a linux noob.
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8fd4c246-c841-430f-8734-915fab9db312 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
rootnoverify		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8fd4c246-c841-430f-8734-915fab9db312 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
rootnoverify		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8fd4c246-c841-430f-8734-915fab9db312 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
rootnoverify		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
rootnoverify


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1

```

If there is anymore info you need from me just ask. I'd appreciate any help you guys can give.

Thanks

---

### Post by The MAX on 2008-05-24
I tried to delete the linux partitions and install again. 
This time I went through the official install guide and I think I changed a few things...

now I get an error 18!!!
anyways... any help when you get a chance...

---

### Post by unutbu on 2008-05-24
According to [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) error 18 means:
> 18 : Selected cylinder exceeds maximum supported by BIOS


BIOS hands off control to the MBR (Master Boot Record). I think the error means your MBR is too far down on the hard drive for the BIOS to access.

Do you know on what partition you installed GRUB?
It would also help us if you post the output to
```

sudo fdisk -l

```

---

### Post by The MAX on 2008-05-24
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cf71cf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       29508    32226390    5  Extended
/dev/sda5           25497       29143    29294496   83  Linux
/dev/sda6           29144       29508     2931831   82  Linux swap / Solaris
hughie@Laplace:~$ 


```

I installed the boot loader on the default area hd0 I believe.
This only happened when I attempted to reinstall ubuntu, before that I was getting error 17. I tried again this time saying beginning instead of end of the drive for the partitions and still getting error 18.

Any other info you need just ask.
And thanks.

---

### Post by unutbu on 2008-05-24
According to [http://www.gnu.org/software/grub/manual/grub.html#rootnoverify](http://www.gnu.org/software/grub/manual/grub.html#rootnoverify)  rootnoverify is

> Similar to root (see root), but don't attempt to mount the partition.

It seems to me that mounting the partition is what we want. Try editing menu.lst, changing the 'rootnoverify's to simply 'root'.

---

### Post by The MAX on 2008-05-24
it was originally root, and I was getting the same problem.

I changed it to rootnoverify in accordance with this site from herman
[http://users.bigpond.net.au/hermanzone/p15.htm#17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

---

### Post by Herman on 2008-05-24
:) Hello The MAX,
> it was originally root, and I was getting the same problem. I changed it to rootnoverify in accordance with this site from herman [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17) 'rootnoverify' is only needed for Windows with the NTFS file system, you will probably be better off just using 'root' in your menu.lst stanzas for booting Ubuntu. ( I agree with unutbu).
 > I tried again this time saying beginning instead of end of the drive for the partitions and still getting error 18. That was a good idea, and I would have expected that to have fixed it. GRUB error 18 is normally caused by having the Linux kernel located too far out in the hard disk for the BIOS to 'see' it. Installing Ubuntu close to the start of the disk should have fixed that. For some computers the BIOS hard drive limit is 8 1/2 GB, and for others it's 33.8 GB, and some have the 137 GB BIOS hard drive limit.
How old is your computer? 
Can you try to find out the BIOS details, such as the BIOS manufacturer and BIOS date?
In some PCs you might see that in your monitor as the computer boots, press your 'Pause/Break' key to hold it until you have time to read, or enter your BIOS and get your BIOS [product information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information") for there somewhere.

While in the BIOS, make sure your hard disk is detected and set up properly in the BIOS, for example, you might try putting the hard disk detection on auto rather than on user if that might be the problem.

Depending on your BIOS date, it might be advisable for you to try re-installing again with a separate /boot partition, or you can [make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition") without re-installing, but it is a bit more work.

You might also need to check your hard drive and CD/DVDcables and jumper settings too if it's a PATA disk.

Here's my link on [Grub error 18]("http://users.bigpond.net.au/hermanzone/p15.htm#18") and here's my [Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17") link too, where I have been collecting information on those boot errors in case anything there might help.

Regards, Herman :)

---

### Post by unutbu on 2008-05-24
I could be wrong about this, but I believe rootnoverify is sometimes helpful for booting windows, but I don't believe it is useful for booting linux.

Please read [http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18). Search for 'Error 18' and read as much as you can.

These are quotes from Herman's page:

1) > BEFORE YOU DO ANYTHING, check your computer's BIOS date and settings in case your BIOS can be updated instead.

According to your fdisk output, your linux partition starts at cylinder 25497. That is about 210GB into your hard disk. I think you are getting the GRUB error 18 because your BIOS can not access hard drive addresses that far down. 

2) > "I had the same problem. Error 18 and After GRUB. The solution is in the bios.
Put the hard disk detection on auto and not on user. It did the trick for me."

I don't know what auto and user mean, but this seems like a relatively easy thing to try...

3) > Make sure LBA is enabled in your BIOS. If LBA is already enabled, try switching to 'normal' mode and see if that helps.

Also, seems relatively easy to try.

4) > Making a separate /boot partition would probably still be the best answer even with a relatively modern computer if you think you might have the 137 GB hard drive limit.

The /boot partition should be put before your big HPFS/NTFS partition. That bad news about that is left end point of a partition is (I hear) a very slow operation. But if you can't upgrade your BIOS or use the other BIOS settings above, this seems to be the best way.

See [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by The MAX on 2008-05-24
Okay changed rootnoverify back to root, extcept in the windows section, also changed harddrive mod from auto to large to no effect. Didn't know if thats what you guys suggested or not by the LBA thing.

My Bios is from 2005, thats all I got from the boot screen and didn't see a product info in the bios screen.
[Here is my MoBo]("http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=1928")
it has a new bios from 2006. Should I update it? Thats something else I have to learn how to do...oh boy.

So I should create another partition for mounting to /boot?
so total I'll have my
NTFS
/boot
/
and swap 
partitions?

Also I don't know how to put anything before my ntfs partition. How can I do that if windows is already installed there?
Also how big should /boot be?
Thanks guys for taking the time to help me. I'm going to see if I can get any more info on the bios and try to update it. I don't think that will help but it might. If not I'm hoping I can have some clarification on this /boot partition so I can try another reinstall.

Thanks again.

---

### Post by The MAX on 2008-05-24
It appears the "edit" function on this forum is giving me grief...sigh no luck today.
So had to change the windows back to root and hdd mode back to auto. One of those gave me a problem going back into windows. 
So More info...
bios is 07/27/05 dated. Going to try to upgrade that and see what happens. with any luck it will help the issue, if not I'm hoping we'll try the reinstall.
Thanks again.

---

### Post by Herman on 2008-05-24
Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)

Since your BIOS is much newer than any of those dates, I don't think that would be likely to be your problem.

---

### Post by The MAX on 2008-05-25
Okay then. Well I guess I'll leave the bios be as it seems to be risky sometimes if not done right.

So I'll try a reinstall with this 4th partition mounted to /boot.
So like I said I have a 200GB XP install and a 30GB Ubuntu install and I was using 3GB for swap. I Can put swap to 2GB as I only currently have 1GB of ram. So Would a gb or two be okay for this /boot partition. And should it be the partition right after xp?

If you can give me any more advice about what specifically to change before I reinstall I'd be greatful, not that I'm not already! :)

---

### Post by Herman on 2008-05-25
[> Here is my MoBo]("http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=1928")
:) Wahoo, nice hardware!

I was just reading that link a little and I saw this part,
> The NVIDIA RAID allows multi-disk designs to be set up as RAID 0,1,0+1 based on users’ priority of protection/ performance. This NVIDIA RAID function makes the RAID even more accessible by introducing the innovative windows-based facility.
Now, that might have something to do with it.
Are you using RAID right now and are you given a choice? I don't know very much about RAID except that there are lots of different kinds of either software or hardware RAID, so there would be a lot of studying involved probably. It is possible to boot a RAID array with GRUB, but I think you need to know a few extra tricks.

---

### Post by The MAX on 2008-05-25
Oops we posted around the same time. lol

Thanks, its a couple of years old. Plan on buying a new setup soon actually.
I only have a single drive and as far as I know no raid setup what-so-ever.
But I'll check the bios again to make sure there are no raid issues.

---

### Post by Herman on 2008-05-25
There must be some other problem here but I'm not sure exactly what it might be yet. :confused:

Maybe a good way to troubleshoot your problem would be to try downloading and burning [Super Grub Disk Official]("http://www.supergrubdisk.org/")  and try booting with that and see if it helps.

Another thing about Super Grub Disk is you can always press your 'c' key, (as you can from any GRUB), and get into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), which is very useful for testing commands and solving booting problems, because usually it gives us some feedback.
I have to go for a while but I'll be back.
Try some of the tricks in that last link and see if anything helps.

Regards, Herman :)

---

### Post by The MAX on 2008-05-25
I burned the CDROM iso to a dvd and it just went straight to error 18 again. I don't have a floppy.
I was thinking of doing the auto windows sgd or the usb, but its 2am here and I've been doing this all day. Tired now. lol

Well, I'll have to get some rest and try again tomorrow.
Thanks for all you're help, hopefully I'll get this figured out soon.

---

### Post by Herman on 2008-05-25
Okay, (I'm back), and I have Super Grub Disk 0.9711 on a DVD-RW here.
I chose 'Choose Language & Help', and then 'English Super Grub Disk', and 'Gnu/Linux', and 'Boot Gnu/Linux Directly'.
After confirming that, I selected 'SCSI' for my hard disk type, and my operating system to boot once for the 'root file system', again for the vmlinuz kernel, and again for the initrd.img file I want to boot with.  (Don't worry, just select your operating three times if you aren't sure what I mean).
That should cause Ubuntu to boot.

Another way to do exactly the same thing, is to press your 'c' key from a GRUB menu in Super Grub Disk. It's slower and more laborious, but also more informative.
You should then have a black screen with a grub>_ prompt.

After the grub prompt, tyoe,
```
find /vmlinuz
```You should see some output on your monitor after you press your 'enter' key, it should look like this, 
```
(hd0,1)
```Whatever it says, write that down. That's your hard disk and partition number for your /boot partition, in GRUB terms.

Next, after the grub prompt, tyoe,
```
find /initrd.img
```You should see some output on your monitor after you press your 'enter' key, it should something look like this, 
```
(hd0,1)
```Whatever it says, write that down. That will be your /root partition, and unless you have a separate /boot, it should be the same partition number as above.
Now, for the /root partition, you will need to be able to convert that to Linux notation, here's a  [Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System") to help you convert. Write that down somewhere.
Normally it would be /dev/sda2, I would guess, but that's probably wrong or else your Ubuntu would probably be booting by now.

Okay, so now you have all the information you need to boot Ubuntu directly with GRUB.
So, you do,
```
root (hd0,1)
``` Where: '(hd0,1)' was the answer you recieved for where your kernel is,  the /boot partition.
```
kernel /vmlinuz root=/dev/sda2
```Where /dev/sda2 is the Linux equivalent of the answer you got after GRUB found your initrd.img for you, (your /root partition).
```
initrd /initrd.img
``````
boot
```A tip you can use to make it easier when you are typing GARUB commands is, you only need to type the first two or three letters and then press your 'tab' key and much of the time, GRUB is smart enough to guess what you're going to type next, and will either complete the word for you, or give you a list of suggestions. (That's called 'Tab completion', and it's a very handy feature). :)

Well, by now if your Ubuntu is going to boot, you will have it running.

If that didn't boot Ubuntu for you, maybe you will have some observations, feedback or error messages that will give valuable cluse as to what's wrong or where to look next.

One other thing that can cause GRUB error 17 would be if your Ubuntu partition needs a file system check. That seems unlikely to me, since you have even re-installed already and still have the same problem, but it's worth a try anyway and won't do any harm, only some good. From a Linux Live CD,
```
sudo e2fsck -C0 -p -f -v /dev/sda2
```Where" /dev/sda2 is your Ubuntu partition, if not, please replace '/dev/sda2' with whatever partition number yours happens to be.

Your hard disk is SATA isn't it? So jumper settings and the type of cables and the way they're plugged in shouldn't be the cause of any problems.
I would take a look at the way your CD/DVD drive(s) is/are plugged in and jumpered, if you're still having trouble, and make sure there's no other disks plugged in, such as USB flash memory sticks or the like, just in case those could possibly be interfering, but I think that would be unlikely.

That's all for now, see what happens up to here.

Regards, Herman :)

---

### Post by The MAX on 2008-05-25
Okay here it goes...
So the first part you suggested about going to 'Boot Gnu/Linux Directly' that worked fine. If I can't boot and get the Error, thats only when I WAS in Linux and RESTART (not shutdown) my system, then I get the error. If my computer is off and I turn it on I get no problems (until I restart while in lunix).

So I did the second part you suggested while I had REBOOTED from Linux. Then I got this
```
grub> find /vmlinuz
Error 15: File not found

grub>find /initrd.img
error 15: file not found
```

I then totally turned off my system, and turned it back on again did the same thing and got

```
grub> find /vmlinuz
(hd0,4)
grub> find /initrd.img
(hd0,4)
```
but that info was in my fdisk already I think.

Maybe this sheds some light on the situation, only when I'm in Linux and then 'Restart', only then can it not find my linux to boot from...strange
I'm downloading the Live CD now and will give that a shot.

---

### Post by unutbu on 2008-05-25
The fact that you are only having problems after a reboot and not a poweroff/poweron must be a clue.

Something that happens after the machine is powered on must be changing something basic about your hard drive which is not being reset to its correct state until the machine is powered off. 

Could the **savedefault** line in your menu.lst be doing this? Perhaps try deleting it. I'm rather skeptical about my own suggestion, but since it is easy to try and easy to revert, I'm suggesting it anyway.

---

### Post by The MAX on 2008-05-25
Okay I've got some serious issues.
Tried all of this and nothing worked.
Now my computer hangs at start up for some reason sometimes and It takes a couple of minutes to even get my Bios main screen if I get it at all.
When I boot into linux normally my login screen is a really weird resolution even though when I boot in it goes to 1600x1200 which I set it at. When I unplugged my DVDROM and booted into linux my startup screen was at my normal 1600x1200 resolution but it didn't fix the error 18 problem!!!
I'm thinking of just uninstalling linux and windows and trying everything again...but if I uninstall ubuntu isn't there some problem with grub being gone and not being able to get into windows?
How should I do this? Uninstall windows first then Uninstall Ubuntu (and Grub) then start from scratch with my XP cd?

I'm so frustrated with this I'm real close to giving up on ubuntu all together...But I really like using it, when it works...

Ugh if anyone has suggestions I'm open to anything to help this.

---

### Post by Herman on 2008-05-26
> I'm thinking of just uninstalling linux and windows and trying everything again...but if I uninstall ubuntu isn't there some problem with grub being gone and not being able to get into windows?
How should I do this? Uninstall windows first then Uninstall Ubuntu (and Grub) then start from scratch with my XP cd? Here's a link that explains lots of different ways to change your MBR back to boot Windows again. [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
That's about all you will probably need to do. You can delete Ubuntu anytime with a hard disk partitioner, but I would wait and see what happens first. It will be interesting to  see if Windows will still boot okay. I'm not sure, but it's beginning to seem as if you might have some hardware problem. Re-installing Windows boot loader to MBR and trying it to see if it works might be a good test.

---

### Post by meierfra. on 2008-05-26
herman: I suggest do add "ms-sys" to your Uninstall page.

  ms-sys is very easy to use
```

sudo apt-get install my-sys
sudo ms-sys -m  /dev/sda
```
of course /dev/sda needs to replaced by the actual location of the MBR in question.

Also ms-sys is not in the Hardy repositories. So Hardy user have to download the  i386 version of the debian package [http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys") and double click (or right-click) the icon to install ms-sys.

---

### Post by Herman on 2008-05-26
:) Done! Thank you meierfra, here is the new link, [Replace GRUB in MBR with ms-sys]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Replace_GRUB_in_MBR_with_ms-sys").

Regards, Herman :)

---

### Post by thewhiteraven on 2008-05-28
Hello, I haven't been following the whole thread cos, well, it's 33 pages long! :) Anyway, I tried mbwardle's solution and it was ok till I got to this point:

> **mbwardle said:**
> 

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"

Here, it says "No such file or directory"

What do I do? I'm an absolute beginner! help!

---

### Post by unutbu on 2008-05-28
Hello thewhiteraven, mbwardle's method is meant for a rather special problem -- when a machine has more than one hard drive and the BIOS detects them in a different order than Linux. Is this your situation?

When you were following mbwardle's steps, did you type
```
mount /dev/scd1 /ubuntu
```
? This line in particular is very specialized -- it will only work if your Linux root partition happens to be on the third hard drive's first partition (scd1). 
Given the error you received, "No such file or directory", it was probably this step that failed. 

Please do the following:
Boot from the LiveCD. 
Open a terminal, and type:
```
sudo fdisk -l
```
Post the output.

Also please tell us more about what problems you are having. When you try to boot normally, what do you see? Do you see the BIOS screen? Then do you see some output from GRUB? Does it say Error 17? or some other error?

---

### Post by The MAX on 2008-05-28
> **meierfra. said:**
> herman: I suggest do add "ms-sys" to your Uninstall page.

  ms-sys is very easy to use
```

sudo apt-get install my-sys
sudo ms-sys -m  /dev/sda
```
of course /dev/sda needs to replaced by the actual location of the MBR in question.

Also ms-sys is not in the Hardy repositories. So Hardy user have to download the  i386 version of the debian package [http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys") and double click (or right-click) the icon to install ms-sys.

So what will this do? Should I do this without uninstalling linux to see if my comp will dual boot with ms-sys? Or is this something else...
I'm so confused.

---

### Post by meierfra. on 2008-05-28
> So what will this do? 

It is just one of the many ways to put Windows back in charge of the MBR.

>  Should I do this without uninstalling linux to see if my comp will dual boot with ms-sys?  

No, it is only useful if you want to uninstall Linux.
But you can  test it before you uninstall Linux and see whether you can boot into Windows without problems.

---

### Post by The MAX on 2008-05-28
so...I used gparted to shrink my windows partition to 60 gigs and delete linux, then installed a 40 gig ubuntu partition. It worked fine, no more errors...until when i went to go create another ntfs partition for an extra windows drive, i realized that my bios was now only recognizing my harddrive as a 130gb as opposed to 250 gb.
what the hell?

anyone have any ideas on this, I can't believe I'm running into this much trouble just to freaking dual boot.

Help is appreciated. Thanks.

---

### Post by Herman on 2008-05-28
Aha! It sounds like your BIOS probably has the 137 GB or 268,435,455 LBAs limitation (28-bit limit), overcome in most computers since September 2001.

You should read this, [Grub error 18]("http://users.bigpond.net.au/hermanzone/p15.htm#18"). and see if anything there will help you.

Maybe you will find some BIOS setting that you can apply to enable your BIOS to 'see' your whole hard disk, or else maybe there's an update for your motherboard's BIOS at the manufacturer's website that you can download and use.

EDIT: So we've gone around in a full circle and we're back to what unutbu already said back in post  			#[**312 **]("http://ubuntuforums.org/showpost.php?p=5036046&postcount=312")  :)
[]("http://ubuntuforums.org/showpost.php?p=5036046&postcount=312")

---

### Post by The MAX on 2008-05-28
I've had the computer for almost 3 years now, and its had a 250gb hdd all that time without a bios upgrade. I used gparted and all of a sudden its 136gb.
Looked at bios and couldn't find anything to hepl...working on it with roomate.

---

### Post by blegs38552 on 2008-05-28
I tried every suggestion that I could find without success. Finally, I was forced to do a full reinstall of Vista. Following this, I reinstalled Ubuntu and so far all is well. The good news is that I always keep my data on a separate partition and back up critical Windows data files that are stored on my C:\ drive (such as my Outlook PST file), so I did not lose any data, just a lot of time. At a minimum, if you are going to play with dual booting, create a data partition and use it, and perofrm frequent backups of your Windows system.

---

### Post by Herman on 2008-05-29
> I've had the computer for almost 3 years now, and its had a 250gb hdd all that time without a bios upgrade. I used gparted and all of a sudden its 136gb.
Looked at bios and couldn't find anything to hepl...working on it with roomate.:) Yes, but you probably just had Windows in it, and as far as I know Windows just installs itself starting at the beginning of the hard disk and fills up the partition from the outside track, working its way inwards.  I don't think there are new kernels for Windows given in updates, and that's probably the only reason you haven't encountered any problems thus far.

Now you're trying to do something completely different, install another operating system, and it happens to be Ubuntu. Linux operating systems don't just concentrate all their files at the start of their partition, but arrange them in clusters evenly spread out all over the partition, like bunches of grapes on a vine. The kernel might happen to end up within the BIOS accessible area or it might not. Definitely not if the entire partition is outside the BIOS accessible area.

GParted hasn't done anything to your hard disk, if you take a look at your hard disk with GParted, or Gnome Partition Editor, it would still tell you 250 GB. It's just that your BIOS apperently can't handle the mapping for a hard disk that large. The hard disk is divided up something like a map, into squares makred off by imaginary lines. On a map you could describe your position as co-ordinates of latitude and longitude. In a hard disk, your BIOS addresses locations on a hard disk by either the sector number, or by cylinders, tracks and sectors. Only your BIOS doesn't seem to have the ability to count high enough to understand the position of a kernel in a hard disk larger than 137 GB.

It's kind of like the map of the world before Christopher Columbus 'discovered' America. They used to think the Earth was flat right? Your BIOS thinks your hard disk is only 137 GB because that's as far as it has the ability to address or 'map' to. It's no good telling it to look past there for a Linux kernel to load. It's like trying to tell someone to go to America when they still thought the Earth was flat, it will be 'off the map'.  The kernel may be there alright, but your boot loader needs to be able to tell your Bios the exact location of your kernel. It can't describe the exact location to your BIOS because your BIOS's can't handle those co-ordinates.

Once you have an operating system booted though, the operating systems should be able to see your entire hard disk okay, and use it all. 
Probably you just need a separate /boot partition for Ubuntu somewhere within the first 137 GB of the hard disk, and you can let Ubuntu have some space near the end of the hard disk and it will boot okay. Windows can have the rest. It's just a matter of forcing the Linux kernel to be located where the BIOS can understand it's location. Once the Linux kernel is loaded, the Linux kernel will have the right drivers to use the rest of your hard disk, so it won't matter what the BIOS can or can't address. :)

---

### Post by Herman on 2008-05-29
> I tried every suggestion that I could find without success. Finally, I was forced to do a full reinstall of Vista. Following this, I reinstalled Ubuntu and so far all is well. The good news is that I always keep my data on a separate partition and back up critical Windows data files that are stored on my C:\ drive (such as my Outlook PST file), so I did not lose any data, just a lot of time. At a minimum, if you are going to play with dual booting, create a data partition and use it, and perofrm frequent backups of your Windows system. I agree, everyone should always make regular backups of their important files in any case, whether you are installing an operating system or not.
It's particularly important to make a fresh backup before using any hard disk partitioning software.
You should make a backup to some other media, not just to another partition in the same hard disk, in case the partition table gets destroyed somehow. You can restore it with TestDisk these days, but why take the risk?
Neither Ubuntu nor GRUB touch your Windows installation at all, so there should never be any need to re-install Windows because of a GRUB problem. 
Boot loader problems very rarely require re-installation of an operating system, normally they can be solved in a few minutes if you know what you are doing or get the right help.

---

### Post by thewhiteraven on 2008-05-29
> **unutbu said:**
> Hello thewhiteraven, mbwardle's method is meant for a rather special problem -- when a machine has more than one hard drive and the BIOS detects them in a different order than Linux. Is this your situation?

Yes, I think this is my problem. I have one hard drive with 4 partitions and an external hard drive. However, I store only data in the second drive, it's got nothing to do with the OS.

> When you were following mbwardle's steps, did you type
```
mount /dev/scd1 /ubuntu
```
? This line in particular is very specialized -- it will only work if your Linux root partition happens to be on the third hard drive's first partition (scd1).


No, I typed ```
mount /dev/sda2 /ubuntu
``` which is the root partition. Actually I just tried it again and it says that I need to enter a type of file system. So I tried ```
mount -t ext3 /dev/sda2 /ubuntu
``` and it says "Wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper programs, or other error."

> Please do the following:
Boot from the LiveCD. 
Open a terminal, and type:
```
sudo fdisk -l
```
Post the output. 

Here it is:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 53 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a431a3

     Device Boot    Start    End    Blocks   Id    System
/dev/sda1               1   2502  22097283+   b    W95 FAT32
/dev/sda2            2503   3747  10000462+  83    Linux
/dev/sda3            3748   3808    489982+  82    Linux swap / Solaris
/dev/sda4            3809  19457 125700592+   b    W95 FAT32

```

> Also please tell us more about what problems you are having. When you try to boot normally, what do you see? Do you see the BIOS screen? Then do you see some output from GRUB? Does it say Error 17? or some other error?

It loads as usual until the GRUB screen comes up. It says

```
GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 17
```

I'm not dual booting with Windows, Ubuntu is my only OS... So what am I doing wrong?:confused:

---

### Post by MichaelMay1976 on 2008-05-29
HELP HELP HELP

When I boot up the laptop I am getting a Grub Error 17.

Let me tell you how i got there:

I originally tried to install Ubuntu. (  Half way through the install, I stopped the install because I thought it was done.

Then I tried to re-install windows from the factory cd I received from the manufacturer.  Half way through the reinstall the computer receives an error and aborts the reinstall.

When I try to boot the computer I get a Grub 17 error.  I have tried numerous times to reinstall but no luck.  I have searched the web for how to correct the issue but again….no luck.

Right now I cannot get Ubuntu or Windows to install due to the Grub 17 error.


Do you have any suggestions on how to correct this?

---

### Post by unutbu on 2008-05-29
> **thewhiteraven said:**
> I tried ```
mount -t ext3 /dev/sda2 /ubuntu
``` and it says "Wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper programs, or other error."


This is often a sign that there is some corruption of the filesystem. Let's try to clean that up. Boot the LiveCD, open a terminal and type

```

sudo e2fsck -C0 -p -f -v  /dev/sda2
```
Hopefully it will find some errors and fix them.

---

### Post by thewhiteraven on 2008-05-29
Ok thanks! :) 

But this is what it says now:

```
e2fsck: Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Hmm... I'm tempted to just go ahead and reinstall ubuntu! :)

---

### Post by unutbu on 2008-05-29
Okay, if there is nothing on /dev/sda2 that you don't mind losing, reinstalling is probably the easiest solution.

---

### Post by thewhiteraven on 2008-05-29
Thanks unutbu!

---

### Post by unutbu on 2008-05-29
MichaelMay1976, I would use GParted to delete the partitions you were using for Ubuntu and Windows and then try reinstalling. To run GParted, first boot your computer using the LiveCD. Then click on the gnome panel menu at the top of the screen: System>Administration>Partition Editor.

For great instructions on creating a dual-boot machine, go to Herman's website: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by The MAX on 2008-05-29
> GParted hasn't done anything to your hard disk, if you take a look at your hard disk with GParted, or Gnome Partition Editor, it would still tell you 250 GB. It's just that your BIOS apperently can't handle the mapping for a hard disk that large.

I'm sorry Herman, while I appreciate the help, thats incorrect. While I am a noob to linux I've been tinkering with hardware and windows and bios stuff for long time.
My bios previously detected my drive as roughly 230gb (its a 250 drive) as did windows and gparted the first time I ran it.
After running gparted, my bios only detects my drive as 136gb, as does gparted. I deleted everything off the drive, wiped all partitions,its still 136.
Took the drive to my roomates computer which has 2 x 500GB drives and a 320GB drive and it recognized my drive as 136GB, in his bios, windows, and multiple partitioner software. 

It appears to have put the drive into 28bit read mode, instead of 48bit which clips it at 136gb. The only problem is nvidia chipsets seem to have a problem forcing a drive back into 48bit mode. Going to a friends house tonight (has a different chipset) to try it out.

I for one will not be using gparted ever again. My bios as well as everything else on  my computer recognized my hdd correctly until until I ran gparted.

---

### Post by Herman on 2008-05-30
:) I don't think GParted writes to the firmware in your hard disk at all. I don't imagine it would even have capability to do that. GParted is a program for modifying the partition table in your hard disk's MBR.
Chances are, you have some kind of a hardware problem or firmware problem that has happened to occur or become apparent at around the same time as you used GParted by co-incidence, so it seems to you as if GParted has something to do with your problem.
Unpredictable failures like electronic and mechanical problems in firmware can occur quickly, for example a tiny manufacturing defect or a brief power surge can cause chip or circuit failure.

I'm very sorry to read that you are having this much trouble. Please keep posting and let me know what else you find out and how you get along, I'm very interested and curious know more.  I'm certainly wishing you all the best with it in the meantime. 

Regards, Herman :)

---

### Post by The MAX on 2008-05-30
Thanks man, not trying to come off harsh or anything just getting frustrated with all the bad luck I've been having. Even used Seatools, a dos boot program that is used for disk utilities. Tried setting it to max native ammount and it fails, but it does recognize that its supposed to be bigger than it is.
Called Seagate tech support and they were usless, telling me to check My Computer to see if the C drive showed up...lol.
So I just made an RMA for it cause its still under warranty and I also orderd a 500 GB Seagate 7200.11 with a 32mb cache from ncix.com. When That gets here I'll ship off the 250 to seagate and hopefully get a new one out of it.
In the meantime, I have a 30GB Ubuntu Installed on it to get me by and its working fine, and I'm slowly getting used to it.
the future plans is to have the 500GB for XP and the 250 for Linux.

BTW, when I shutdown ubuntu and my computer powers off, my LED keyboard still has its lights on...have to unplug and discharge the capictors in order for it to go off...any known  fixes? (I guess I should start asking these questions in other threads lol.)

---

### Post by meierfra. on 2008-05-30
Edit:  I realized that my post doesn't really fit under "Grub Error 17". So I moved it [ here]("http://ubuntuforums.org/showthread.php?p=5082723#post5082723")

---

### Post by hal8000 on 2008-05-31
After deleting some partitions on my IDE hard drive I also arrived at grub error 17.
Booting was not possible I could use the Hardy 8.04 CD in live mode but when I attempted to setup grub, it could not see my IDE hard drive, only my SATA ??

My installation was multi boot, before I addede Ubuntu and I think one reason for grub not seeing the drive may be a slightly different grub version.

I also have Suse 10.3 on DVD which acts as a rescue system (although theres absolutely no reason the following commands should not work from the Ubuntu Live Cd).
The Suse Live CD creates a small ramdisk and no partitions are mounted, this is important. Heres my solution:
Start grub
(sudo grub) from the live cd, you'll arrive at a grub shell:
grub >

Use the grub find command to list all grub stage 1 entries:

find /boot/grub/stage1

My results were
hd  (0,5)
hd  (0,10)
hd  (1,4)
hd  (1,6)

each of these places are installed linux root partitions, so you can choose
any OS to control grub; just edit the corresponding menu.lst in the appropriate partition.
My choice was (hd0,10) thats /dev/hda11 in my case.

If, like me you have moved partitions then you will need to edit menu.lst so that the entries reflect the new locations of the file systems
mkdir tmp1
mount /dev/hdx tmp1

(above is for mounting an IDE, where x is partition number (add 1 to grub notation). If the drive is SATA then it will be /dev/sdx ( where x is partition number).
After modifying menu.lst and the root file system is still mounted, you will have to modify /etc/fstab to tell the OS where to mount its new / and /home partitions (or any partitions in the filesystem table)

Next step is to tell grub where to find the menu.lst file, this is (hd0,10)
command is

root (hd0,10)

finally to set grub in the mbr

setup (hd0)

If all goes well you will see confirmation of the stage1 and stage2
loaders:

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,10)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

Reboot and everything should be well again.
Hope this may help soomeone.

---

### Post by Don in the Mountains on 2008-06-13
While waiting to resolve a reinstall issue on a Toshiba laptop I installed UMBUTU. After resolving the problem I wiped out the UMBUTU partitions but found that I couldn't boot. Got the Grub 17 error.

After searching this thread I saw mentioned using the DOS command, "FDISK /MBR". It worked.

What I wanted to add was that I found an FDISK command on the installation disk that came with the laptop. When reinstalling the system I noticed that it was copying from drive "Q:". I searched "Q:" and found in the directory "bin" was "FDISK". When the disk booted it said to press "F1" to install, "F2" if not. Pressing "F2" left me with a command prompt at "A:". Running the "Q:\bin\fdisk /mbr" fixed the problem.

---

### Post by rampokker on 2008-06-17
Thanks for the help, changing my HDD boot priority worked for me =D

---

### Post by richtea on 2008-06-18
Hi,

I am getting grub error 17 after updating my Hardy install last night.

My fdisk entry is:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4743145f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d74dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    19535039     9767488+  83  Linux
/dev/sdb2        19535040   308592584   144528772+  83  Linux
/dev/sdb3       308592585   312576704     1992060   82  Linux swap / Solaris

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec3ec430

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   117210239    58605088+   7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb259b259

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   268430084   134215011    7  HPFS/NTFS


Menu.lst is:

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b18641c5-f24d-44a3-a160-c38d36f08131 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet


Device.map is:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

From fdisk, I can tell you my root partition is /dev/sdb1.

Can someone please advise on how I should progress from here to repair grub 

Cheers in advance!

---

### Post by unutbu on 2008-06-18
Try changing (hd3,0) to (hd1,0).

(hd3,0) is the first partition of the fourth HD (/dev/sdd1).

(hd1,0) is the first partition of the second HD (/dev/sdb1).

---

### Post by richtea on 2008-06-18
> **unutbu said:**
> Try changing (hd3,0) to (hd1,0).

(hd3,0) is the first partition of the fourth HD (/dev/sdd1).

(hd1,0) is the first partition of the second HD (/dev/sdb1).

Excuse my probably obvious question, do you mean change in device.map?

So it would something like:

(hd0) /dev/sda
(hd1) /dev/sdd
(hd2) /dev/sdc
(hd3) /dev/sdb

Is that correct?

---

### Post by unutbu on 2008-06-18
Oops, sorry -- I should have been clearer.
I meant change all occurrences of (hd3,0) to (hd1,0)
in /boot/grub/menu.lst.

You can leave device.map in its original state.

---

### Post by richtea on 2008-06-18
Aha, it all makes sense to me now :) Thanks for that unutbu, will try out tonight, fingers crossed it works!

---

### Post by f1nn on 2008-07-12
hi all!

how about this?

last night I discovered a 100GB of my 320GB hard drive was unused. But I can't directly format it as there were already 4 primary partition, so I deleted an 80GB (data and mp3) partition and then combined them together to form 180GB partition. I didn't touched Hardy Heron's partition and the 8MB swap partition. This morning I turned on my PC and it showed GRUB Error 17 on Stage1.5.

there are lots of threads.. the Super Grub helped me to access my Windows XP and I backed up everything to my external drive.. and I can't find a particular match to my dillema to fix that GRUB.

any help?

---

### Post by unutbu on 2008-07-12
Perhaps try this: [http://ubuntuforums.org/showpost.php?p=5235963&postcount=2](http://ubuntuforums.org/showpost.php?p=5235963&postcount=2)

---

### Post by upchucky on 2008-07-12
f1nn


it found stage 1 but stage 2 is on the hardy mbr you saved, however it is written with the drive order in it before you changed your partitions around. you have now got a new drive order and need to tell stage 2  (menu.lst) of the mbr in the hardy partition you saved what this order is.

this means using advanced supergrub to find and repair the mbr, and editing menu.lst with the newly found drive order and parameters (hdo.0) ect:

---

### Post by evcamstrss on 2008-07-16
i havea presario 700 that runs XP sp1, and Ubuntu Hardy.  the grub is giving me probloms, and i dont know how to fix it.  i get error 17, but it doesnt say anything else.  whats wrong with my computor and how do i fix it?

---

### Post by unutbu on 2008-07-16
evcamstrss, please boot from the LiveCD, open a terminal and post the output of 

```
sudo fdisk -l
```
(the last part is a minus L (lowercase).)

---

### Post by jdash1 on 2008-07-17
hi everyone.
i hope someone can help.

1st PROBLEM: i had problem in the grub loader in ubuntu 8.04
error 17
found answers in ubuntuforumsin REINSTALLING it
i'm following this step [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
but

find /boot/grub/stage1 <- **when i try to execute this it**
it sees NONE
Checking if "/boot/grub/stage1" exists... none

i can't continue on with the step.

**and when i use the live cd**
and was planning to reinstall everything 
I always use Manual partitioning to avoid losing my windows information
PROBLEM is its ONLY SEEING **/dev/sda** ONLY


**but when i open terminal and execute fdisk -lu**

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     2099199     1048576   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     2099200   162995489    80448145    7  HPFS/NTFS
/dev/sda3       162981888   237890519    37454316    7  HPFS/NTFS
/dev/sda4       237890520   312576704    37343092+   f  W95 Ext'd (LBA)
/dev/sda5       237890583   247658039     4883728+  82  Linux swap / Solaris
/dev/sda6       247658103   247850819       96358+  83  Linux
/dev/sda7       247850883   273506624    12827871    b  W95 FAT32
/dev/sda8       273506688   312576704    19535008+  83  Linux


It sees it.:(

Help

-----------------------------------------------

I'm also following the first step here in this THREAD 

opened GRUB

but when i try to execute the 
ROOT (hd0,6)  its just giving me errors
i continue in executing the SETUP (hd0) command

so that's why i used another way to fix it.

---

### Post by unutbu on 2008-07-17
> **jdash1 said:**
> planning to reinstall everything 
I always use Manual partitioning to avoid losing my windows information
PROBLEM is its ONLY SEEING **/dev/sda** ONLY

I don't see anything necessarily wrong here. I think the installer was just asking you to select the hard drive on which you want it to install. The next screen should then ask you to select the partition into which you want to install.

> 
but when i try to execute the 
ROOT (hd0,6)  its just giving me errors

(hd0,6) is /dev/sda7, a Windows partition. 
(hd0,5) is /dev/sda6,
(hd0,7) is /dev/sda8. Which is your root partition?

Are you currently trying to reinstall Ubuntu, or are you trying to fix GRUB?

---

### Post by jdash1 on 2008-07-17
> **unutbu said:**
> I don't see anything necessarily wrong here. I think the installer was just asking you to select the hard drive on which you want it to install. The next screen should then ask you to select the partition into which you want to install.

coz everytime i reinstal the software manually i use to see all my partitions

/dev/sda1 2048 2099199 1048576 27 HPFS/NTFS
/dev/sda2 * 2099200 162995489 80448145 7 HPFS/NTFS
/dev/sda3 162981888 237890519 37454316 7 HPFS/NTFS
/dev/sda4 237890520 312576704 37343092+ f W95 Ext'd (LBA)
/dev/sda5 237890583 247658039 4883728+ 82 Linux swap / Solaris
/dev/sda6 247658103 247850819 96358+ 83 Linux
/dev/sda7 247850883 273506624 12827871 b W95 FAT32
/dev/sda8 273506688 312576704 19535008+ 83 Linux







> (hd0,6) is /dev/sda7, a Windows partition. 
(hd0,5) is /dev/sda6,
(hd0,7) is /dev/sda8. Which is your root partition?

Are you currently trying to reinstall Ubuntu, or are you trying to fix GRUB?



/dev/sda7 247850883 273506624 12827871 b W95 FAT32
/**dev/sda8 273506688 312576704 19535008+ 83 Linux ** <this is my root

I Ended up Reinstalling the whole OS for the reason that i USED PARTITION MAGIC8 in my Windows.



Device Boot Start End Blocks Id System
/dev/sda1 2048 2099199 1048576 27 Unknown
**Partition 1 does not end on cylinder boundary.**THIS WAS THE PROBLEM.
/dev/sda2 * 2099200 162995489 80448145 7 HPFS/NTFS
/dev/sda3 162981888 237890519 37454316 7 HPFS/NTFS
/dev/sda4 237890520 312576704 37343092+ f W95 Ext'd (LBA)
/dev/sda5 237890583 247658039 4883728+ 82 Linux swap / Solaris
/dev/sda6 247658103 247850819 96358+ 83 Linux
/dev/sda7 247850883 273506624 12827871 b W95 FAT32
/dev/sda8 273506688 312576704 19535008+ 83 Linux




Learned a lesson today :)

Thanks for the reply bro

---


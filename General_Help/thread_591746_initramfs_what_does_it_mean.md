---
title: "initramfs: what does it mean?"
date: 2007-10-25
forum: General Help
---

### Post by twbdan on 2007-10-25
initramfs, what does it mean, when ubuntu won't load and uou get this message?

---

### Post by ago on 2007-10-25
That something get wrong in the boot stage and you are thrown into a console

---

### Post by dadani on 2007-11-03
i have the same problem after I have installed Kubuntu 7.10 with wubi 7.10. I do this several times but it's at each time the same problem

that appears on my screen:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)_

what can I do?

Dani

---

### Post by antimatter15 on 2007-11-03
the same error is happening to me.

i think it means that ubuntu/wubi can't find the boot disk ?!?

---

### Post by ago on 2007-11-03
What version are you using and when exactly does it happen? First reboot after windows installation or second reboot after linux installation?

---

### Post by dadani on 2007-11-03
I tested it with all wubi 7.10 versions (every time the same error). And it happends after the kubuntu installation, when linux reboots the system.

thx

---

### Post by ago on 2007-11-03
> **dadani said:**
> I tested it with all wubi 7.10 versions (every time the same error). And it happends after the kubuntu installation, when linux reboots the system.

thx

when you boot, press esc when given the chance, then press 'e'. Edit the kernel line, remove "quiet splash" and add "debug". Then press enter and "b"

---

### Post by dadani on 2007-11-04
Now I get this:

(initramfs) [   24.872000] usb 4-1: new low speed USB device using uhci_hcd and address 3
[   25.048000] usb 4-1: configuration #1 chosen from 1 choice
[   25.064000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   25.064000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-1
[   25.348000] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00030d49530311f3]
[  317.708000] usb 4-1: USB disconnect, adress 3

then i test the same without a mouse:

this error
(initramfs) [   25.508000] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00030d49530311f3]

---

### Post by dadani on 2007-11-05
is that a problem of wubi or ubuntu 7.10 ?

---

### Post by ago on 2007-11-05
If you did as mentioned there should be a log under /  or /tmp or /var/log (don't remember the path on top of my head)

---

### Post by dadani on 2007-11-05
sry i am a linux starter i found this file called "initramfs.debug" now, what to do?

---

### Post by ago on 2007-11-05
Read using the commands "cat" or "more" and report any error. Errors will normally be at the bottom. You can scroll with shift+pgup

---

### Post by dadani on 2007-11-06
I think that's the right part:

....
+modeprobe -Qb vfat
+ mount -r -t vfat /dev/disk/by-uuid/ACOD-30D5 /root
mount: Mounting /dev/disk/by-uuid/AC0D-30D5 on/root failed: No such device
+ [ /ubuntu/disks/root.disk ]
+ mkdir -p /host
+ mount -o move /root /host
mount: Mounting /root on /host failed:Invalid argument
+ [! -e /host/ubuntu/disks/root.disk]
+ panic ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to shell!
+ [ -x /sbin/usplash_write]
+ /sbin/usplash_write QUIT
+ [  = 0 ]
+ modprobe -Qb i8042
+ modprobe -Qb atkbd
+ echi ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping a shell!
+ PS1=(initramfs)	/bin/sh -1

---

### Post by ago on 2007-11-06
That's the failing command:

mount -r -t vfat /dev/disk/by-uuid/ACOD-30D5 /root

You should look into /dev/disk/by-uuid and check whether device ACOD-30D5 does exist.
Note to self: might it be that devices by-uuid are not populated for FAT?

---

### Post by dadani on 2007-11-06
oh thx, i solved the problem, it's realy easy i take a FAT32 for my wubi installation, and no i fomate it and took NTFS and now it works great.

Do you now why it doesn't work with FAT?

---

### Post by ago on 2007-11-06
> **dadani said:**
> oh thx, i solved the problem, it's realy easy i take a FAT32 for my wubi installation, and no i fomate it and took NTFS and now it works great.

Do you now why it doesn't work with FAT?

Well no I was for you to give me some indications based on the commands above. I have no fat partition at all, guess I'll need to create one  sooner or later.

---

### Post by Bluemercury on 2008-03-03
Hi! im having this same problem, my wubi exe file is on a fat32 disk and the target installation is also on a fat32 partition.....any possible solutions?


regards,

---

### Post by ago on 2008-03-04
Please test it as indicated here: [http://ubuntuforums.org/showpost.php?p=4450651&postcount=20](http://ubuntuforums.org/showpost.php?p=4450651&postcount=20)

---

### Post by steve196 on 2008-03-04
I also have tried wubi on fat32 and i always got the busybox  not after installation but after the first time updating the kernel. And it was only with the new kernel. If i selected the old one it still worked. 

Maybe (i do not know) the others got the kernel update immediately, because i never had internet during installation, because i need to manually type a command to bring internet up.

Maybe the other weirdness (i aleays had to change "ro" to "rw" in menu.lst) also had to do with me using a fat32 partition.

---

### Post by ago on 2008-03-04
> **steve196 said:**
> I also have tried wubi on fat32 and i always got the busybox  not after installation but after the first time updating the kernel. And it was only with the new kernel. If i selected the old one it still worked. 

Maybe (i do not know) the others got the kernel update immediately, because i never had internet during installation, because i need to manually type a command to bring internet up.

Maybe the other weirdness (i aleays had to change "ro" to "rw" in menu.lst) also had to do with me using a fat32 partition.

I'd like to have precise info if possible, otherwise it is difficult for me to fix the issues.

Ideally once in busybox you should try to run the commands manually (in verbose mode) as indicated in the link above, and report what fails and what does not. Possibly including  /casper.log.

---

### Post by steve196 on 2008-03-06
I had deleted the wubi installation and now reinstalled and updated everything. After update, synaptic said:

E: linux-ubuntu-modules-2.6.24-11-generic: subprocess post-installation script returned error exit status 1
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

The Details said:
```
Processing triggers for initramfs-tools ...
ln: creating hard link `/boot/initrd.img-2.6.24-11-generic.dpkg-bak' => `/boot/initrd.img-2.6.24-11-generic': Operation not permitted
dpkg: subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.85eubuntu26) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-11-generic (2.6.24-11.15) ...
ln: creating hard link `/boot/initrd.img-2.6.24-11-generic.dpkg-bak' => `/boot/initrd.img-2.6.24-11-generic': Operation not permitted
dpkg: error processing linux-ubuntu-modules-2.6.24-11-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-11-generic; however:
  Package linux-ubuntu-modules-2.6.24-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.11.11); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...



```

I will reboot now, to run those mount commands and see what happens.

---

### Post by steve196 on 2008-03-06
The modprobe does not find the modules and mount does not find the fstab.

---

### Post by ago on 2008-03-06
Steve, ubuntu is installed under ntfs correct?

---

### Post by steve196 on 2008-03-06
No, it is a fat32 partition. But the system is NT (win2ksp4)

---

### Post by ago on 2008-03-06
Ok the issue has been nailed down. It will be fixed in coming releases

---

### Post by ago on 2008-03-07
> **ago said:**
> Ok the issue has been nailed down. It will be fixed in coming releases

That refers to problems araising when updating the kernel and as mentioned should be ok in coming ISOs (AFTER alpha6),

I am still no wiser about issues people reported about the inability to mount vfat partitions, which is a different problem.

I would appreciate some more info/help on that, by having users that end up in a busybox, try to manually mount their vfat partition

---

### Post by Irysche on 2008-03-08
I'm really green on Ubuntu.  I've used Linux and Unix before (somewhat), but I'm no expert.

I grabbed Wubi because I have hear great things about Ubuntu.

After I installed Wubi on Windows and rebooted, I got the option to boot into Vista or Ubuntu.  I select Ubuntu and got much further with this version (7.10) than I did with 7.04 which said "No RAID". I know I don't have RAID, this is a notebook!

Anyway, I thought I was making progress because I got a splash screen and progress bar, only to have my hopes dashed when it fell into busybody

I'm running this on an NTFS Partition.  I have only the distros that the program calls for.  I'm nearly ready to go for the 8.04 alpha to see if I have better luck.

I've see alot out here from Ago, but I'm hoping there is something easy.  I was hoping to be running this by now.

Cheers,
Irysche :confused:

---

### Post by ago on 2008-03-09
What version of 8.04 did you use? Can you type 

cat /casper.log 

and let me know about any error message (use shift+pgup to scroll)

---

### Post by Irysche on 2008-03-09
Hi Ago,

I was actually using Wubi 7.10, but I can download and try the latest build of Wubi 8.04 and give it a shot if that would help development along.

I'll try the same command in 7.10 and let you know what I come up with.  If nothing then I will try 8.04 and see if that get me any further.

From what I hear, this is going to be very cool!

---

### Post by ago on 2008-03-09
Please use 8.04 instead of 7.10

---

### Post by Irysche on 2008-03-09
OK.  I downloaded wubi 8.04 build 449 and installed it.

Since my E:/ drive has more space that I where I put it ( all previous installs were placed there as well).  E:/ in this case is a logical Windows partition on the primary disk.  It is setup as NTFS and I am an administrator on this machine with full rights to the disk and directory where this was installed.

If it helps I am running this on a Dell Latitude D620 running Vista Business with 2 GB of RAM.  I have 20 GB of free space on the drive that Wubi is installed on.  From what I have read space and RAM should not be an issue here.

I reboot after the installation and get the Ubuntu splash screen as I have in the past.  It seemed to take a little longer to fail into busybody, but it went there.

I ran cat /casper.log as you suggested.  Here is the out put (I have only put in the relevant messages as these repeat over and over)

[I]/scripts/casper-premount/30custom_installation: /scripts/casper-premount/30custom_installation: 92: cannot open /dev/scd0: No Medium
[/I]
At the end there is this repeating over and over:
*/init: /init: 1 : cannot open /dev/scd0: No Medium Found*

I only ran the install and then rebooted the machine when I was asked to do so.  Wubi must at least start the scripting.

My directory on Windows looks like this:
[I][U]E:\Ubuntu
\disks
   \boot
     \Grub
   \shared
  root.disk
  swap.disk
\docs
\install
  \boot
    \Grub
      menu.lst
    initrd.gz
    vmlinuz
  \custom-installation
    \hooks
      casper-premount.sh
      early-command.sh
      failure-command.sh
      success-command.sh
    \packages
    preseed.cfg
  hardy-desktop-i386.iso
  MD5SUMS
  MD5SUMS.asc
  unbuntu-desktop-i386.iso.metalink
\winboot
  menu.lst
  wubildr
  wubildr.exe
  wubildr.mbr
curl_log.txt
metadl_log.txt
uninstall.exe
[/U][/I]

Is there anything that I am missing or need to move?

Hope to hear more soon.

---

### Post by ago on 2008-03-10
If you have usb devices try disconnecting them

---

### Post by damn66 on 2008-03-10
boot to wind$ws and right click on the drive X (where u installed ubuntu)..do an auto repair..windows will prompt 'unable blah blah blah'..reboot for auto repair & finally, try booting to ubuntu again. this should solved yr problem :):)

---

### Post by some109 on 2008-03-10
chkdsk /r didn't fix it, so I reinstalled successfully. Again I turned off the computer, and when I booted back into Ubuntu later, the graphical loading screen disappeared 1/2way and went into a screen showing the loading process, and it got stuck there.
It stopped at the step after "mounting file disk", at something to do with swap space. Sorry if it isn't very clear; I'll check again soon and make it more detailed.

---

### Post by ago on 2008-03-10
> **some109 said:**
> chkdsk /r didn't fix it, so I reinstalled successfully. Again I turned off the computer, and when I booted back into Ubuntu later, the graphical loading screen disappeared 1/2way and went into a screen showing the loading process, and it got stuck there.
It stopped at the step after "mounting file disk", at something to do with swap space. Sorry if it isn't very clear; I'll check again soon and make it more detailed.

Do you see a desktop with a bird? If so when it stops press ctrl+alt+f2, then type

cat /var/log/syslog

and look for errors. If you copy the syslog to /host or /isodevice you will be able to access that from windows and attach it here.

---

### Post by some109 on 2008-03-10
no, it never gets to the desktop. it stops while loading in a DOS-like screen

also, i had enabled 3d in nVidia before I turned off the computer. could this be a problem?

it gets stuck during "swap-file swap"

---

### Post by ago on 2008-03-11
Did you try to press esc and select the other options? In case boot in verbose mode and try to copy /casper.log over to the mounted windows partition (you might have to mount it manually first) then attach it here.

---

### Post by DonQuichote on 2008-04-11
I had the same problem a few times with Xubuntu 8.04 beta. The startup messages also show that NTFS cannot be mounted, because it is busy.

I suspect that this is caused by an unclean Windows shutdown, that does not somehow "free" the NTFS partition that contains the Xubuntu distro. So you might try to login into Windows again, shut it down nicely and see if that helps.

---

### Post by capoditutti on 2008-05-17
Hi there,

Trying to unstall ubuntu 8.03 onto a sub-notebook with external pcmcia cd-rom drive - getting the same initramfs screen - any advice please?

---

### Post by jdennis_99 on 2008-05-20
I am having problems with my usplash screen - it disappears part way through bootup. I have been told in another thread ([http://ubuntuforums.org/showthread.php?t=798377](http://ubuntuforums.org/showthread.php?t=798377)) that this may be something to do with Wubi, as I installed Ubuntu via Wubi.

Apparently, I don't have a swap partition, which is causing the problem. Out of all the threads on the Wubi section, this one seems most in line with my problem.

---

### Post by ago on 2008-05-20
Press esc after selecting "ubuntu" at boot and go for the second (or other) option.
See if there is any relevant message

---

### Post by travist120 on 2008-07-23
if this has already been mentioned, I'm sorry.

But the way I usually fix this with Wubi is that I simply boot into windows, and do a proper shut down. (start -> shutdown) this might be part of the reason.

---

### Post by presh55 on 2008-07-24
> **twbdan said:**
> initramfs, what does it mean, when ubuntu won't load and uou get this message?

I have had the same problem today (first time Linux user and Ubuntu user) I realised this was caused by me downloading the .ISO for Intel / 64 bit machines, I believe this is corrected by downloading the file for PC / Pentium / AMD... 

lesson: it helps to pick the correct architecture before beginning!!! 

Hope this helps your problem!

Presh55

---

### Post by wizekid on 2008-09-05
man  i still cant get the flipping thing to install! its a new OS install 2!!! using 8.04  and it just wont leave!  what else can i do?  i had it working at 1 time but   i changed mobos and it hasnt worked since then! i dont think it could be a mobo could it?

---

### Post by ago on 2008-09-05
> **wizekid said:**
> i dont think it could be a mobo could it?
Yes it might be, depending on the differences you might have to reinstall (although it is generally possible to fix things manually it might be a bit complicated).

Also note that to uninstall rev 505 you need to follow these instructions:

[https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu)

---

### Post by wizekid on 2008-09-05
well remember, i dont have windows nor do i want it! the harddrive is clean and nothing on it! why am i still gettting this error? im going to try with anoother linux distro to see if they work

---

### Post by ago on 2008-09-05
> **wizekid said:**
> well remember, i dont have windows nor do i want it!
mmm I am a bit confused, you are not using wubi then.

---

### Post by linuxcat on 2008-09-07
I am getting the same type of problem.  The boot stops on "[796.801573] checking if image is initramfs..."  The install is running in a Virtual PC 2007 environment, 256Mb and 4Gb VHDD, and has been working for months.  Any help or pointers would be great.  I don't really want to reinstall.

---

### Post by Gilean on 2008-09-09
Ago, the same problem here with MSI Wind and Intrepid Ibex installed by Wubi-8.10-rev507.exe (Alpha 5). After the first windows reboot i have the initramfs...

---

### Post by zotrules on 2008-09-28
Is there any real answers in here, or not?
Just please, don't pretend to be experts and wait to get all the details of an error that shouldn't even occur.
There's people like me, who don't know a thing about linux/ubuntu.
As i can see from here, there's other people who are stuck at the same point, just like me; and I can see that nobody is giving them any answers, because these questions are being repeated over and over again.
"be more specific, i need detailed info...!" Is this a joke?
Now, i am aware of the fact that Ubuntu is free for everyone, and that there's no warranties whatsoever in it; so we install at our risk.
But please, some help here??? - It's ubuntu forums...
I am stuck at initramfs... damn that, and wohever invented it.
Now let me point our some things, so you don't ask anymore for "details"...
When you install via wubi, you're supposed to install through/over another OS. Let's say, XP, or Vista.
By default, either XP or Vista format their partitions with NTFS. You should have a really old computer to have any partitions formatted with Fat, or Fat32. Vista won't even bother to install without formatting in NTFS.
Now, that's supposed to work, ain't it?
I mean, there's millions of programs/installation packages out there that work and install perfectly in either vista or xp. Why can't ubuntu install?
Now this bug has been reported for longer than a year... hasn't anyone been able to fix it, or even bother to fix it?
As far as i can see it, Ubuntu, in my case and others that mention initramfs, doesn't do anything more than lock a couple of GBs of your drive, throw in some 800MB of files and write a little line in the boot.ini file (in XP). Now, everybody can write something like that! That isn't programming!
While in this ubuntu, i can't even see the demo!!!!!!!!!
I just downloaded it for the second time, hash-checked it successfully, burned it on a cd, and it is still not working.
Actually, when i check the cd for errors from the ubuntu console, the first time it found 8 errors; the second 9 errors.
my question comes as easy as it can get...
Is there any solutions?
I'm always stuck at this initramfs, i get the feeling it expects me to type commands... i type commands, but apparently it doesn't speak windows, it only speaks linux, which i don't.
I'm brand new in linux, i have no idea about it, i've seen it twice,once in a demo cd, the other itme in a demo computer in a shop.
Is there any way i could try this ubuntu without having the feeling i'm asking too much or without having to become a linux coding expert myself?
excuse my long post, but it's frustrating.

---

### Post by redbytex on 2008-10-01
I completely agree with zotrules.

This is my situation:

[LIST]
[*]I have only ever used windows.

[*]Today I went and bought a brand new custom built PC with a completely blank HDD.

[*]I put in the 8.04 (64-Bit) CD and selected "Install" at the menu.

[*]I am then brought to the [frustrating] initramfs screen.
[/LIST]

I've read all 5 pages of this thread and it makes absolutely no sense to me whatsoever.

Is there anyone out there with some answers?

Thanks in advance :)

---

### Post by redbytex on 2008-10-01
FIGURED IT OUT!!
After about 3 hours of searching forums via google and nearly giving up, I found this 23 page thread right here on our forums:
[http://ubuntuforums.org/showthread.php?t=765195]("http://ubuntuforums.org/showthread.php?t=765195")

_The very first reply worked for me!_

So here's what to do.

You will need to go into BIOS
(When you power on your PC, hit the delete key repeatedly till you are brought to a menu)

Using the arrow keys, find and select the option that says "Storage Configuration" or something similar to that.

Hit enter. Now go to where it says drive format (?), and change it from IDE to **RAID.**

Save settings and reboot.
PRESTO!

How this was never brought up in 6 pages of discussion I don't know. But there you go. 


Linux _cannot _boot to IDE, (which is the default setting for many motherboards) whereas Windows can. 

Hope this helps!

Obviously this problem needs to be addressed sooner than later, because as I've read on other boards, people are so frustrated in not knowing an answer that they give up and go back to windows.

---

### Post by airtonix on 2008-10-01
>  Linux _cannot _boot to IDE

Might want to elaborate on that statement, becuase many if not a majority of machines i have install linux on have had only IDE controllers with IDE drives.

---

### Post by redbytex on 2008-10-01
Yeah I could be wrong on that part. I'm just reiterating what another guy said in a thread.

Maybe it's this version of ubuntu, maybe it's this mobo. All I know is, it won't work in IDE mode.

---

### Post by zotrules on 2008-10-02
Redbytex... thankyou for your reply...
I don't think this is the case buddy.
It is supposed to install right on the click. At least that's what they say.
I am pretty sure, that this initramfs is asking for a command to continue the installation. The only problem is that i don't have a clue what it wants. Just like as i don't have the slightest idea about the linux coding.
There are very few the things I can't do to a windows powered pc, but with linux... i'm left open mouthed.
At the moment speaking, i have already managed to install ubuntu.
I'm going to tell everybody here how i did it.
I downloaded again the ubuntu installation iso. I rechecked the hash with success.
I installed a program called magic iso. (before doing this, i tried almost everything out there; from a little program of 30something MB from HP to ... ; this HP program could only work on .img extensions... i tried it, with an ubuntu converted to .img, but it didn't work.)
Finally, magic iso worked.
I burned this ubuntu.iso to a flash memory, a memory stick. On my case, 1GB of size. It burned successfully.
I went into bios. At the boot options, i brought up the list all the options that involved a memory stick/external memory.
I put the memstick in, rebooted and it worked like a charm!
Actually, at first, i loaded a demo of ubuntu; it loaded! Then i continued with the installation.
Everything went perfect. 
The only thing is that many things changed in my drive.
Some good,some not so good; but overall, perfect.
I am running an acer aspire 3682... it has been a long while that i had lost access to the pqservice partition. Alt+F10 option of restoration would not work. Even the acer's "technicians" can't tell you zip about that. They just know the altf10, and that's it. I couldn't use the dvd, as it's got some reading problems. Ubuntu, all of a sudden, brought it up, and pqservice ca run at the blink of an eye.
You wouldn't want to follow these steps on a vista operated system. Lunux writes directly to the MBR, just like vista, and not like xp with a simple, god-blessed boot.ini. (in my case, the mbr is now controlled by ubuntu... which i don't really mind; as long as i get the options for the pqservice, winXp and ubuntu recovery console.)
Personally, i don't guarantee that what worked for me will work for everybody else. but it's still worth a try. after all, a memory stick is better and more manageable than a cd. You can write, rewrite, rerewrite and do whatever you want. it woun't get any unfixable errors if checked. While the most cds are write and trashcan it.
There should be something wrong with the burning process of this iso to cd. the cd, like i've previously said, will result with errors. I bet everybody is having problems because of that.
I only wish somebody else tried these steps and wrote a reply here to maybe confirm that what i've just said is right or wrong.
good luck everyone.

---

### Post by HDTimeshifter on 2008-10-11
I get the "initramfs" error when I try to install or run live Ubuntu 8.04.1 or Ubuntu 8.04.  This is on a new PC I just built, but I swapped drives with my HTPC, so the disk has Mythbuntu 7.10 on it.  I've tried installing with both a CD just received in the mail from Canconical as well as one I burned a month ago.  The one I burned worked live on another PC a few weeks ago.  This has nothing to do with FAT, because the disk has only ever had Mythbuntu installed on it and nothing else.  I believe I have the regular 32-bit version although my PC has 4 GB ram, but when I tried downloading the 64-bit version, it had a filename prefix of AMD, so I didn't trust that to run on my Intel system.

---

### Post by kinyua on 2008-10-23
> **ago said:**
> when you boot, press esc when given the chance, then press 'e'. Edit the kernel line, remove "quiet splash" and add "debug". Then press enter and "b"

Thank you heaps, you are my hero!

---

### Post by Gralgrathor on 2008-11-06
I have a similar problem.

I have a simple machine, 32 bit architecture mainboard, dual core Intel cpu, 4 sata channels, 2 IDE, to which I added an additional 4 IDE channels using a PCI IDE controller. The machine came with a Samsung 500G SATA drive (ch. 1/4), and I added 2 WD 1T SATA drives (ch. 2 and 4/4), and 2 older WD 500G IDE drives (those last two I plugged into the PCI controller, both as master).

The base install works like a charm. I just enter through the program, sacrifice my entire (hd0) 500G SATA drive to the "guided partitioning" process, remove the CD, hit enter - and -

End of story. The thing won't boot no matter what I do. The machine just stopped dead right after the POST check.

So here's what I did: I re-installed Debian, my previous installation, using the same harddrive, and told the installation program to tweak the MBR and /boot partition (why doesn't the ubuntu install livecd have nifty options like that? sure, the installer is easy to use - unless it doesn't work!). Then I re-installed ubuntu, again using (hd0).

Now, at boot, at least I got the grub menu. But keying enter got me in the BusyBox. So I rebooted and got myself into a grub commandline, to try some stuff. I couldn't get it to boot no matter what "root (hd#,#); setup (hd#)" I entered. 

I did discover one thing though:

Debian assigns a completely different range of drive numbers to my drives than ubuntu.

My machine has 3 SATA drives, and 2 IDE drives on a plugged in PCI IDE card. It also has a combination card reader internally on USB. It's starting to look like with ubuntu, USB is numbered as the first 4 SCSI devices, while the SATA and IDE drives are given drive designations higher than those. I want to install ubuntu to the same disk Debian was first on: the first sata drive - but apparently my BIOS, Debian and Ubuntu *all* have different ideas as to which drive is which.

I still don't know why the ubuntu installer can't figure out how to correctly configure my MBR and grub, but at least I know the direction to look in.

If any of you knows anything about this; don't hesitate to lemme know: my system's been offline for 3 days now, and it's starting to hurt :|

Thanks!

G.

---

### Post by nickinuse on 2008-11-06
I'm trying to do an install from an external USB-CD drive (I believe it's NEC inside) onto an IDE drive inside a Thinkpad R51.
It seems that the installation process/hardware probing drops the power of the drive or gives wrong instructions to the CD-ROM or something, because even when I reboot from the initramfs screen winxp fails to attach the cd drive giving the usual device malfunctioned talk until it's turned off and on again (not just disconnected).
However I'm sometimes able to boot the install/demo by turning the usb-cd power off and on again, then selecting "help me to boot the CD" from the autorun menu, thus adding an entry to wubi loader to boot.ini (again, not always, usually this involves turning the cdrom on/off somewhere at the beginning of the screen with ubuntu log and progress bar running).

Another suspicion (actually two) is incorrect operation of gparted and the results in the partition table. I went to install a tripple-boot system. I used gparted to shrink and move my C: (winxp, obviosly NTFS) partition so there would be free space at the beginning of the HDD to install Mac Leopard to a first primary partition to avoid problems with booting into it. Experimented with the installation to no avail, though I believe it added its own GPT besides MBR. So I try to move the C: partition back to it's initial place (Ubuntu is planned be at the end of drive). Although the initial drive had ~17Gb at all for C:, of which ~3Gb taken by windows's files and programs, gparted now shows ~13gb as used on the partition and is taking forever to re-shrink/restore the space. Windows checkdisk shows no errors adn the correct size of ~3Gb taken, PartitionMagic however warns of partition table sectors moved (wrong MBR) and warns not to edit partitions in this state.
I know incorrect size may reported either be due fragmentation, which gparted thus may have produced moving the partition for the first time or it's picking incorrect entries from GPT/MBR (I did fdisk /MBR from windows startup cd to be able to boot into windows).
Also I've been running into similar problems on another laptop with a SATA drive, grub not being able to "predict" the Ubunutu's partition at correct place for a newly-created ext3 partition (re-grubbing from command line is a real pain, there really should be some "auto re-grub" / fixmbr / fixgpt command utilities on the install cd).

---

### Post by nickinuse on 2008-11-07
Ok, have been able to correct the partition table (reset end of disk from sector 254 to 239 or something) and shrink my C: partition (there were some files at the end of the partition, mostly MFT, used some defragmenting tools to move them closer to the beginning).
This, however, leaves the problem of USB-CDROM failing at some point after the kernel initiation. I am able to proceed to the demo/installation only if experimenting with turning it off and on again, thus "reinitiating" the usb connection.

---

### Post by EnGorDiaz on 2008-11-23
try the link in my sig guys you might be surprised it might work:)

---

### Post by bruno9779 on 2008-11-24
I had a similar problem with Wubi on a lousy Windows Vista.
The problem is very simple: If windows doesn't shut down properly, Ubuntu is not going to work. Lame but true

Eg.: If I forget to choose ubuntu at the beginning and just switch off before WV is loaded, I will then get initramfs untill I reopen and shut down properly WV.

Furthermore, Ubuntu recovery mode pretty much does it, as it tells you about what is happening and 2 possible solutions.
It is kinda unbelievable, but you get the linux kernel telling you it can't work while windows is in that state.

---

### Post by mzar on 2008-12-24
> **ago said:**
> when you boot, press esc when given the chance, then press 'e'. Edit the kernel line, remove "quiet splash" and add "debug". Then press enter and "b"

This doesn't help me solve the problem. It still load to initramfs. What to do? My box just using Ubuntu 8.04. No other OS.

---

### Post by bond17_007 on 2008-12-25
I ma having similar problem.. 

I have a custom made desktop with 
Intel Core 2 Duo 1.8 GHz
2 GB Ram
250 HDD
American Megatrends MB

----
I have a internal HDD on which I have Windows
I have a 250 GB USB HDD that i have for Ubuntu 8.04. 
So, Mostly I just go to BIOS and change the boot order to load to UBuntu. 

every thing was working fine until recently when I formated my windows HDD and re-installed windows.. 
everything was good
but then I wanted to start using ubuntu. So, I did the same thing I use to do, Pluged my USB HDD (with Ubuntu) change the boot order.. but now i get "initramfs" screen :(
I changed the bios to set to RAID instaed of IDE and stuff but no luck . 
ANy help is appreciated. 
thank you,

---

### Post by msriram on 2009-01-20
Thanks .. It worked

I tried to install Ubuntu 64 on my quadcore comp, and it gave me the error. Hdd was set to IDE. I changed it to RAID, and ... tadaa.. it worked

---

### Post by Feivel on 2009-01-20
INITRANFS means

**I**
**N**ever
**I**ntended
**T**o
**R**ead
**A**ny
**M**essages
**F**rom
**S**ystem

---

### Post by dysvir on 2009-03-25
i have this initramfs thing and am VERRY new to ubuntu please help me boot back into ubuntu i have documents i need to get to A.S.A.P

---

### Post by jmszr on 2009-03-25
dysvir,

       Are you using Wubi or is it a full install?

---

### Post by Tundro Walker on 2009-04-16
Ok folks, not sure I can clarify an answer, but I think I can at least shed some light on what might be going on.

I installed command-line Ubuntu 8.10 (Intrepid) on an old i-opener netpliance comp, which comes with a default 16mb flash disk built-in, but someone had hacked the i-opener to also use a 40gb IDE laptop hard disk drive.

After installation, rebooting would cause a "freeze" with a screen dumping a bunch of boot-up stuff and finish with ...

---[ end trace (long string of characters) ]---

I found out that this was because boot-up was having a hard time detecting the monitor settings.  FOLKS DOING VIRTUAL PC INSTALLS HAVE HAD THIS ISSUE FOR A WHILE when using Ubuntu.

The temporary fix for this is ...

1) boot up
2) at grub, press ESC to enter grub menu
3) hit 'e' to edit the 1st boot option (the default boot)
4) go to the line that starts with 'kernel ...'
5) hit 'e' to edit it
6) delete " splash quiet" from the end
7) add " vga=791 noreplace-paravirt" to the end (make sure there's a space before typing vga=...)
8) hit ENTER
9) hit 'b' to boot using your edits

What this does is force the boot to see if the VGA setting you typed in is compatible with your system.  Even if it isn't, the system will prompt you to pick one that is (asking you to choose or to just wait 30 seconds.)  Pick an option that your monitor can support.

(Side Note: once you successufully boot, you can go into the /boot/grub/menu.lst and permanantly edit those "kernel " lines to include those changes, so you won't have to keep manually editing each time you boot...  Easiest way would be to...

1) open command-line terminal
2) sudo nano /boot/grub/menu.lst
3) scroll down to the lines that start with "kernel "
4) go to the end of them and replace " splash quiet" with "vga=791 noreplace-paravirt"   (or, leave "splash quiet" and just add "vga..." etc onto the end if you still want the boot splash screen instead of all the boot lines to show
5) CTRL+O to "writeout" (save) your changes to the file

If you're sick of being prompted to pick a VGA setting that's compatible with your monitor, since 791 isn't, you can use [this site]("http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/") to figure out which 7XX code to fill in on the menu.lst file instead.

While virtual PC installs of Ubuntu have this issue, I also had it on the i-opener since it only supports 800x600x16bpp.

end side note)

~~~~~~~~~~~~

However, sounds like a lot of you are having a hard time even getting past boot due to initramfs.

First, what is INITRAMFS ... it's basically Ubuntu's more modern method of implementing INIT.D by using a RAM File System (INIT RAM FS ... INITRAMFS).

Init.d handles a lot of boot & module loading, probing, etc during boot up.  InitRAMFS creates a RAM drive to make this go quicker, and (I think) also does it in such a way to allow concurrrent loading (making it go even quicker).

(In MS-DOS, there's an equivilent function called SMARTDRV, which sets aside a portion of RAM to load things into as a disk drive, making accessing the info much faster.  I think INITRAMFS is using the same concept to make the Linux boot faster.)

~~~~~~~~~

After initial install (and fixing the vga= issue), booting was going ok.  After I got it going, I got my wireless going and did a system-wide update, which included an update to the latest kernel.

From that point on, I started getting dumped to the (INITRAMFS) prompt, or sometimes the boot-up process would keep running these ...

ata0. (Blah, blah, blah)
ata1. (blah, blah, blah)

... things every 30 seconds.

What I believe is happening is the bootup is scanning for, finding, and trying to figure out what the new hardware it's seeing is.

EG: 

To install Ubuntu on my i-opener's laptop drive, I swapped the laptop drive over to a faster desktop computer, booted it from CD, did the install, then swapped it back over to the i-opener.  The desktop I did the install on only had the cd-rom & laptop drive hooked up as media sources.

The i-opener, however, has the laptop drive, but also has the built-in 16mb flash disk, plus I've been leaving a 1gb flash stick plugged into a usb hub hooked to the i-opener which I was using to transfer files.

Watching the initramfs go through it's song and dance, it looks like it's detecting these devices (since they weren't there during initial install), and perhaps trying to figure out if they're being used in some kind of RAID configuration.

I also noticed my system seemed to "lock up" during one boot.  Looking at the preceding lines before it stopped, it had detected the 16mb built-in FDD.

I hit "enter", and it dropped me to the (initramfs) command line.

(INITRAMFS) WORKS LIKE ANY OTHER COMMAND-LINE.  Ideally, you'd use it to fix whatever problem the system is wigging out about.  But I just typed "exit" and hit "enter" to quit the command-line, and it proceeded on with the boot-up process, finally getting to the login.

~~~~~~~~~~~~~~~~

I'm not quite sure if INITRAMFS is having issues modprobe'ing hardware, or if it's crapping out while trying to mount drives in RAID fashion, or what.  But, if you installed Ubuntu on a machine with multiple HDD's, updated the kernel and now it's taking a long time to boot, it seems to be one of those two things.

Anyone else care to take a stab at this?

---

### Post by Cokemonkey on 2009-06-02
I'm getting this from a fresh full install of Linux Mint 7.

typing exit at the initramfs console booted normally, and repairing GRUB using the super grub disc fixed it I think.

---

### Post by ____ on 2009-06-03
i am getting this with the live cd of gOS i will try to download another .iso

---

### Post by ramiro77 on 2009-08-30
Hi

I also had the intramfs problem, unable to install ubuntu in an ide hard drive. I tried formatted the drive on fat32 and nothing.

I have an old computer, and I was looking on the bios how to switch from sata to raid  as suggested by some, and I couldn't find that option.

what I did was to disable the apic mode in the bios and tried again booting from the ubuntu installation cd, and now it works!

I don't know how my system is going to be affected by disabling the apic mode (I know it has something to to with interruptions), but at least it worked. :)

---


---
title: "Ubuntu won't load"
date: 2007-11-24
forum: General Help
---

### Post by pikablu on 2007-11-24
This really sucks. I spent 3 hours installing Wubi, I installed Ubuntu, I went to the OS screen when I restarted my computer, chose Ubuntu, and it never loaded past a couple lines of something. Does anybody know how I can fix this?

---

### Post by linux noooob on 2007-11-24
you should use the default boot loader grub it may fix the problem.

---

### Post by pikablu on 2007-11-24
Well, I don't know what that is. I'm very new to Linux and all this. :P

---

### Post by linux noooob on 2007-11-24
sorry
i know it is confusing um well grub installs with ubuntu so if you re-install it then grub is installed automatically.

but really i have no clue what wubi is:confused:

---

### Post by gali98 on 2007-11-24
Don't know much about Wubi. Can you still boot windows?
Kory

---

### Post by gali98 on 2007-11-24
> **linux noooob said:**
> sorry
i know it is confusing um well grub installs with ubuntu so if you re-install it then grub is installed automatically.

but really i have no clue what wubi is:confused:

Wubi is a way to install ubuntu through the windows bootloader. Go here to check it out.
[http://wubi-installer.org/]("http://wubi-installer.org/")
You might check this site to see if they can help you...
I'm sorry I've never used this so I can't help much.

---

### Post by pikablu on 2007-11-24
Oh, well, it said that this was their support board, so I thought I would ask here.

I can still boot up windows, yeah. I'm on that now.

---

### Post by ago on 2007-11-25
What exactly do you see?
When there is the countdown, try to press esc, and select the ACPI option.

---

### Post by brucem91 on 2007-11-25
Once you install Wubi from windows, you have to then let ubuntu install. This only happens the first time you boot ubuntu(or only happens till it is complete). So when you go to boot ubuntu, it is actually finishing the install. Takes about 30 minutes I beleive, been a while since I have installled ubuntu.

---

### Post by pikablu on 2007-11-25
Well, thanks, but neither of those worked. :-/

Are there any other known problems.

---

### Post by kzz5 on 2007-11-25
I tryed to install ubuntu, and some other kind of Linux, but neither worked of them..

somebody told me with wubi I can use Ubuntu correctly.
Today I had installed it, but after the second boot, Ubuntu stopped to load...

so I have the same problem. and there isn't any options to change ACPI on or off. I only can choose from XP and Ubuntu to boot. That's all.

I'm really bored of useing XP so please help me! :)

---

### Post by jaezcurra on 2007-11-25
I am sure that Wubi for Gutsy will be OK soon, but in the meantime I may suggest you try virtualization stuff such as VirtualBox, VMWare, etc.

---

### Post by ago on 2007-11-26
You have more boot options if you press "esc" at the countdown during boot.

If an acpi option is not there, you can add "acpi=off" to the boot menu, by pressing "e"

---

### Post by morag on 2007-12-16
[LEFT]
Hello. I have the same problem.
(I mean: I downloaded the Wubi executable and ran it successfully (the running included downloading of a few hundreds MB). Then I rebooted and chose Ubuntu, and after few lines are written on screen the computer stays there forever.)
I've tried to reinstall - nothing changed.
I've tried to press ESC in the counting down time - it stopped the counting down, but nothing else happened (couldn't, for example, type "acpi=off"). pressing "e" didn't seem to make any change.
My MS Windows is fine (as far as you can say it about any MS product ;-) ) - I'm writing from it right now.
Any suggestion?
Thanks in advanced for your help
[/LEFT]

---

### Post by Sanijs on 2007-12-16
When you choose Ubuntu-Linux press Esc then press on "start in safe graphic mode" it will works if he stop installing just reinstall wubi and try again i do this a couple times i mean reinstalling wubi, and it works for me or you select "start in normal mode" then when he stops i dont know sum error like "fatal IO error 104 press" Ctrl+Alt+F1 and type startx and hit enter then you get linux desktop where you just duble click on install icon and follow instructions! I hope you understand, because my English is very bad! :)

---

### Post by morag on 2007-12-16
I hope I understood.
But, I tried and it didn't help. I press ESC and don't get any menu. Everything looks the same as before pressing it.

---

### Post by Sanijs on 2007-12-17
Ok try this [http://wubi-installer.org/devel/minefield/Wubi-7.10-alpha-rev381.exe](http://wubi-installer.org/devel/minefield/Wubi-7.10-alpha-rev381.exe) and with this distra [ftp://ftp.linux.lv/pub/ubuntu/7.10/ubuntu-7.10-desktop-i386.iso](ftp://ftp.linux.lv/pub/ubuntu/7.10/ubuntu-7.10-desktop-i386.iso) it works fine at least for me!

---

### Post by morag on 2007-12-19
Well, I tried...
The installation went fine, the n I rebooted.
It looked like it's going ok, but then it got stuck, on the screen of "checking the installation" on the "copy files" at 46%.
I tried rebooting a few times, each time another point of getting stuck, most of the times I had the built-in shell, which I don't know what command to type.
On one of the rebootings, I noticed that the computer tried to read from the floppy (A) couple of times, even though nothing was in there.

---

### Post by MONODA on 2007-12-19
dont use wubi. it is beta software. ubuntu will not run as good as it would if you install it correctly. If you dont want to make a comitment to ubuntu yet, then I suggest using the live cd that you can download from ubuntu.com or just install it to a small partition. also if you dont have any cds, you can use unetbootin which is like wubi but actually creates  a real partition.(be careful with unetbootin it is also beta software.

---

### Post by Migosh on 2007-12-22
I finally installed Ubuntu 7.10 using Wubi 7.10, thanks to morag, Kzz5 and Pikablu! I had made about 10 failed attempts on win XP using different file systems (FAT and NTFS) and partitions. I faced the same frustruations like morag; -ubuntu installation will freeze at one point or another during "Copying files". Running CHDSK /R did not help (time costly!). On win98 (on which it should onlso work) it said: "no root file system is defined. Please correct this from the partition menu".
Well, after going through all the entries relating to morag's and Kzz5's problems I worked it out. This is how it can be don:
1. Install Wubi-7.10-alpha-rev386 (which is/was the latest) on XP
2. Upon reboot to complete ubuntu installation chose UBUNTU LINUX (2nd option), and PRESS [ESC] IMMIDIATELY AFTER (within 1 second)! This is important to access ubuntu's boot options.
3. Chose the option the says something about walking around ACPI if you have ACPI problems.
From here, continue with your installation guide.
Thanks also to Sanijs and you all.

Someone said "don't use wubi". But, I say "WUBI IS JUST WHAT I HAVE BEEN LOOKING FOR!".

---

### Post by morag on 2007-12-22
Thanks, Migosh.
Unfortunately, I tried it before and didn't make it. After I install and boot, choose the ACPI option, it get stuck somewhere on a window that says "Checking the installation", with subtitle "checking the mirror site" (I hope I translate it right, it's not English...) on 82%. After a long while, it simply reboots.

MONODA
You're might be right, but I had also problems when I tried to install Ubuntu form CD. that's the reason I try Wubi, no success ](*,)
I think the problem is not Wubi, because I saw the attempts to read from the floppy also on the CD installation.

---

### Post by dz0 on 2007-12-25
I noticed two times, that wubi way installed ubuntu will install, but won't load, when it's drive is other than windows install drive (I mean, when we have c:\windows, but instal linux to d:\ or e:\)
and I think its not the ACPI or APIC thing, as installation process goes through OK

---

### Post by tunnerus on 2007-12-30
Hi 

I am also experiencing some challenges with Wubi 7.10 and 7.04 on my Thinkpad X60s WinXP. Installed on the D partition using 8 GB.

Wubi-7.10-alpha-rev386.exe (which I tried first, and also rev 385)
Install goes fine, machine restarts, I choose Ubuntu-linux, I see the progress bar going right-left-right-left, but then I get this error message for a couple of second, then it halts with a screen that says:

"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)"

The brief error message: I took a photo, the message looks something like:

"
[      1.080000] PNPBIOS fault.. attempting recovery.
[      1.(blabla)   PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[      (morebla)   PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[       (...)          PnPBIOS: check with your vendor for an updated BIOS
[    (...)             PnPBIOS: get_dev_node: unexpected status 0x37
"
(already have the latest BIOS)
Then I tried to use that suggested &#8220;pnpbios=off&#8221; but I really didn&#8217;t get where to put it so no results so far. Have also tried ctrl+alt+f1 to get to some place and enter &#8220;startx&#8221; like someone suggested but I only got a screen which said something like &#8220;wait&#8221;&#8230;

Wubi-7.04.04.exe
I sort of get to something similar but it ends up in a different message: 
&#8220;Booting &#8216;Ubuntu&#8217;

(hd0,1) 
Filesystem type is ntfs, partition type 0x7
  [Linux-bzImage, setup00x1c00, size=0x1a82cc]
  [Linux-initrd @ 0x1f85e000, 0x7918a5 bytes]
Loadin, please wait&#8230;
[       4.752000] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
No RAID disks&#8221;

Then it just ends there.

Please help!

(BTW: tried to install ubuntu on another PC, but did not succeed until I found wubi!! :-)  - thanks to the developers! Now I would like to do it on my laptop as well!)

---

### Post by ago on 2007-12-30
> **morag said:**
> Thanks, Migosh.
Unfortunately, I tried it before and didn't make it. After I install and boot, choose the ACPI option, it get stuck somewhere on a window that says "Checking the installation", with subtitle "checking the mirror site" (I hope I translate it right, it's not English...) on 82%. After a long while, it simply reboots.

Try with internet connection on. Normally though if it reboots it means that the installation went fine

---

### Post by ago on 2007-12-30
> **dz0 said:**
> I noticed two times, that wubi way installed ubuntu will install, but won't load, when it's drive is other than windows install drive (I mean, when we have c:\windows, but instal linux to d:\ or e:\)
and I think its not the ACPI or APIC thing, as installation process goes through OK

Check menu.lst file

---

### Post by ago on 2007-12-30
[QUOTE=tunnerus;4040009]Then I tried to use that suggested “pnpbios=off” but I really didn’t get where to put it so no results so far.[\quote]
In /wubi/install/boot/grub/menu.lst

in the line(s)  that starts with "kernel" replace "quiet splash" with "pnpbios=off"

You can also try to press esc at the countdown and select one of the other boot options

---

### Post by tunnerus on 2007-12-31
Hi + thanks for the help!

tried to replace in d:\ubuntu\install\boot\grub\menu.lst,but there was no line starting with "kernel" so I just replaced all of the "quiet splash"es with "pnpbios=off". didn't work thou...

what now?

should I un- and reinstall wubi, try again to replace before the firstreboot?

**** edit below****
So, now I finally tried again...
Uninstalled, reinstalled "Wubi-7.10-alpha-rev386.exe", edited d:\ubuntu\install\boot\grub\menu.lst again but before first wubi-install-reboot, replaced all quietsplashes with pnpbios=off. Then rebooted and tried loading without pressing Esc in the brief countdown, as well as all three options (safe graphics, ASPI(?), and verbose). With varying results, actually. I will attach photos of the screen at each halt...

---

### Post by morag on 2007-12-31
> Originally Posted by **ago**:
Try with internet connection on. 
Thanks, ago.
But, in order to connect, I have to install the dialer, isn't it? I cannot install it without finish the Ubuntu installation.
Beside that, isn't there any way to install Ubuntu without internet connection? I don't see the reason for that. I have the complete ISO CD downloaded to my hard disk, so why should I ever need any web connection?
Thanks anyway for the advices, and thanks in advanced for any suggestion.

---

### Post by tunnerus on 2007-12-31
attached photos of how far I got in the ubuntuload...

---

### Post by ago on 2008-01-01
can you post here menu.lst?

@morag internet connection is not normally required but there might be some bug and that would be a quick workaround, waiting might also work.

---

### Post by morag on 2008-01-01
Thanks again, ago.
about waiting: I already waited for a long time, ended with rebooting of computer (the rebooting wasn't done by me. the computer did)
If it's a bug - Do you think it's Ubuntu's bug or Wubi's?

---

### Post by ago on 2008-01-02
rebooting is normal after successful installation

---

### Post by tunnerus on 2008-01-04
Hi there,

I really hope I didn't interrupt this thread with something inappropriate, but I am still struggling with my wubi-installs. I cannot get past the installation and first reboot, no matter what I try. It usually freezes in either of the following:

"[ some number ] JFS: nTxBlock = 8192, nTxLock = 65536"

or 

"[ some other number ] usb 4-2: configuration #1 chosen from 1 choice"

and sometimes I also get a prompt:

"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash) 
Enter 'help' for a list of built-in commands.

(initramfs)"

Is there some command I should give at that point? Should I wait? 

Oh, here's the content of my menu.lst:
#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu
timeout		3
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso pnpbios=off ro -- automatic-ubiquity locale=en_FI console-setup/layoutcode=se console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz xforcevesa boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso pnpbios=off ro -- automatic-ubiquity locale=en_FI console-setup/layoutcode=se console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz acpi=off noapic nolapic pnpbios=off boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso ro -- automatic-ubiquity locale=en_FI console-setup/layoutcode=se console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debug boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso ro -- automatic-ubiquity locale=en_FI console-setup/layoutcode=se console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot



Please help!

---

### Post by grimbello on 2008-01-04
Hi ALL - As usual there are heaps of posts reporting the same or similar problem but no viable solution. I too have just wasted hours, it seems, downloading and installing Ubuntu via Wubi only to reach the end and get a dreaded error message....code 17 - cannot find file. 
I have installed on external USB drive named "F"....Could the problem be that the Windows boot loader will only search for files on the "C" drive and is ignoring "F"? If so, how can one change this behaviour??
Everything seems okay, the download, install, setup and all went without a hitch then can't boot.....it is sooooo frustrating....HELP!

  lol.........cheers.......JIMBO

---

### Post by ago on 2008-01-04
tunnerus press esc at the countdown and select one of the other options.

If none works look at the log files generated when booting in verbose mode. The logs are in /tmp or /var/log

---

### Post by ago on 2008-01-04
> **grimbello said:**
> Hi ALL - As usual there are heaps of posts reporting the same or similar problem but no viable solution. I too have just wasted hours, it seems, downloading and installing Ubuntu via Wubi only to reach the end and get a dreaded error message....code 17 - cannot find file. 
I have installed on external USB drive named "F"....Could the problem be that the Windows boot loader will only search for files on the "C" drive and is ignoring "F"? If so, how can one change this behaviour??
Everything seems okay, the download, install, setup and all went without a hitch then can't boot.....it is sooooo frustrating....HELP!

  lol.........cheers.......JIMBO

try wubi 7.10 it uses a more recent bootloader

---

### Post by grimbello on 2008-01-04
I reckon that Wubi-Ubuntu will NEVER boot from an external USB drive. Wubi is specifically designed to install Ubuntu on the primary hard drive, alongside Windows, without the need for partitioning....it uses the Windows boot loader and that only searches for files on the main ("C") drive. You could possibly change this behaviour by editing the boot.ini file but that would be way over my head.
Does that sound right? I don't know much about it but it makes sense to me.

---

### Post by ago on 2008-01-04
not really correct. grub4dos can search for files on any drive including usb ones, and wubi should work also off usb drives (never tested that personally though).

---

### Post by grimbello on 2008-01-04
I hear you, but Grub is also installed on the external drive so you never actually get to it.

---

### Post by tunnerus on 2008-01-05
ago: I booted in verbose mode, but cannot find any log files - am looking for them in Windows, is that right or are they available in the "initramfs" prompt?

---

### Post by ago on 2008-01-05
log files are available within the initramfs shell

use "ls" to list files and "cat" or "more" to read them

---

### Post by tunnerus on 2008-01-06
okidoki, found a logfile called initramfs.debug, it was pretty long (1st screen with more showed as only 3%)

couldn't see any obvious things in it, though, what should I be looking for?

It ended with 

+ touch /casper.vars
+ parse_numeric
+ return
+ mountroot
+ exec
+ exec
+ exec
+ exec

---

### Post by ago on 2008-01-07
Easiest way is if you can past it here.

You should be able to mount one of the windows partitions 

mkdir /mydir
cat /proc/partitions #list partitions
mount /dev/sd?? /mydir #replace ?? with the right partition from previous command
cp /path/to/log /mydir

Then zip it from windows and post it.

Otherwise look for errors in the log

grep -i err initramfs.debug

---

### Post by tunnerus on 2008-01-09
I feel a little stupid now, couldn't get the mounting to work

my partitions were sda, sda1, sda2, sda3, and sda4

(tried to mount sda, sda1, sda2 and then gave up)

"grep -i err initramfs.debug" returned nothing

---

### Post by ago on 2008-01-09
grep -i err /tmp/initramfs.debug

mkdir /tmpmount
mount -t auto /dev/sda1 /tmpmount
ls /tmpmount

umount /tmpmount
mount -t auto /dev/sda2 /tmpmount
ls /tmpmount

...

---

### Post by tunnerus on 2008-01-15
ooook

tried installation on c:\ instead

this also ends before it is ready: reboots and goes thru a lot of lines in verbose mode but then stops more or less in the same spot as before

the only change is that now I cannot find any logfile from the initramfs shell....

---

### Post by Migosh on 2008-01-17
Greetings all. After my 1st entry (see #20) I was surprised that wubi didn't seem to work for anybody. Maybe it is hardware dependent, because I have installed on 2 other machines with different HD partition configurations successfully. (I have not tried installing on C: however). 
I have also noticed that after a power failure (I live in Cameroon where such things are very common) sometimes ubuntu will boot in verbose mode. Booting windows xp, which in turn runs chkdsk (check disk) brings everything beck to normal. So, if you have had a successful installation and it starts misbehaving, maybe just booting xp can help.
One more thing positive about wubi; since the early 90s I made it a practice to always have 2 HD with independent installations of whatever windows I was using, such that I could switch boot drives at the BIOS level. This saved my day many times. With wubi I install ubuntu once, but whatever partition I chose to boot from ubuntu linux is always available as long as the partition where wubi installed ubuntu is in the machine. I don't need to do multiple installations of wubi/ubuntu.
:)

---

### Post by tunnerus on 2008-01-19
......went back to installing to d:\, in order to try again to get that initramfs.debug here

after "mount -t auto /dev/sda1 /tmpmount"

I get: "mount: Mounting /dev/sda1 on /tmpmount failed: invalid argument"

same story with /dev/sda2

(unrelated to this, I have installed wubi on two other PCs and those both went fine...)

Am now thinking that the wubi/unbuntu installation problem might be linked to this "mount" problem - maybe the installation has failed in a way that makes it impossible to mount, or maybe the problem preventing the mount is the same problem that is preventing the installation. Any comments, anyone? Of course this is pure speculation, very far from any concrete error which might be the real cause...

My laptop has some kind of utimaco safeguard encryption of the hard drive, but this should not to my understanding impact this installation - maybe it does anyway?

Should I take photos of each screen of "more initramfs.debug" and upload here?

---

### Post by ago on 2008-01-20
> **tunnerus said:**
> 
Am now thinking that the wubi/unbuntu installation problem might be linked to this "mount" problem - maybe the installation has failed in a way that makes it impossible to mount, or maybe the problem preventing the mount is the same problem that is preventing the installation.
If wubi cannot mount the windows partition then the installation will fail with a busy box.
Why that is the case I do not know. Look into /proc/partitions to see if the windows partition is visible. And try to mount using the exact filesystem.

> My laptop has some kind of utimaco safeguard encryption of the hard drive, but this should not to my understanding impact this installation - maybe it does anyway?

If the full hard disk is encrypted it might create problem. Try to mount the same partition from live CD.

---

### Post by tunnerus on 2008-01-21
The windows partitions are visible in /proc/partitions. How to mount using exact filesystem? Am pretty newb....

full HD is encrypted - will maybe give up soon...moving beyond my patience limit anywho

thanks for the help to all anyway!

---

### Post by ago on 2008-01-21
> **tunnerus said:**
> The windows partitions are visible in /proc/partitions. How to mount using exact filesystem? Am pretty newb....

full HD is encrypted - will maybe give up soon...moving beyond my patience limit anywho

thanks for the help to all anyway!

mkdir /mntpoint
mount -t vfat /dev/XXX /mntpoint #for fat partitions
mount -t ntfs /dev/XXX /mntpoint  #for ntfs partitions

As mentioned, it is well possible that encrypted disks are not supported, particularly if the decrypting usually happens in the windows domain.

---

### Post by LouReed on 2008-01-21
Hi I'm having some problems too installing Ubuntu via Wubi.

I had already tried to install Ubuntu 7.04 on this laptop (compaq presario V6000) a year ago but I gave up.

I installed wubi 7.10, downloaded Ubuntu , rebooted, selected Ubuntu-linux, and pressed esc.
Then I have a menu :
1)normal mode.
2)if you are having displaying issues. 
3) acpi mode.
4) verbose.

whatever mode I pick up, I see lines of codes, checkings ending by [OK], and then a black screen ...

and to me this is not really [OK] xD

So if you guys have any ideas to help me out I would be more than happy to try to fix  this mess ^^

PS: Is it possible that the installing process is running while all I see is a black screen ?

---

### Post by ago on 2008-01-21
Yes, that's unlikely to be the same issue as mentioned above by the way, since that results in a busybox shell after mounting.

You can normal press (ctrl)+alt+F2 to get a shell. Looking at the logs is a first step.

Log files (depending on what stage you are in) are in 

/casper.log
/tmp/initramfs.log
/var/log/*

In particular your issue seem to be with the graphic driver.

---

### Post by LouReed on 2008-01-22
Okay I finally got the installer to work.
I booted and choose the no acpi mode and it worked.

the installation process ran succesfully but when I rebooted again it crashed.

On boot i could choose between :
normal
rescue
memtest

Both normal and rescue fail to boot... 
I have the laoding display ...with the progress bar and ubuntu stuff.

Then black screen.

What should I do ?
I might be wrong but I suppose i have to specifie the no acpi option but I dunno how.
HELP :p

---

### Post by ago on 2008-01-22
add acpi=off to /ubuntu/disks/boot/grub/menu.lst

you can look at the example within /ubuntu/install/boot/grub/menu.lst

normally if you need acpi off during installation you will also need it after installation (will change that to make it default)

---

### Post by LouReed on 2008-01-25
Thanks I edited menu.lst and it booted !

problem is I forgot my password and ID ... :lolflag:

is there a way to retrieve them ?
Or do I have to unistall wubi and start over again?

by the way is there a way to fix the ACPI issue later on ?
Cause it saves alot of battery.

---

### Post by ago on 2008-01-25
For acpi issues, bets way is to file a bug report in launchpad

If you forgot the password choose the second boot option (recovery mode). Then at the console you can change the user password with the passwd command.

---

### Post by Apostacio on 2008-01-25
hi guys im really REALLY new to ubuntu but after 2 trys I've successfully installed 7.10 with wubi, i though there was something wrong when wuby installed super fast compared to the 7.04 version, i notice that supposedly it copys the DESKTOP ISO that you downloaded to an install directory so i think something might have happened there like getting corrupted, i just deleted it and put the original one and in reboot for the second time i selected ACPI and it continued to the classic "checking installation" dialogue box and after the longest 10 minutes of mi life it finished :KS i know that some people have reported errors after de second boot, im yet to reboot for the first time cuz im installing de updates :lolflag:

edit: i rebooted and everything looks fine

---


---
title: "[SOLVED] Initramfs ...why?"
date: 2008-04-10
forum: General Help
---

### Post by Gilean on 2008-04-10
Hi to all...i installed my ubuntu hardy with wubi installer inside cd...Today i started ubuntu but (i dunno why) it started in shell mode with cursor after initramfs.....why it happened and how to fix it? tnx a lot for you help.

---

### Post by ago on 2008-04-10
There should be  a file called casper.log. You can read it with the command "cat" and shift+pgup to scroll. Please report any error msg.

---

### Post by Gilean on 2008-04-10
how to do? i cannot do copy paste 'cause i'm in shell mode..can i open it from windows?

p.s. sono italiano cmq :D

---

### Post by Galantir on 2008-04-10
I get the same problem everytime.
I tried everything mentioned in the other post about this problem.
Nothing seems to work.

I hope someone finds out what it is.

---

### Post by ago on 2008-04-10
I need some more error info to understand what is happening

When you are in a shell type

cat /casper.log

use shift+pgup to scroll

See if there is any meaningful error. Also see if you have an installation-logs.zip file in C:\ubuntu under windows.

---

### Post by Galantir on 2008-04-10
ok i did find out a lot more by trying out verbose mode.
It seems none of my internal hd's are mounted which results in the fact that the iso can't be found.

I also found out my external drive was mounted so i tried to install on that one but got an error an a wave files and soon after a failed instalation, but at least the install started which confirmed that the external drive was mounted.

I also receive some error about drives 2 to be exact.
But since i have 2 hd's in raid(hardware) i figured it might be those two.
Both of these drives are sata drives.
I also have another IDE drive but also that one doesn't get mounted.
The raid drives contain both vista and xp.

Anyway i'm going to see if it helps to put the iso on my external drive and installing it to an internal drive.

---

### Post by ago on 2008-04-10
raid 0 is not supported (see FAQ on wubi website)
as for the usb installation problems might be the same issue as [http://ubuntuforums.org/showthread.php?t=750352](http://ubuntuforums.org/showthread.php?t=750352)

---

### Post by Galantir on 2008-04-10
Yeah i thought that wasn't supported, however this does not explain why my IDE drive is not showing.

I tried another install to my external drive and this time i didn't get the wave file error, however the instalation fails at the end and forces reboot.
Indeed it seems i have that problem with the usb drive so i'm trying out an older version on it now.
I'll stick to that for a while till the other one works ok.

---

### Post by ago on 2008-04-10
> **Galantir said:**
> Yeah i thought that wasn't supported, however this does not explain why my IDE drive is not showing.

Do you see any error message related to that? Can you try mounting that manually from shell prompt? Does it show in cat /proc/partitions?

---

### Post by Galantir on 2008-04-10
Well i tried several thing and several versions but nothing seems to work for me.

with 7.04 i get a black screen after splash/loadingscreen dpkg-reconfigure xserver-xorg and changing it to vesa doesn't work for me.

With 7.10 i get a black screen after first reboot after the splash/loadingscreen even in safe mode.

8.04 still fails at the end of each install.

I have an amd64 3800+ 
2gb ram
2x7800GT(running SLI in windows)

tried 64 bit verions aswell as 32bit

I'm getting a bit desperate about getting ubuntu to work.
it seems if 7.04 is booting fine when installed since i hear the logon sound and when i logon blindly again the startingsound sounds.

One videocard seems to give output so i connected two monitors to both connectors to see what they would do.
They both go to black after the splash/loadingscreen.

---

### Post by ago on 2008-04-10
> **Galantir said:**
> 
8.04 still fails at the end of each install.

That is what I am interested in. Do you see c:\ubuntu\installation-log.zip? In case post it here (password may be there).

---

### Post by Galantir on 2008-04-10
well i deleted 8.04 already.
The past hour i've been trying to install it again, but this time receive the error 15
The solution to this points me to a non-existing file which i should change and thus can't.
This all together has convinced me to stick to windows since all these things are signs for future problems.'ve spend over 10 hours today on this and over 2 hours yesterday with not a single positive result.
This has convinced me to stick to windows.

Thanks for your help.

---

### Post by Gilean on 2008-04-10
ago hai msn?

---

### Post by ago on 2008-04-10
irc
#wubi su irc.freenode.net

---

### Post by Galantir on 2008-04-10
I did manage to get the zip file containing the logs using a recoverytool.
Maybe they can be of interrest.

---

### Post by ago on 2008-04-10
Galantir same issue as here: [http://ubuntuforums.org/showthread.php?t=751601](http://ubuntuforums.org/showthread.php?t=751601)
Unfortunately today daily iso was broken, it has been fixed, but the new iso has not been uploaded yet...

---

### Post by Galantir on 2008-04-10
Well i had another go with the iso mentioned in that thread.
The install finished but wehn i reboot after install and try to run ubuntu i get another error.

error 21 looks like it can't find a file in the ubuntu/disks folder

---

### Post by ago on 2008-04-11
Are you sure it is error 21? Or is it error 15?
Press esc after you select Ubuntu, then press "e" to edit the first item, what are the first 2 lines?

---

### Post by Galantir on 2008-04-11
Yes, i'm sure it was error 21.

But this was easy enough to solve.
Somehow after the install one of my other drives is also recognised which somehow changes the hd and partition.
I just added options for every partition to the menu.lst so i could try every partition on boot.

Turns out instead of hd(4,0) it became hd(3,0)

So i finally got it to boot.
The only problems i'm left with is that my wireless card doesn't work and both my videocards are not using the correct driver.

For now i hooked up a cable(since i'm using ubuntu to post this) to see if i can get something to work to solve these last problems.
I don't expect too much problems on my nvidia cards, but do on my broadcom wireless. I can't seem to find anything about the 306 rev 3 version which is also a linksys card.

---

### Post by ago on 2008-04-11
Well turns out you went through the entire WubiGuide troubleshoting section... 
Thanks for bearing with us.

---

### Post by Galantir on 2008-04-11
Well i guess i was wrong about the nvidia part.
I downloaded the driver from nvidia site and installed itxtra appearance options.
But after reboot ubuntu now starts in low graphics mode and not a single setting works.
also i can't run in 1680x1050 anymore which i was able to do from start even without the nvidia cards supported.
It also recognised my monitor, now it doesn't anymore.
Opening up the nvidia control panel tells me x is not configured the right way and i should run nvidia-config to correct this.
But even after doing this nothing works.

Any clues on how i could solve this?

---

### Post by ago on 2008-04-11
You may want to try [http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135)
I have no direct experience with your hardware. If the nvidia driver does not work revert to the previous one (good rule is to backup /etc/X11/xorg.conf or the whole /etc). 

I'd also try to stick to the Ubuntu repository. If something is not there, there is probably a good reason... The restricted driver applet should be able to suggest something reasonable.

---

### Post by Gilean on 2008-04-11
ok i totally removed wubi+ubuntu hardy beta...only one thing...i had this problem even in 7.10. In final hardy release there will be this bug or u'll fix it 'till the final ago?

---

### Post by ago on 2008-04-11
Gilean I do not have enough information on your specific case (unless I missed it).

I would need to know the error message generating the problem, from a log or from something appearing on screen.

---

### Post by Gilean on 2008-04-11
ho ago, is there any way to copy-paste this log from windows'?

---

### Post by ago on 2008-04-12
do you mean casper.log?
At the shell prompt, you first have to mount a windows partition, then copy it there, then you will be able to access it from windows

mkdir /trash
mount -t auto /dev/sda1 /trash
cp /casper.log /trash

where you have replace sda1 with the appropriate disk (=a) and partition (=1)

---

### Post by Jason Perlow on 2008-04-12
I am experiencing similar problems to the original poster, but this appears to have happened after doing an apt-get upgrade and installing six patches which include the updated kernel. I can currently only boot to initramfs.

I'm working on an article on wubi, so Any help would be appreciated.

Jason Perlow
Linux Magazine
AIM: JHPERLOW

---

### Post by ago on 2008-04-12
Jason, do you know what was the original kernel and what was the new kernel?

The kernel update per se' should not have much to do with wubi, it is possible that the new kernel introduced some regression. For instance I have a samsung q45 and while that worked with 2.6.24-12, the new kernel  2.6.24-15 had ACPI problems (have to boot with acpi=off). See my last comment in [https://bugs.launchpad.net/ubuntu/hardy/+bug/146692](https://bugs.launchpad.net/ubuntu/hardy/+bug/146692)

Things to try include: 

1) Press esc after selecting Ubuntu to get a boot menu, and choose the old kernel if still available

2) Press esc after selecting Ubuntu to get a boot menu, select the second option  (rescue mode). See if there is any relevant boot error. In particular, if you see any message about acpi problems, report the bug in launchpad and append "acpi=off" to the kernel line. To do so  press "e" to edit the first boot entry, and "e" again to edit the kernel line. Then enter and "b".

3) If all else fail boot with the "debug" argument appended, there should be a log under /tmp, you can access it using the commands "cat" or "more"

---

### Post by Jason Perlow on 2008-04-12
The problem does appear isolated to the -16 kernel. I booted with -15 instead, and all is well again. Obviously there is some sort of regression issue with the new kernel or module dependency associated with it.

---

### Post by Jason Perlow on 2008-04-12
BTW, this is on a Lenovo ThinkPad T60, 32-bit Core Duo. I did not specify acpi=off on -15, it just plain boots and works on -15. I'm going to try acpi=off with -16.

Here is the launchpad report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/216418](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/216418)

---

### Post by Jason Perlow on 2008-04-12
So, I tried booting with acpi=off on -16. The system boots, it goes to X, to GNOME, but it apparently breaks the USB subsystem. I am unable to connect my USB mice to the machine. I also get some sound stuttering and multiple replays of the "ubuntu drums" at the GDE login.

---

### Post by ago on 2008-04-12
Jason try first to do a system upgrade, if you still have the same problems, do open up a bug report in lauchpad [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

It is important to notify developers of regressions as soon as possible in this stage

---

### Post by Jason Perlow on 2008-04-12
when you say system upgrade, you mean an apt-get upgrade or an apt-get dist-upgrade?

---

### Post by ago on 2008-04-12
yes

---

### Post by ago on 2008-04-12
Jason could you please post c:\ubuntu\disks\boot\grub\menu.lst?

---

### Post by Jason Perlow on 2008-04-12
Here is everything past the commented out stuff on top:

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=666806DD6806ABBD loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=666806DD6806ABBD loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=666806DD6806ABBD loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=666806DD6806ABBD loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by ago on 2008-04-12
that looks good, thanks

---

### Post by Jason Perlow on 2008-04-15
Ago, it appears that the kernel related problems for -16 stem from ThinkPads that have not been updated to the latest BIOS revision which support various bugfixes to PnP. The crash to Intitfs appears after a number of PnP errors in the kernel boot. After I upgraded the T60's BIOS, I was able to do a clean WUBI install with 2.4.26-16 and everything runs fine.

---

### Post by ago on 2008-04-16
Glad to hear that! And thanks for the tip! Will try to upgrade my BIOS too and see if it addresses my ACPI issues...

---


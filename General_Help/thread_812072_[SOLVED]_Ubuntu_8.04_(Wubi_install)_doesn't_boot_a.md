---
title: "[SOLVED] Ubuntu 8.04 (Wubi install) doesn't boot after the last update"
date: 2008-05-29
forum: General Help
---

### Post by azangru on 2008-05-29
Hi!

I was running Ubuntu 8.04 (installed with Wubi), when after the last update the system had to be restarted, and failed to boot - it stopped at "initramfs" promt. That happened a couple of days ago. I reinstalled Ubuntu, went through the updates again, keeping my fingres crossed, but the result was the same devilish initramfs. I can't figure out how to boot the system and whether it's at all possible to do so. Could you please help?

Don't know if it matters, but just in case: my machine is a Toshiba Satellite 5100 laptop, and Ubuntu worked quite well on it, until that ghastly update that is.

(sorry if this post belongs not with Wubi, but with other Ubuntu forums - I am a very inexperienced Lunux user yet)

---

### Post by azangru on 2008-05-29
Tried to browse ubuntu forums in search of a solution, and apparently another piece of information that you may ask for before giving an advice is the type of file system. Mine is NTFS.

---

### Post by Dave2k6 on 2008-05-29
See [here](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623) for information and two possible solutions.

---

### Post by azangru on 2008-05-29
Thank you very much for the hint - I wasn't aware of the "esc" trick.

Anyhow, I located the problem. Apparently, during the last update, Ubuntu downloaded the kernel version 2.6.24-17 and now can't boot in it. When I choose the previous kernel, 2.6.24-16, the system boots fine.

Now, since I am a complete newbie, I need some further advice. What do I do next? Do I remove the offending new kernel (and if so, how do I do it?) or do I somehow fix it?

---

### Post by ago on 2008-05-29
> **azangru said:**
> Thank you very much for the hint - I wasn't aware of the "esc" trick.

Anyhow, I located the problem. Apparently, during the last update, Ubuntu downloaded the kernel version 2.6.24-17 and now can't boot in it. When I choose the previous kernel, 2.6.24-16, the system boots fine.

Now, since I am a complete newbie, I need some further advice. What do I do next? Do I remove the offending new kernel (and if so, how do I do it?) or do I somehow fix it?


Can you pls provide some exact log/error message when booting with 2.6.24-17? That would be helpful.

---

### Post by azangru on 2008-05-29
> **ago said:**
> Can you pls provide some exact log/error message when booting with 2.6.24-17? That would be helpful.

I'll see what I can do. Just in case there are too many of them - are the startup messages logged in any file (or can I make them logged in some file, and how do I do it)?

---

### Post by Dave2k6 on 2008-05-29
I'm not sure how to remove a kernel, but you can edit the menu.lst file to set the default boot option back to kernel 2.6.24-16.

menu.lst is in D:\ubuntu\disks\boot\grub (replace D with actual drive that ubuntu was installed onto, on your system).

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
# kopt=root=UUID=9418D86918D84C3C loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)/ubuntu/disks

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=9418D86918D84C3C loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=9418D86918D84C3C loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9418D86918D84C3C loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9418D86918D84C3C loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1
```

If your menu.lst file is like mine (see above), then changed the default 0 line to default 2 and save the file (use notepad or wordpad to edit the file).

GRUB numbers the enteries listed after '## ## End Default Options ##' from 0 (0 being first menu item (Ubuntu 8.04 Kernal 2.6.24-17).

---

### Post by azangru on 2008-05-29
> **azangru said:**
> Just in case there are too many of them<...>

Turns out I was worrying too much. There were no error messages whatsoever, at least none that I could see. Just a Grub counter, then the Ubuntu logo with the running orange line below it - and then the busy-box.

That just proves that I'm stupid and don't know how to make error messages visible. And, what's more important, how to save them in a file.

---

### Post by azangru on 2008-05-29
> **Dave2k6 said:**
> menu.lst is in D:\ubuntu\disks\boot\grub (replace D with actual drive that ubuntu was installed onto, on your system).

<...>

If your menu.lst file is like mine (see above), then changed the default 0 line to default 2 and save the file (use notepad or wordpad to edit the file).

Yep, my menu.lst is identical to yours (apart from the values in "kernel" - I have: kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=1F1D-08E1, whatever that means).

Only I wonder where you found your file - in Windows or in Linux. I can't view any Linux files from Windows (there wasn't a Ubuntu folder visible on my C: drive at all). I found menu.lst in Ubuntu File System (/boot/grub). Don't know whether we are talking of one and the same file, but I guess we are.

---

### Post by ago on 2008-05-30
Getting initrd log is not obvious at all, the first thing to try is to press esc at boot and select recovery mode, then press "e" to edit the entry and "e" again on the kernel line. Append "debug" to that line and press enter to save the changes and "b" to boot

Now you should see more messages passing by, and a log will be in /tmp
You can use the commands "more" (to read the file) and "grep" (to look for a word in the file) to look for errors. In particular look for mount error

grep err /tmp/* -A3 -B3
grep mount /tmp/* -A3 -B3

---

### Post by azangru on 2008-05-30
> **ago said:**
> Getting initrd log is not obvious at all, the first thing to try is to press esc at boot and select recovery mode, then press "e" to edit the entry and "e" again on the kernel line. Append "debug" to that line and press enter to save the changes and "b" to boot

Now you should see more messages passing by, and a log will be in /tmp
You can use the commands "more" (to read the file) and "grep" (to look for a word in the file) to look for errors. In particular look for mount error

grep err /tmp/* -A3 -B3
grep mount /tmp/* -A3 -B3

Now, I'm confused. I did as you said, and got some messages after inputing grep mount /tmp/* -A3 -B3 (grep err returned nothing), but how do I save the output to a file on the disk to publish it here? There was nothing in the tmp folder after I rebooted in the .16 kernel.

---

### Post by ago on 2008-05-30
> **azangru said:**
> Now, I'm confused. I did as you said, and got some messages after inputing grep mount /tmp/* -A3 -B3 (grep err returned nothing), but how do I save the output to a file on the disk to publish it here? There was nothing in the tmp folder after I rebooted in the .16 kernel.

If you cannot mount any partition you will have to write down the relevant error messages and post them here (exactly).

What filesystem did you install onto? Was that fat32 or ntfs? What is your kernel?

cat /proc/partitions
uname -r

You can try to mount mount the relevant partition (it will be one of th items in /proc/partitions) manually with the command

mkdir /tmp/sda1
mount /dev/sda1 /tmp/sda1

mkdir /tmp/sda2
mount /dev/sda2 /tmp/sda2

...

And so forth for all listings in /proc/partitions

---

### Post by Dave2k6 on 2008-05-30
D:\ubuntu\disks\boot\grub = /boot/grub in ubuntu (used drive letter D as this is where ubuntu is installed on my system).

So, /boot/grub/menu.lst and D:\ubuntu\disks\boot\grub\menu.lst are both the exact same file.

If mine and your menu.lst files are the same, then the default 0 line needs changing to default 2 (to boot 2.6.24-16 kernel).

---

### Post by azangru on 2008-05-30
> **ago said:**
> If you cannot mount any partition...

Oh, now I see why nothing was saved to the file. Makes sense.

OK. Here goes my error message:

```
mount: Mounting /dev/disk/by-uuid/1F1D-08E1 on /root system failed: No such device
mount: Mounting /root on /host failed: Invalid argument
panic alert! /host/ubuntu/disk/root.disk does not exist
Dropping to a shell
```

---

### Post by sobukus on 2008-05-30
I encountered the same issue yesterday with someone I helped to get wifi going on his wubi install (note: while being quite experienced with linux systems, my ubuntu knowledge is very limited -- and I just learned abount wubi).
I suggested a system update after wifi was working and thus we faced the issue described here.
the -17 kernel boots and bumps into the initrd... saying tha the root device is missing.

I've found /dev/sda1 and friends looming there, tried to mount them directly (of course I wasn't aware of the special wubi install yet).
That didn't work: the devices are invalid. Nothing about bad filesystem or such... mount just doesnt't accept the devices.

I made a screenshot of the initial bump into busybox:
[IMG]http://sobukus.de/Foto_052908_001.jpg[/IMG]

Any idea what didn't work there with the loop drive setup or the devices in general?
The -16 kernel works normally and I will recommend to switch back to that one for now... but of course I'd like this guy to have a positive first experience about linux keeping the system up to date.

---

### Post by azangru on 2008-05-30
> **Dave2k6 said:**
> If mine and your menu.lst files are the same, then the default 0 line needs changing to default 2 (to boot 2.6.24-16 kernel).

Thanks, I'll do just that. Only - sorry for the lame question - how do I get the root privileges for editing this file with, say, Notepad (I'm still not friends with the Terminal).

---

### Post by Dave2k6 on 2008-05-30
in terminal type:

```
sudo gedit /boot/grub/menu.lst
```

and press Enter, then type in your password and press Enter again.

---

### Post by ago on 2008-05-30
If you have fat32 there is a confirmed bug that resuluts in Wubi failing to boot on kernel upgrade (to 17).

To fix it:

* boot with the 16 kernel (press esc at boot)
* add "vfat" to /etc/iniramfs-tools/modules
*run: sudo update-initramfs -c -k 2.6.24-17-generic

---

### Post by azangru on 2008-05-30
Thanks, Dave! Worked like a charm :)

Besides, I reduced the waiting-before-booting time from 10 seconds to 3, which added a bit of convenience.

---

### Post by azangru on 2008-05-30
> **ago said:**
> If you have fat32 there is a confirmed bug that resuluts in Wubi failing to boot on kernel upgrade (to 17).

Now, there's something weird going on here. I clearly remember that I converted my C: drive to NTFS using this Windows tool (Convert.exe?), whose shortcut was on the desktop. It did its job, and now Windows reports that my C: drive's file system is NTFS. Then I installed Wubi and Ubuntu on the C: drive. Should be NTFS, right?

However, when Ubuntu was booting up, I noticed a message that said: file system type: fat.

What the heck?

---

### Post by Dave2k6 on 2008-05-30
Don't quote me on this one, but at a guess I think the convert tool is a 'dirty' convert which doesn't correctly mark the drive as NTFS (hence the ubuntu error). Windows XP knows the drive was converted so sees it as an NTFS.

Really it's NTFS on FAT32. True NTFS is only gained when you install Windows and tell it to format drive as NTFS.

This is only a guess, I could be wrong, but that's the only thing I could think of that's causing the ubuntu error.

---

### Post by azangru on 2008-05-30
> **ago said:**
> * boot with the 16 kernel (press esc at boot)
* add "vfat" to /etc/iniramfs-tools/modules
*run: sudo update-initramfs -c -k 2.6.24-17-generic

Seems pretty straightforward, only I never dealt with modules before. How do I get this vfat?

---

### Post by azangru on 2008-05-30
> **Dave2k6 said:**
> Don't quote me on this one, but at a guess I think the convert tool is a 'dirty' convert which doesn't correctly mark the drive as NTFS (hence the ubuntu error). Windows XP knows the drive was converted so sees it as an NTFS.

Really it's NTFS on FAT32. True NTFS is only gained when you install Windows and tell it to format drive as NTFS.

I guess you are right.

---

### Post by sobukus on 2008-05-30
[QUOTE=ago;5077384]If you have fat32 there is a confirmed bug that resuluts in Wubi failing to boot on kernel upgrade (to 17).

Oh, interesting information... I'll try your proposed fix (though I am still puzzled as to why I cannot mount /dev/sdaX ... well, at least why I don't get a message about "wrong filesystem / bad superblock".

But, supposing that re-including the VFAT driver is the solution... can we expect a -18 kernel that fixes the issue soonish? Sounds like a no-brainer.

---

### Post by ago on 2008-05-30
> can we expect a -18 kernel that fixes the issue soonish? Sounds like a no-brainer.
Yes, I have already submitted a patch and it has been accepted, the automatic upgrade should resolve this soon.

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/236021](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/236021)

---

### Post by Dazed_75 on 2008-06-04
> **ago said:**
> If you have fat32 there is a confirmed bug that resuluts in Wubi failing to boot on kernel upgrade (to 17).

To fix it:

* boot with the 16 kernel (press esc at boot)
* add "vfat" to /etc/iniramfs-tools/modules
*run: sudo update-initramfs -c -k 2.6.24-17-generic

Unfortunately, this does not seem to resolve the problem.  Yesterday I did the wubi install on a friend's windows machine (unfortunately his fs is FAT32) and everything was fine until the update manager installed 124 updates.  The reboot failed to the initramfs shell as with other people.

Your instructions were clear (ignoring the missing t in the second line) and appeared to run properly including the update-initramfs command.  However, reboots continue to fail in the same way unless I interrupt and select the 2.6.24-16 kernel image and then everything works.

1) Is there a way to check whether the updated image file truly has the needed update in it?
2) Are there alternate fixes known (other than changing grub menu default to 2)?  :lolflag:
3) Any projection yet for the fix (whether -18 or later)?

Unless a fix is coming quickly, I will probably uninstall the wubi-ized ubuntu and install ubuntu for real as an xp/ubuntu dual boot so my friend does not need to deal with it.

---

### Post by ago on 2008-06-04
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/236021](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/236021)

---

### Post by Dazed_75 on 2008-06-05
Thanks for the reference Ago!.  I understood much of it though not all.  I think the best solution for my friend is still to dump the wubi install and go with a normal install.

I still think wubi is the cats meow for noobs wanting to try linux but for now I will be telling them to only use it if they are running on NTFS and even not on one which was converted from FAT32.

---

### Post by ago on 2008-06-05
The fix will be available in the point release on the 1st of July

---

### Post by bikinguy77388 on 2008-06-06
Very informative..thanks so much. I use fat32 on win2000pak4. I have to select the 16 version which is no real problem for me. Nice to know fix is on the way. 

bikinguy

---

### Post by mobilediesel on 2008-06-06
At least an update is on the way. The good thing about this problem happening is that it forced me to learn more about Ubuntu and Linux in general! I've used Microsoft Windows since 3.11 except for Windows ME. XP Pro was definitely a HUGE stop up from 98. Vista steps up the features but TOTALLY steps DOWN performance! Yes, I have used Vista and it renews the definition of bloatware. I switched to Ubuntu because of the impending stop on support for XP even though it will be awhile before they stop supporting it completely. I switched my desktop to Xubuntu yesterday because this 633Mhz processor wasn't quite up to the task of running XP.

Even with the problems that I've had with Ubuntu I'm totally happy with it! Some talk about lack of support for all Linux derivatives. I've had MUCH better support with Ubuntu through the forums, IRC and Google. Volunteers are doing support for Ubuntu. Worker drones are doing support for Microsoft. Who do you think will personally care more about helping you?:guitar:

---

### Post by jcwinnie on 2008-06-07
> **Dazed_75 said:**
> wubi is the cats meow for noobs wanting to try linux

Operative word is "try", just don't upgrade even when prompted to do so or be prepared to start over again and again and again

---

### Post by azangru on 2008-06-07
Downloaded the .18 kernel through the update manager today. Thought it has been fixed. Nope - it was the same old initramfs on startup.

And yes, I entered the grub menu to boot specifically the .18 kernel. Nada.

Looks like this:

> **jcwinnie said:**
> just don't upgrade even when prompted to do so

is the only foolproof solution. :(

---

### Post by jcwinnie on 2008-06-08
And, don't believe the Wubi Wiki, which states, "Upgrading from 8.04 to 8.10 will be fully supported."

---

### Post by ago on 2008-06-09
You can follow it up here [https://bugs.launchpad.net/ubuntu/+bug/236021](https://bugs.launchpad.net/ubuntu/+bug/236021)

---

### Post by ago on 2008-06-09
The fix has been released, new updates should be ok

Please test it out and let me know.

---

### Post by mobilediesel on 2008-06-11
> **ago said:**
> The fix has been released, new updates should be ok

Please test it out and let me know.

The new update definitely fixes the problem!

---

### Post by azangru on 2008-06-22
> **mobilediesel said:**
> The new update definitely fixes the problem!

Yes, it does! The .19 kernel works. Great!

---


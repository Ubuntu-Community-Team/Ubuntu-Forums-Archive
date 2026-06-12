---
title: "ERROR, PORTS ALREADY IN USE on boot"
date: 2006-12-19
forum: General Help
---

### Post by W. Irving on 2006-12-19
Installed Ubuntu on a Thinkpad 380D (150MHz/48MB). Server installation with fluxbox. Works great, apart from one tiny issue; the computer doesn't always boot.

At least nine times out of ten, it stops right after this:
> Starting up ...
[  xxx.xxxxxx]hda: ERROR, PORTS ALREADY IN USE

Sometimes it adds another line as well:> [  xxx.xxxxxx]hdb: ERROR, PORTS ALREADY IN USE
Peculiar, since, AFAIK, there is no hdb... (unless that's the CD, but I assumed the CD would be hdc)

Then it sits like that for a few minutes and eventually goes to what looks to me like shell run off a ramdisk - unless I press Ctrl + Alt + Del and hope for the best.

Here are the kernel parameters:

> /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet acpi=off noacpi apm=on

After some googling on the error message, I suspect it might have something to do with DMA, so I tried appending this to the kernel parameters:

> ide=nodma ide0=nodma

But there hasn't been any difference.

What can I do? I'm getting desperate..

---

### Post by W. Irving on 2006-12-19
I snapped a photo of the display with the error once I'd removed the quiet bit in the kernel parameter.

Strange thing though, the recovery mode seems to work every time!

[http://img214.imageshack.us/my.php?image=dsc00424smalldw7.jpg](http://img214.imageshack.us/my.php?image=dsc00424smalldw7.jpg)

So that's what happens during a failed boot.

The only differences between this and when booting in recovery mode are the

> [ xxx.xxxxxx]hda: ERROR, PORTS ALREADY IN USE

and

> register_blkdev: cannot get major 3 for ide0

which are not present when the boot succeeds.

---

### Post by W. Irving on 2006-12-20
Update: no, recovery mode does not "seem to work every time". The success rate is as poor as with regular mode.

Any ideas?

I'm guessing a kernel bug, IDE controller bug, or perhaps a faulty hard drive (doesn't explain hdb failing though). Gonna have a stab at compiling a new kernel.

---

### Post by W. Irving on 2006-12-20
It's not the hard drive. Replaced it - same problem.


Anyone..?

---

### Post by hikaricore on 2006-12-20
I used to get this error in dapper 6.06 after a particular kernel upgrade, or one I compiled myself I can't remember for sure.  I don't know how else to resolve it but rebooting a couple times.  The times it wouldn't boot I'd have to boot another OS like a live cd then reboot.  >.<  Never had it happen in edgy tho.

Sorry I can't help just wanted to let you know it's not just you.

---

### Post by W. Irving on 2006-12-20
Thanx for the comforting reply! :)

It is indeed Edgy I've installed.
One final attempt before installing Windows 95 instead; compiling my own kernel. Pity really, since the whole fluxbox setup is so much faster then W95.

---

### Post by hikaricore on 2006-12-20
Did you install edgy direct or do a dapper -> edgy upgrade?

---

### Post by W. Irving on 2006-12-20
I installed Edgy directly, using netboot.
Now compiling.. wonder how long this'll take.

---

### Post by scorpion-kde on 2006-12-21
I get the same error on Feisty Herd 1 on a Pentium II.  It started after I upgraded update-initramfs.  I have run Dapper and Edgy on the same machine without issues.  I'll see if I can dig up any more info on it.

---

### Post by sysops on 2006-12-22
I have the same issue with Feisty on a PIII running linux 2.6.20. I'd installed a bunch of updates yesterday and rebooted fine but the machine was having serious performance issues, I noticed a bunch of messages like these logged in syslog every second.
[B]
[######.######] hdb: drive is not ready for this command[/B]

(where # was a bunch of numbers)

After deciding to reboot, i landed up with these -

[B]
hda: ERROR, PORTS ALREADY IN USE
hdb: ERROR, PORTS ALREADY IN USE
[/B]

then a two minute pause before

[B]Check root = bootarg cat /proc/cmdline
  or missing modules, devices  cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/b3bad[/B]..<long UID here>..[B] does not exist
[/B]

and then the busybox ash prompt as show at the bottom of this image [http://img214.imageshack.us/img214/4899/dsc00424smalldw7.jpg]("http://img214.imageshack.us/img214/4899/dsc00424smalldw7.jpg")

Indeed the mount-point does not exist, as a manual ls reiterates. After ruling out IRQs conflicts and other possible contentions,i decided to try booting knoppix which boots up fine, no indications of failure there at all. Nautilus with an Edgy desktop CD does not read the mount point labels for /dev/hda but correctly identifies those on /dev/hdb. And to no surprise the ash shell has no listing of the device by that UUID under /dev/disk/by-uuid or /dev/hda*.

It seems it's an issue with the latest kernel images? I can't get to boot linux 2.6.19 either. What kernel version is everyone else with this issuse running?

---

### Post by gosh on 2006-12-22
I have this problem too, since I added some lines in my fstab to automount my ipod and usb-harddisk.

I run this kernel:  2.6.20-2-386

I'll will try what happens if I install the linux-generic kernel.

---

### Post by gosh on 2006-12-22
No luck, linux-generic gave me the same error

---

### Post by gosh on 2006-12-22
Succes! with linux-kernel 2.6.19-7

---

### Post by sysops on 2006-12-22
Gosh, can you give us more details about your setup please? Details such as which drive was failing and whether it was a new style /dev/disk/by-uuid/* drive or old style /dev/hd*.

It'll help other users who have the issue with a similar setup. 

I am going to try installing an earlier kernel release as 2.19 still doesnt work for me.

Thanks

---

### Post by dm1024 on 2006-12-25
Same issue. Kernel 2.6.20-2.

---

### Post by superG on 2006-12-28
same problem was for me.
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/76872](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/76872) - there is a solution.

---

### Post by gosh on 2006-12-28
> **sysops said:**
> Gosh, can you give us more details about your setup please? Details such as which drive was failing and whether it was a new style /dev/disk/by-uuid/* drive or old style /dev/hd*.

It'll help other users who have the issue with a similar setup. 

I am going to try installing an earlier kernel release as 2.19 still doesnt work for me.

Thanks

This is my fstab:
```
/dev/hda2  / ext2      defaults      1 1
#proc     /proc     proc     defaults     0 0

/dev/hda1  /media/XP ntfs ro,user,fmask=0111,dmask=0000 0 0
/dev/hdb1  /media/Movies ntfs ro,user,fmask=0111,dmask=0000 0 0
```

hda and hdb both fail.

---

### Post by rvfh on 2007-01-03
I have the same problem on an nForce2 chipset, with kernels 2.6.19 and 2.6.20. The other (Egdy) kernels don't boot at all anymore.

I'm gonna try and re-create the initial RAM disk if I ever manage to boot into Linux again...

I noticed a md error at initramdisk creation, maybe linked?

---

### Post by towsonu2003 on 2007-02-20
I just got the same message booting a self-compiled 2.6.20-1... using Dapper. I wonder if this is the same problem?

edit: the work-around of "add "ide0=noprobe ide1=noprobe" to your kernel command-line" as mentioned in bug report doesn't work for me.

---

### Post by panda84 on 2008-03-25
> **towsonu2003 said:**
> edit: the work-around of "add "ide0=noprobe ide1=noprobe" to your kernel command-line" as mentioned in bug report doesn't work for me.

The explanation of why it doesn't work for you is here:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0706.1/1645.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0706.1/1645.html)

But I don't know if that workaround will work for you!

---

### Post by panda84 on 2008-03-25
This another solution worked for me:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/76872](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/76872)

In Ubuntu 7.10 Gutsy the file is no longer called:
```
/usr/share/initramfs-tools/scripts/local-top/udev_helper
```
but it is called:
```
/usr/share/initramfs-tools/scripts/local-top/live
```

However the solution is the same: just edit the "live" file and comment out (put a "#" at the beginning of the line) the line with "modprobe ide-generic" and then run:
```
sudo update-initramfs -u
```
and reboot.

Regards,
Diego

---


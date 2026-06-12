---
title: "Error 1: Filename must be either an absolute pathname or blocklist"
date: 2017-02-07
forum: General Help
---

### Post by ray-3 on 2017-02-07
Hi there,

I have a Ubuntu 14.04 LTS (Desktop) system I have been using for many years, it has been upgraded many times (hardware and Ubuntu versions) and until today has proved reliable

Last night I had a power failure and this morning the system would not boot. Grub loads, then the kernel is selected for boot and the error in the thread title pops up.

The last major update to the hardware was a move of the boot drive to SSD.

What I have done so far;
[LIST]
[*]Tried other grub entries,
[*]Pulled the boot disk and tried it in another highly simplified hardware setup,
[*]Booted to system rescue distro and successfully mounted the root partition, (/dev/sda1)
[*]Checked the grub path to the kernel, (/boot/vmlinuz-3.13.0-108-generic*)
[*]Checked the root UUID,
[*]Checked the partition has space,
[*]Took a look at "/boot/grub/menu.lst". All looks ok, though it is very long and messy and has many entries. (I really should run autoremove)
[/LIST]

As far as I can tell the disk should boot. So I'm in need of ideas. Open heart surgery to menu.lst seems like the next move but I am reluctant at this point until I get some pointers.

Right now the disk is sitting in my test rig, mounted with system rescue booted from a USB flash drive, so I can post configuration files to assist with diagnosis.

---

### Post by Bashing-om on 2017-02-07
ray-3; Hello; Welcome to the forum.

I be the bearer of real bad news :
> 
 Ubuntu 10.04 LTS (Lucid Lynx) was the twelfth release of Ubuntu. Desktop support ended May 9 2013. Server support ended on April 
               30 2015. See [http://ubottu.com/y/lucid](http://ubottu.com/y/lucid) for more details.

There no longer exist a supporting software repository for 10.04 .
Install a current release ( 16.04 ). ( and get acquainted with systemd) .

[INDENT][INDENT]it was
[INDENT][INDENT]but no longer is
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ray-3 on 2017-02-07
Apologies. A typo on my part, the system is 14.04 LTS.

---

### Post by Bashing-om on 2017-02-07
ray-3; well then; :)

The 1st order of business after a power failure is to run a file system check/repair :
see thread :  [https://ubuntuforums.org/showthread.php?t=2351777&p=13603880#post13603880](https://ubuntuforums.org/showthread.php?t=2351777&p=13603880#post13603880) post #3 for this procedure.
If still not able to boot , then we boot the system from the grub prompt, and see ;- maybe consider re-install grub ?

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by ray-3 on 2017-02-08
Bashing-om,

From system rescue boot I have umount'ed /dev/sda1 and run; 

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

No errors occurred. Same error after reboot.

What's next?

I will set up a Boot Repair USB flash disk as per [these]("https://help.ubuntu.com/community/Boot-Repair") instructions, and give that a shot in the meantime.

---

### Post by Bashing-om on 2017-02-08
ray-3; Well ..

we try and boot the system .
In the transfer of the hard drives, is the problematic drive installed as the 1st drive on the buss - such that it is identified as 'sda' ?
then from the liveUSB, booted to the boot options screen try and see what results from the option " boot from first hard drive " ?
else, can you boot the problematic system to the grub boot menu ?

From the install grub boot menu we can attempt to boot the system and if not booting perhaps get some hints why it fails ,

if at 1st we do not succeed
[INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT]

---

### Post by ray-3 on 2017-02-08
[COLOR=#000000]Bashing-om,

As per my initial post, currently the drive I am attempting to boot from is installed in a test rig. The system is configured to boot from it if there is no USB device to boot from. When I insert the liveUSB, the system boots from it successfully, and the problem drive (a Kingston 480GB SSD) shows up as /dev/sda. The drive has 2 partitiions,  1 is root and 2 is home.

If I boot from my liveUSB and select [/COLOR][COLOR=#000000] " boot from first hard drive "[/COLOR][COLOR=#000000], grub loads, and then when I select any of the grub entries, I see the same error as in the title of this thread.[/COLOR][COLOR=#000000]
If I boot from the problem drive, grub loads [/COLOR][COLOR=#000000]and then when I select any of the grub entries, I see the same error as in the title of this thread.[/COLOR][COLOR=#000000]


Again:[/COLOR][COLOR=#000000]I will set up a Boot Repair USB flash disk as per [/COLOR][these]("https://help.ubuntu.com/community/Boot-Repair")[COLOR=#000000] instructions, and give that a shot in the meantime.[/COLOR]

---

### Post by Bashing-om on 2017-02-08
ross03;  Welp;
Let's see what we can do .

Boot to the grub boot menu in the install, and here 'c' key for a (C)ommand line ,
execute:
```

ls ##to see what partitions are, and if the new syntax is used (hd0,msdos1)
set pager=1
set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
Does it boot ? If not we get any hints of where it fails ?

[INDENT][INDENT]inquiring minds want to know[/INDENT][/INDENT]

---

### Post by ray-3 on 2017-02-08
Following [COLOR=#000000][COLOR=#000000]Boot Repair liveUSB [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000] instructions [/COLOR][/COLOR] [here]("http://help.ubuntu.com/community/Boot-Repair") solved my problems. I have a system that boots again. The log results from Boot Repair are [here]("https://paste.ubuntu.com/23952966/").

---

### Post by Bashing-om on 2017-02-08
ray-3; Outstanding !

You do good work -

boot-repair is some kind of smart, huh .

[INDENT][INDENT]right tool for the right job
[/INDENT][/INDENT]

---

### Post by ray-3 on 2017-02-08
Yes, cleverer minds than mine obviously put boot-repair together :) 

Thanks for all your help. It is really appreciated.

---


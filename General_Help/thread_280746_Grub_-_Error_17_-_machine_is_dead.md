---
title: "Grub - Error 17 - machine is dead"
date: 2006-10-19
forum: General Help
---

### Post by OmahaVike on 2006-10-19
i would be so very appreciative if someone would help me with my latest woes.

i've been running a dual boot of xp pro and 6.06 for quite some time.  i rebooted yesterday and got a grub error of 17.  rather strange how this popped up out of nowhere.

so, i booted into live cd and grabbed some stats.

first of all, my BIOS settings:
```

Boot Order:
Ch1 Master - ST3120814A
Ch1 Slave - WD1600B
Ch3 Master - Maxtor blah blah
Ch2 Master - Maxtor Blah blah

```
btw - how do i find which volumes (/hda, /hdb, etc) these map to??!?

okay, so on to the investigation:

first up....  fdisk -l
```

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id System
/dev/hde1               2       19457   156280320    f W95 Ext'd (LBA)
/dev/hde5               2         559     4482103+   7 HPFS/NTFS
/dev/hde6             560         911     2827408+   7 HPFS/NTFS
/dev/hde7             912       19457   148970713+   7 HPFS/NTFS

Disk /dev/hdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id System
/dev/hdg1   *           1       19457   156288321    7 HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id System
/dev/hda1   *           1        4462    35840983+   7 HPFS/NTFS
/dev/hda2            4463        7012    20482875    f W95 Ext'd (LBA)
/dev/hda3            7013       14593    60894382+  83 Linux
/dev/hda5            4463        7012    20482843+   b W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id System
/dev/hdb1               1       19457   156288321    7 HPFS/NTFS

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id System
/dev/hdc1   *           1       14569   117025461   83 Linux
/dev/hdc2           14570       14946     3028252+   5 Extended
/dev/hdc5           14570       14946     3028221   82 Linux swap / Solaris

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id System
/dev/sda1   *           1       30514   245103673+   7 HPFS/NTFS

```

so it appears that the grub boot is on hdc1.  mounted
and went into /boot/grub.  

next up is menu.lst:

```

--  snip  --
## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-27-386
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-27-386
root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery
mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-27-386
root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-26-386
root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery
mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-26-386
root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-23-386
root=/dev/hdc1 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery
mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-23-386
root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items
below from the Debian
# ones.
title           Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```


so, let's take a looksie at device.map now

```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdc
(hd3)   /dev/hde
(hd4)   /dev/hdg
(hd5)   /dev/sda

```


I'm at a total loss for where to look next.  Please?!?!?  I
can't get to *any* OS on my machine.

Thank you in advance for any and all help you can give.

---

### Post by ReaderRat on 2006-10-20
From GRUB error codes site:
> 17 : Cannot mount selected partition This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.
Hope this helps...

---

### Post by m.musashi on 2006-10-20
Did you make any changes that might have changed where the computer looks for grub or where it points to the files? I know the first HD in grub is usually named hd0. In your case it's pointing to hd2, partition 0. It's unlikely that your linux is installed on partition 0. That could be the problem. You might check out [this](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) page. There is some good info and links to super grub disc. I used that in the past to rebuild grub when it got fried reinstalling windows.

EDIT: from the above linked site:
> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Most commonly this is caused by using the 'root' command instead of 'rootnoverify' when booting Windows having the NTFS file system.
Edit your commands in your menu.lst or grub.conf file with 'rootnoverify' to get rid of this error message.

If you get this error when trying to boot Linux, check your grub conf. or menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct.

You will need Super Grub Disk to boot Linux for you so that you can easily check and repair your operating system's entry in menu.lst.
Super Grub can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...

If you have used hard disk partitioning software recently and you have copied and pasted your partition that contians Grub, it probably has a different partition number now than it had before. You can use Super Grub Disk to re-install Grub. You will also need to edit /etc/fstab if your partition numbers have changed.

---

### Post by OmahaVike on 2006-10-21
yeah, that's the wierd part about it.  i made no changes, i only rebooted.  haven't touched anything at that deep of a level since i set up dual booting six months ago.

i looked up the error prior to posting my plea, which is why i listed the fdisk information and provided the information (always do your homework!).  it appears as if only one linux (grub) partition is in bootable status.  thus, i was able to successfully mount that partition with the ext3 switch and dig out that info.  ext3 should come natural to grub though, right?  or is there a separate mapping which indicates which partition is of which filesystem type?

the fact that i could mount it and work within it is baffling with this particular error message...

or did i miss something in our communications?

---

### Post by m.musashi on 2006-10-21
I didn't mean to imply you didn't do your homework. Sorry. I don't know much about grub myself (although I've learned a bit more in the past couple days :).)
However, I have to admit I'm at a bit of a loss. I don't see anything wrong. It seems that grub is looking for the root partition to boot but not finding - if I understand what the Error 17 message means. I believe this part
```
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-23-386
root=/dev/hdc1 ro single
```
is saying that the root partition is on hdc1 and this
```
   Device Boot      Start         End      Blocks   Id System
/dev/hdc1   *           1       14569   117025461   83 Linux
```
says that indeed hdc1 is the root partition for a linux file system. That should work. The only thing I can think of is that somehow the hdc1 is not the correct partition (perhaps a BIOS change?) or that something on hdc1 is corrupt. Sorry, that's probably not much help.

---

### Post by link141 on 2006-10-21
Have you been running an unactivated copy of windows?  I was, and after a month, the D*mn thing said I needed to activate windows, but I hate Windows, so I didn't really care, and continued using ubuntu.  The next day, *windows* cama cozied (I don't know how to spell) the drive, and corrupted the whole D*mn system. The windows partition was gone, but the remaining linux partitions were damaged beyond recognition to read from >:(.  Now, instead of quietly hating windows, I have to tell everyone!(joke, haha) Is this what happened to you?

---

### Post by Bigbluecat on 2006-10-21
Two things to suggest.

1. Get a copy of Super Grub Disk. Very useful to keep around.
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

2. Follow Herman's guide about manually booting the Kernel from grubs command line interface. This will take you step by step through finding the drives and partitions that contain your Kernel and boot menus.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I found grubs command line extremely useful for diagnosing boot problems as you can use the find command to identify each disk and partition that matters to the boot.

Did you do a Kernel update recently?

Check your menu.lst for groot and kopt. These should point to your root partition and the disk with your kernel. I had a boot problem after a kernel upgrade because these were not set right.

---

### Post by OmahaVike on 2006-10-21
m.musashi - no worries on the "homework" issue.  your comments weren't interpreted negatively.

link - it's a legit and activated license.

bigbluecat - will give Super Grub a try and will report my findings here.

thanks to you all.  more on this as it develops.

---

### Post by OmahaVike on 2006-10-23
i think you were on to something bigbluecat...

yes, apparently my kernel was updated.  i did as you said with super grub, and managed to boot my installed ubuntu (it's alive!).  okay, so i went into menu.lst and saw that none of my OS entries were in there -- wiped clean -- config data was in there, but no OS entries.  hmmmm...  luckily i had a backup copy, so replaced that one with my old copy.  rebooted.  same error.  went to bed.

once again, i'll report more on this as it develops.  thank you for pointing me in a direction.

---

### Post by m.musashi on 2006-10-23
> **OmahaVike said:**
> i think you were on to something bigbluecat...

yes, apparently my kernel was updated.  i did as you said with super grub, and managed to boot my installed ubuntu (it's alive!).  okay, so i went into menu.lst and saw that none of my OS entries were in there -- wiped clean -- config data was in there, but no OS entries.  hmmmm...  luckily i had a backup copy, so replaced that one with my old copy.  rebooted.  same error.  went to bed.

once again, i'll report more on this as it develops.  thank you for pointing me in a direction.

I don't know exactly how super grub works, but I kind of thought it looked at your menu.lst and re-wrote the data or at least pointed to that file. (looking back over this [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) site, it does seem like this is how it works) I just fried my own grub and using super grub it put back eactly what was in the menu.lst - including an entry for a second version of windows that is no longer active but I had not yet cleaned up the menu.lst file.

When you used it, what did your boot menu look like? Was it blank like the menu.lst or did it have entries? What were they and where did they point? It's possible that your menu.lst was somehow corrupted and super grub "re-created" a boot menu that was not corrupted. When you restored the old menu.lst it may have simply replaced the new good version with the corrupted version.

Just a couple guesses that might help you pinpoint the problem - or not. I really don't know the finer details of grub.

---

### Post by TiredBird on 2006-10-23
It appears at least that all of your important data is there. You may have a messed up boot menu or maybe even a bad stage 1 in the MBR but it doesn't look like you have any damaged partition tables so if you don't accidentally overwrite something you can probably recover quite easily.

Be careful not to write anything to your disks unless you are sure of what you are doing!

The boot flag in hdc1 probably doesn't have any meaning. I think boot flags only affect Windows systems. You definitely need one on the main Windows partition which I guess is hda1, but it looks like you have one there.

The Master Boot Record is most likely the first 512 bytes of hda. That is where your Grub stage 1 should be. Grub also uses some more bytes that immediately follow this. None of this should have been affected by Windows but it is possible. When you boot the machine, if Grub is still intact at the front of hda, it should at least load the Grub code and give you some semblance of the menu that is on hdc1, even if that is corrupt. If you can get that far, you can use the Grub command line to finish booting and/or reinstall the bootloader.

However, it sounds as if you are not getting that far which suggests that your MBR has been corrupted. If so, you have to reload Grub into the MBR. I'm going to assume that you need to do that.

Boot from your Ubuntu Live CD. Get the live system running. Then from a command line:```
sudo grub
```That should give you a grub prompt '>'. Enter:```
find /boot/grub/stage1
``` which should tell you every partition, in grub-speak, that has the bootloader information. Hopefully, one of those will be '(hd2,0)' your 'hdc1' partition. Next enter the command, ```
root (hd2,0)
``` assuming it found that as one of your stage1 locations. Then enter ```
setup (hd0)
``` which will put the boot loader at the front of your first drive.

Look carefully at the output from each of those commands. There should not be any error messages. The 'root' command should give you something confirming it found a Linux partition there. The 'setup' command should give you a number of confirmation messages as it looks for and finds each piece it needs. It should end by telling you that the setup was successful. If it doesn't, don't go any further until you eliminate the errors!

You will likely get a message regarding the bios map. Assuming it's the same thing you printed out in your first message, that's to be expected. 

If you can get into that partition, edit your 'menu.lst' file. (/boot/grub/menu.lst). Make a copy of it and then cut it down to one entry, the one necessary to boot that partition. You can add the other stuff later. All you need is one of those blocks that begins with 'title'. None of the rest of the stuff is necessary to make it work.

Then reboot your machine. It should get you into the Ubuntu partition and give you a chance to make the necessary changes.

---

### Post by adrian15 on 2006-10-24
Error 17 comes at you when selecting the Linux option from Grub menu or just after grub booting without any menu for you to see?

Whatever it is the answer for that I would run update-grub from your system, yes, booting first with Super Grub Disk and let update-grub (run sudo update-grub from a terminal) to reconstruct your menu.lst with the values of the upgraded kernel. Reboot with reboot command and you're done.

adrian15

---

### Post by OmahaVike on 2006-10-24
adrian and tirebird...  those solutions do not work either, but i sincerely thank you for trying.  this is getting rather perplexing.  i boot, and it gets to stage 1.5, and then shoots off the error 17.  no menu, nada.

i've tried both of your suggested attempts, even with a truncated menu.lst (where it only lists the one ubuntu OS option) and i'm still getting the same results.

i'm still forging forward with super grub and trying to repair it that way, albeit very meticulously and painfully slowly as super grub is slow moving between menu items and is somewhat cryptic for trying to figure out what i'm up against --egads--.

i'm halfway tempted to throw another drive (that'll be drive #6) in a bay, and install ubuntu from scratch onto that drive in order to simply rebuild the grub installation.

my particular situation is totally crazy.  i've never seen anything like it, *especially* considering that i wasn't jacking around and simply rebooted.  my suspicion is that something happened within w'doze that caused it to malfunction as i haven't been in ubuntu for several days (and reboots) prior.

nonetheless, i'm willing to try anything other than 'rm -fr *'

thanks again for all your help and direction.

btw - that one page on super grub (as pointed out by bigbluecat) is *not* for the weak.  it's a *great* link with *great* information, so i thank you.  still trying to figure out how to rebuild my grub from scratch out of those details.

---

### Post by TiredBird on 2006-10-25
This is quite frustrating for me also. I have been working on another grub problem and it too stalled at about the same point. I have three machines of my own and I'm constantly reorganizing partitions and changing grub and while I get temporarily blocked some times I've always been able to get it working again. 

With all the space you have, cut one of your partitions back a little and make a 2GB partition for testing. Install Ubuntu into that partition and then use it to test your booting and other partition.

Good luck!

---

### Post by OmahaVike on 2006-10-26
Got it!

I ended up wiping one of my 20 gig partitions, and left it unassigned (free).  Installed Ubuntu over that, and it at least has a fresh grub to work from.

I was able to successfully access my w'doze partition and boot just fine.  When I tried to boot into my old Ubuntu install, it gave me a little more description that it was an unknown filesystem type.  I will be playing with the *new* grub menu to see if I cannot manually adjust it to be recognized.

The important lesson here is...  if anyone else rubs up against this problem, and cannot get it solved with any of the above steps, this one worked for me.  Get a cheap/old drive and do a fresh install on that (not overwriting your old install) and you should be able to move a bit forward.

Thanks again to everyone for their help.  It is truly appreciated.

hmmm...  upon looking, everything matches up to the old grub.

very very strange how i can get in using the same grub setting in super grub as what is listed in menu.lst.  very very odd.  i'll keep looking into this and follow up on this thread as i find my way.  best of luck to you all.

---

### Post by TiredBird on 2006-10-26
I am glad that something finally worked. 

Look very carefully at the entries in the old menu.lst, the programs it refers to, (are they really where it is looking), the fstab file on that partition, etc. Something is probably inconsistent someplace.

Compare the working menu, the one from the new partition to the one on the old partition. Try to find what is different. Something IS different or the new one wouldn't be working.

Also, if you have any more than just a passing interest in this, I would suggest that you read up on Grub and the boot process. I'm not a programmer, don't ever look at source code and have never done a 'make'. But trying to understand partitions, Grub and the boot process has helped me immensely. 

Grub is not linux, and was not even written for linux originally. I have a separate partition that is Grub only. No linux or other operating system at all, but it boots linux, windows and all of my operating systems. 

Good luck.

---

### Post by adrian15 on 2006-10-30
> **OmahaVike said:**
> 
very very strange how i can get in using the same grub setting in super grub as what is listed in menu.lst.  very very odd.  i'll keep looking into this and follow up on this thread as i find my way.  best of luck to you all.

This means that this partition has some errors. Depending on which version of Grub you use you can mount it or not (i.e. Super Grub version can mount it). Run a fsck from the new linux that now works to the partition that refuses to boot.

```

fsck -a -y /dev/hdXY

```

where /dev/hdXY is the supposedly corrupted partition. 

If the Linux -> Boot Linux option from Super Grub Disk lets you boot your older (formerly corrupted) Linux from Super Grub Disk you can do Linux -> Fix Boot of Linux and... you'll get restored Grub to the MBR.

You won't get access till the new Linux till you edit menu.lst and add something as: 
```

title MY NEW LINUX
configfile (hd0,6)/boot/grub/menu.lst

```

where we suppose that the new Linux is installed on /dev/hda7 .

Tell us if everything worked ok.

adrian15

---

### Post by OmahaVike on 2006-11-03
fudge....

something happened between my previous post and here (following directions) and now i cannot get into my ubuntu at all.  will be following up as i move along.

notice how i said "my ubuntu"?  boy, have i been whipped, or what?  heh.  details as they follow.

---

### Post by OmahaVike on 2006-11-06
alright...  although it has been weeks working on this particular issue, i must admit that my dedication to the task has been rather limited.

something had happened between those prior couple of posts which would appear to attempt a linux boot, but then drop out into a grub shell.  prior to this, i would boot successfully into ubuntu via super grub.

thus, i surrendered myself to failure and reinstalled.  will be rebuilding everything from scratch yet again.

my followup question would be centered around protecting this from happening again.  while i do not know exactly what happened, i am highly suspect that something in 'doze jacked with the boot sector and/or the filesystem itself.

is there any way to lock this down from occurring again?

thanks again to all.

---

### Post by OmahaVike on 2006-11-18
for those of you who are following this series...

i installed ubuntu on another disk that i had available, and it all came back up (dual booting to 'doze too).

so, i got a wild hair, and tried to install ubuntu back to the disk i had originally had problems with (the FULL dedicated disk).  installation went fine without incident, but upon reboot i got the same grub error as originally reported.  i even went so far as to delete the partitions in gpart before installing.  grrrr....

this, in and of itself, reeks of "bad disk hardware" problems, although none is reported by the ubuntu install...   hmmm.

so, where i am at is:  i reinstalled ubuntu to that other disk just to get my box moving again.  okay, all is good.  boot back into 'doze and am formating that disk as NTFS.  powerquest PM8 is showing no problems, and neither is the built-in compmgmt.msc disk evaluation as well as LavaLys Everest.  i'm hoping that the 'doze NTFS formatting will rearrange the disk/sectors accordingly before i try to install on that hardware again.

btw -> "fsck -fy /dev/hdc1" (where the original install and reinstall lived) from the Ubuntu liveCD didn't do squat or return any errors before or after the reinstall on the troublesome disk.

(say out loud like dennis hopper in Easy Rider) this is really out there, man!

as per usual, more on this as the story develops...

---


---
title: "Windows 8 is not in GRUB"
date: 2014-02-26
forum: General Help
---

### Post by xepherxv on 2014-02-26
i am sorry for a re-post, my last post was removed due to something i said -- i will not make this mistake again 

heres what it said 

[COLOR=#000000]i created a new partition just for Ubuntu, but when grub appears it only shows diffrent versions of linux and ubuntu, i still have the 1.5terabyte partition windows would be on, but i cant seem to access it, ive tried everything, the issue is that i dont have a disc or a key (i used my freinds) so i cant get a direct iso to create a bootable usb for windows 8.1[/COLOR]

[COLOR=#000000]does anyone have any ideas -- i cant afford to lose windows! i have everything on that thing! thats why i made a new partition![/COLOR]

[COLOR=#000000]im just scared depressed and generally out of ideas.[/COLOR]

[COLOR=#000000]anyone out there that can help?[/COLOR]

[COLOR=#000000]i have a uefi bios -- when installing ubuntu i read a tutorial for windows 7 evidently a huge mistake[/COLOR]


[COLOR=#000000]heres what i tired:[/COLOR]

[COLOR=#000000]Boot Repair: 3 times heres a summary [/COLOR]http://paste.ubuntu.com/7000484/
[COLOR=#000000]
Simply Restarting: no cigar

attempting to execute windows boot manager: it seems to just make my bios flash off and back when i click it, thats it tho

i am trying my hardest to get a windows 8 disc (legally), i do not have the key or the disc with me anymore

i do not know much about python or coding in general, 


well thanks for any help ^.^;

[/COLOR]

---

### Post by NilPointer on 2014-02-26
Well, if you didn't do anything to windows partition (such as formatting), then I guess you can relax. Installing Ubuntu on separate partition would not destroy windows, it shouldn't even write anything to it's partition, so windows should be still there with all data intact.

Then, what do you mean by "you couldn't access" partition? It appears in file manager, but it doesn't mount and shows error? There is chance that you didn't shutdown Windows properly and Linux NTFS driver won't touch this partition to avoid data loss. This can usually be fixed with chkdsk (which can be difficult, considering you can't boot windows).

If Windows partition is inaccessible from Linux, it's only natural that GRUB doesn't show Windows. I suppose you'll need to run disk check on Win partition from Windows 8 CD to fix possible FS problems (without installing, if possible, because that'll wipe GRUB and you'll need to repair it) and if partition will be mountable in Linux after that - then updating GRUB menu will probably add Win 8 to boot menu.

---

### Post by twilkins111 on 2014-02-26
Maybe the hd0,0 is allocated to default HDD configuration!! and your Win 7 is installed in (hd0,1)


just once try to find the partition where ubuntu is installed i.e. boot from live disk and

open terminal
issue commands:

 	

 	[TABLE]
 	[TR]
 		[TD="class: bbcodeblock"] 			 				sudo grub 			 		[/TD]
 	[/TR]
 	[/TABLE]
 
 	

 	[TABLE]
 	[TR]
 		[TD="class: bbcodeblock"] 			 				find /boot/grub/stage1 			 		[/TD]
 	[/TR]
 	[/TABLE]
 
this will return your ubuntu partition

now quit grub

 	

 	[TABLE]
 	[TR]
 		[TD="class: bbcodeblock"] 			 				quit 			 		[/TD]
 	[/TR]
 	[/TABLE]
 
now figure out the rest of the partitions using command

 	

 	[TABLE]
 	[TR]
 		[TD="class: bbcodeblock"] 			 				fdisk -l 			 		[/TD]
 	[/TR]
 	[/TABLE]
 
the output for this command will explain you where your Ubuntu and win 7 are installed


Note:: /dev/sda2 = (hd0,1)

and configure rootnoverify     (hd0,0)  accordingly....

---

### Post by xepherxv on 2014-02-26
> **twilkins111 said:**
> 

Note:: /dev/sda2 = (hd0,1)

and configure rootnoverify     (hd0,0)  accordingly....


uhh....

will this be easy to find once im in, im sorry im brand new to this. also, im running windows 8.1, not windows 7 if it matters

---

### Post by xepherxv on 2014-02-26
i got a bootable usb i hit repair, but this happns " The drive where Windows is installed is locked. Unlock the drive and try again"

---

### Post by xepherxv on 2014-02-26
ok, i just found this on my linux [http://gyazo.com/14b063527eaf9887f804f431ceaef11a](http://gyazo.com/14b063527eaf9887f804f431ceaef11a) the "unallocated" is where windows is suppose to be, this might be part of it being locked? theres no way it wiped my other partition in the 5 mins it took to install linux

---

### Post by oldfred on 2014-02-26
Gparted may not show it if it needs chkdsk from a Widnows reparCD or flash drive or if the hibernate flag is set.
If you know it needs chkdsk after a resize or forced shutdown run that first.

Post this:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by xepherxv on 2014-02-26
> **xepherxv said:**
> 

[COLOR=#000000]Boot Repair: 3 times heres a summary [/COLOR]http://paste.ubuntu.com/7000484/
[COLOR=#000000]

[/COLOR]
you talkin about that?

---

### Post by oldfred on 2014-02-26
Missed it in first post as it did not appear as the normal link.

You must have used the erase entire drive option. There is only Ubuntu on drive, no NTFS partitions.

---

### Post by xepherxv on 2014-02-26
so windows is gone?

---

### Post by Bucky Ball on 2014-02-26
According to this:

[http://paste.ubuntu.com/7000484/](http://paste.ubuntu.com/7000484/)

... yes. As oldfred said, there is not an NTFS partition, only a Linux EXT4 partition (which Windows can't be installed on), a BIOS boot partition and /swap.

```
sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 390340800 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 12.04.4 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 
```

And that's all she wrote ...

---

### Post by xepherxv on 2014-02-26
well........

(swear word)

guess im wiping my harddrive

---

### Post by xepherxv on 2014-02-26
WAIT WAIT WAIT


cmd says its locked, so its possible that its just not detecting that anythings there!


right!? right!? please be right? ;~;

---

### Post by Bucky Ball on 2014-02-26
Don't like your chances from what you bootinfoscript is telling us:

```
=================== blkid:
/dev/sda1: UUID="d3fdfa0d-84ad-4c47-9aa2-df9a2d190c70" TYPE="ext4"
/dev/sda3: UUID="1306513d-9842-407b-83f1-11f947c7fab7" TYPE="swap"

_1 disks with OS, 1 OS : 1 Linux,_ 0 MacOS, _0 Windows_, 0 unknown type OS.

```

Should pick up everything there, locked or not. (Underlines mine.)

Win was installed in UEFI mode. You installed Ubuntu in non-EFI mode. This would have not given the option to install alongside Win (as it wouldn't have seen Win as you weren't in EFI) and is notorious for fooling users into wiping their drive. Your only options probably would have been 'Use entire drive' or 'Something Else', missing the 'Alongside' option. Did you select the latter rather than 'Something Else'?

Where are you finding it says 'locked' and what partition is locked? It's not showing in bootinfo.

---

### Post by xepherxv on 2014-02-26
well, even if the OS isint there, will my files will? .remember. i had used an entire TERABYTE and a quarter...

yet

its all gone with a simple 5 min install of linux?

that makes no sence!

i dont mind if i have wipe the whole drive as long as i can retrieve my files i never backed up (actually i put them in a google drive folder on my desktop, but silly me never ran the app -- so its not in google drve because they never uploaded, so dont yell at me saying i should of backed them up! i tried! im not the sharpest tool)

---

### Post by Bucky Ball on 2014-02-26
Some of your data may be there, but your best chance of retrieving anything useful is to stop using that disk now and start researching on another machine if possible. The more you use that machine, the more chance your data will be overwritten. You see, the info isn't actually erased, the areas where it is stored are marked as 'writable'; in other words, that machine considers those areas fair game if it needs to write new data. They are 'usable'. 

I'm no expert on retrieving lost data but there's plenty about here who are. Hopefully someone will jump in but, to be honest, this is swinging off-topic of your original issue and you would greatly improve you chances of getting help with it by posting a new thread with an appropriate title, like 'Help retrieving lost data.' Add a link back to this thread so people might see the full story and a link here to there if you wish. [HERE'S]("https://help.ubuntu.com/community/DataRecovery") a start and further food for thought [HERE]("https://duckduckgo.com/?q=retrieve+lost+data+ubuntu").

You're stumbling block could be that Ubuntu has completely reformatted the disk/partitions to EXT4 from NTFS. Doubt they'd be anything there after that, but again, I'm no expert in this area. Good luck.

---

### Post by xepherxv on 2014-02-26
well im wiping it on friday (thats when i can get to my fathers house go i can get an internal to external usb harddrive converter to retreive my files) i think its safe to say 500gb is large enough so im in the safe zone untill then, im not downloading anything massive. 


anyways thanks for all your help! 


you guys are the greatest i wish i could just hug each and every one of you

---

### Post by Bucky Ball on 2014-02-26
*Blush* We try. :redface:

Just out of curiousity, could you launch Gparted, take a screen shot of it when looking at sda, and attach it to a post? Use the 'Adv. Reply' button, click the paperclip icon and attach the pic that way rather than inserting it in you post. Thanks.

---

### Post by xepherxv on 2014-02-26
im sorry sda?


im new to this

---

### Post by Bucky Ball on 2014-02-26
Oh, sda is the disk so it is the one that should be showing when you open Gparted. If you had two disks the second would be sdb, if you get my drift. You'll notice in your bootinfo that your Ubuntu is on sda1, meaning first partition, first hard drive.

sda in Win language = hd0. sdb would = hd1. Hope that helps.

---

### Post by xepherxv on 2014-02-26
This? (the image addy this is very odd to me sorry if you dont get it - ill try again if you dont)

---

### Post by Bucky Ball on 2014-02-26
Ok, so the 1.34Tb 'unallocated' section is where Win8 should be? There could be hope yet, then. If it is unallocated, as I said, it may just be marked as available but the info still there. Testdisk may even be able to resurrect the partition. None of this is a certainty, of course. See [HERE.]("https://help.ubuntu.com/community/DataRecovery#Testdisk")

PS: Your / partition really only needs to be about 20Gb and store your personal data on another partition. That way, if the OS dies for any reason, at least your data is not on the / partition and you can safely (hopefully!) reinstall.

---

### Post by xepherxv on 2014-02-26
ok, i will definitely store my files in a safer manner when i get back to windows, i am thinking about buying a new hard disk, a small one, like 50gib just for personal data


and yes windows 8 should be there


also testdisk?

im sorry ;~; i feel so dumb

---

### Post by xepherxv on 2014-02-26
ok, i will have to work on this in the morning, i did not realise my time i must sleep, so sorry if i dont respond in a speedy manner

---

### Post by NilPointer on 2014-02-27
> **xepherxv said:**
> also testdisk?

im sorry ;~; i feel so dumb

Don't worry, we all were new to the Linux at some point. ;)

testdisk is basically a program that can (attempt to) restore lost partitions and/or fix some corrupted data in their file systems. It can also undelete files. If Windows partition was only marked as unallocated in the partition table without actually wiping the data, there is a chance testdisk could determine lost partition properties and recreate missing partition entry bringing partition back. It runs from a terminal and has a relatively simple text-menu interface.

---

### Post by xepherxv on 2014-02-27
i cant really use it since my drive is write protected now :/

any idea on how to un-write protect that partition?

---

### Post by NilPointer on 2014-03-02
> **xepherxv said:**
> i cant really use it since my drive is write protected now :/

any idea on how to un-write protect that partition?

Well, you need to run it with sudo, this program requires root priveleges to get access to drive.

---


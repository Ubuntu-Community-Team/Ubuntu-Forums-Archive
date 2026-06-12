---
title: "Please help with restoring GRUB (dual boot system)"
date: 2006-12-14
forum: General Help
---

### Post by inspired on 2006-12-14
Hello,

**THE SETUP:**
Dual booting Windows XP and Ubuntu

**THE PREAMBLE:**
I have managed to stuff my grub boot system. I am not sure what happened. Essentially I removed a few drives in order to plugin one I needed to format. When I put all the drives back into their original position the system starting booting straight into Windows only.

I have found a lot of info on how to reinstall GRUB. Different people suggest different things. I have not found any info that actually explains what each step is about. Therefore I have found it challenging to apply the suggestions to my particular setup.
[B]
THE DRIVE DATA:
[/B]
fdisk -l returns the following info:
```
Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1157     9293571    7  HPFS/NTFS
/dev/hda2            1158        2432    10241437+   7  HPFS/NTFS
/dev/hda3            2433        4982    20482875    7  HPFS/NTFS

Disk /dev/hdb: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1657    13309821    7  HPFS/NTFS
/dev/hdb2            1658        3321    13366080    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          12       96358+  83  Linux
/dev/hdc2              13         137     1004062+  82  Linux swap / Solaris
/dev/hdc3   *         138        1353     9767520   83  Linux
/dev/hdc4            1354        9729    67280220    5  Extended
/dev/hdc5            1354        3177    14651248+  83  Linux
/dev/hdc6            3178        4393     9767488+  83  Linux
/dev/hdc7            9001        9729     5855661    b  W95 FAT32
/dev/hdc8   *        4394        9000    37005696   83  Linux

```

I know that /dev/hdc1 has a grub folder in it, with my menu.lst in that.

When in GRUB, the command "find /boot/grub/stage1" returns "(hd2,2)" which is "/dev/hdc3". I don't think this is where it should be pointing.

I think GRUB has ended up in there when I tried to fix this a few weeks ago. I note that everything in the grub folder at /dev/hdc3/boot/grub all has Nov 21st as the created date, and that's about when I first tried to fix this.

The contents of /dev/hdc3 is:
```

ubuntu@ubuntu:/mnt/hdc3$ dir
bin                      etc                Internet\ Mail    ntfs   sys           vmlinuz.old
boot                    fuse              lib                   opt    tmp           windata
boot\ backup        home            local                proc   usplash_fifo
cdrom                 initrd             lost+found       root   usr
debootstrap         initrd.img      media              sbin   var
dev                     initrd.img.old mnt                  srv    vmlinuz

```
The contents of hdc1 is:
```

ubuntu@ubuntu:/mnt/hdc1$ dir
abi-2.6.15-26-386     config-2.6.17-10-386      lost+found                System.map-2.6.17-10-386
abi-2.6.15-27-386     grub                      memtest86+.bin            vmlinuz-2.6.15-26-386
abi-2.6.17-10-386     initrd.img-2.6.15-26-386  sbm.img                   vmlinuz-2.6.15-27-386
config-2.6.15-26-386  initrd.img-2.6.15-27-386  System.map-2.6.15-26-386  vmlinuz-2.6.17-10-386
config-2.6.15-27-386  initrd.img-2.6.17-10-386  System.map-2.6.15-27-386

```

/dev/hda1 is where Windows XP is installed.

**THE ATTEMPTED SOLUTION:**
Back on Nov 21st I did attempt to fix this using some grub reinstall instructions somewhere on this forum. That failed and I left it until now.
Today I tried to do the following:
1) grub> root (hd2,2)
2) grub> setup (hd2,2)

I choose hd2,2 because that is where "grub> find /boot/grub/stage1" indicated grub was located. As mentioned, I have since figured that is most likely only the result of my previous recovery attempt.
(edit) BTW... after this the system now boots into a GRUB terminal. No XP boot and no Linux boot. Hmmm...

**THE WAY IT SHOULD BE:**
As far as I can tell hdc1 is my linux boot partition. This is where the correct menu.lst file is with all my boot menu settings.

How do I go about getting this to work again?
I would really appreciate some clear, step-by-step assistance. I am sure it will be of use to other people also (to have it spelled out with some explanation as to what each step is doing)

With thanks,

Jonathan

---

### Post by Herman on 2006-12-14
Hello inspired,
Here's a how-to I made, try this link and see if it helps you,

                                      Re-install Grub with a GRUB shell eg; with Live CD.......................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

If you think it needs more explaining I can edit that how-to with your help.
Actually, as I look at it again now, maybe I can already think of a few improvements. See what you think...

Regards, Herman :D

---

### Post by inspired on 2006-12-14
Thanks Herman,
That's a nice howto you've put together. I like the fact you explain what each thing is doing. Makes a world of difference.

One issue I (may) have is that on my dedicated Linux boot partition (/dev/hdc1 -- 98mb) the grub folder is not within a boot folder. I note the "grub> setup (hd0)" generates the following:
```

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 d (hd0) (hd0)1+16 p (hd2,0)/grub/stage2 /grub/me
nu.lst"... succeeded
Done.

```
You will see it tried to find /boot/grub/stage1
I note it did then find stage1 and 2 in the correct location (/grub), so this is why I say "may) be a problem. I shall now leave this livecd session and reboot. I shall check back in hopefully from my Ubuntu and not this cd based one!!

Cheers,

Jonathan

---

### Post by Herman on 2006-12-14
:D Okay, good luck, I'll be here....

---

### Post by inspired on 2006-12-14
Okay, no idea what happened.
When I rebooted I got a prompt I have never seen or heard of before:
```

EL] to enter SETUP(spade)
```
Where I have put (spade) there was in fact a little spade symbol as seen in a pack of playing cards. Odd.

So, now I am not sure what happened.

QUESTION
In GRUB, when I type in ROOT (HD2,0) is that then telling grub that this is the location of my GRUB boot files, so that when I later type in SETUP (HD0) is will in fact install the grub loader to HD0 with a pointer to the grub files on HD2,0?

Does it matter that my grub files are in /grub and not /boot/grub ?

So... here I sit in a liveCD session again. Oh well... I know I'll figure this out one way or another.

With thanks,

Jonathan

---

### Post by inspired on 2006-12-14
I have copied the contents of /hdc1/grub into /hdc1/boot/grub to see if this makes any difference.
Then in grub I did:
```

grub> find /boot/grub/stage1
 (hd2,0)
 (hd2,2)

grub> root (hd2,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd2,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub>

```

BTW... does my linux boot partition need to be ACTIVE (have the boot flag on it)? I notice that /dev/hdc3 has a boot flag on it. As does hdc8 and hdb1 and hda1

Rebooting to see what happens. I don't imagine it will because the previous grub SETUP seemed to work and it found the grub data in the /grub folder.

HERMAN, I have to go out shortly (been at this for three hours this morning!!). So if you reply some time soon, it may be an hour or two before I get back to you. I am not sure what timezone you are in. I am in New Zealand.

Regards,

Jonathan

---

### Post by Herman on 2006-12-14
> Okay, no idea what happened.
When I rebooted I got a prompt I have never seen or heard of before:
     Code:
     [LEFT]EL] to enter SETUP(spade)[/LEFT]
 
Where I have put (spade) there was in fact a little spade symbol as seen in a pack of playing cards. Odd.

So, now I am not sure what happened. Well it looks like your computer has tried to boot and now you are getting an error from the BIOS.
Did it say 'press Del to enter setup' ?
Either Grub hasn't installed or it has installed to the wrong hard disk or your BIOS is not set up to boot from your first hard disk.

---

### Post by Herman on 2006-12-14
>  QUESTION
In GRUB, when I type in ROOT (HD2,0) is that then telling grub that this is the location of my GRUB boot files, so that when I later type in SETUP (HD0) is will in fact install the grub loader to HD0 with a pointer to the grub files on HD2,0?

Does it matter that my grub files are in /grub and not /boot/grub ?

So... here I sit in a liveCD session again. Oh well... I know I'll figure this out one way or another. Just a note, I'm not sure if it has anything at all to do with any problems you might be having, but be sure you pay attention where capital and lower case letters are used in Linux. Linux is case sensitive, not like some other operating systems, so if you try to use capitals where lower case letters are required, you'll have trouble. I'm pretty sure you already know that though, or you wouldn't have gotten this far.

Yes, when you type, root (hd2,0), it tells grub which partition it is to look for the particular  grub files whose stage1 you want installed to MBR, and stage1_5 written to the next 15 sectors of your disc's first track.
In your example, this would be your third hard disk, first partition.
Some people like me have several different Ubuntu operating system on various disks and partitions and Grub needs to be told exactly which one we're talking about.
You could also try (hd2,2) if you like, and see what happens. 

When you type in, setup (hd0) that specifies which disk's MBR you would like Grub's stage1 installed to. Many computers have two or three or four hard disks, and Grub can be installed to MBR on any of those disks, or to MBR on a floppy disk or to a USB disk if the user specifies any of those.
It is usually easiest and best to install grub to MBR in the first hard disk, as that is where the BIOS automatically looks unless it is specially configured to look somewhere else instead.
> HERMAN, I have to go out shortly (been at this for three hours this morning!!). So if you reply some time soon, it may be an hour or two before I get back to you. I am not sure what timezone you are in. I am in New Zealand. Okay, I will go too then, I'm in outback Queensland, Australia, so our time zones aren't too far apart. I'll check back here later on....
Regards, Herman :D

---

### Post by Herman on 2006-12-14
```
Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          12       96358+  83  Linux
/dev/hdc2              13         137     1004062+  82  Linux swap / Solaris
/dev/hdc3   *         138        1353     9767520   83  Linux
/dev/hdc4            1354        9729    67280220    5  Extended
/dev/hdc5            1354        3177    14651248+  83  Linux
/dev/hdc6            3178        4393     9767488+  83  Linux
/dev/hdc7            9001        9729     5855661    b  W95 FAT32
/dev/hdc8   *        4394        9000    37005696   83  Linux
```
inspired,
I notice you have more than one bootable flag set on your third hard disk, that might be the cause of your BIOS error message too.
To make sure that isn't a problem, you should run your favorite hard disk partitioning software and remove one of those boot flags. Almost any disk partitioner can be used for that. GParted in the LiveCD should work fine.
Regards, Herman :D

---

### Post by Sef on 2006-12-14
> GParted in the LiveCD should work fine.

I agree.  You can download [GParted]("http://gparted.sourceforge.net/livecd.php") as a stand alone Live CD too.

---

### Post by inspired on 2006-12-14
I'm back.
Thanks Herman for the close attention to this. Much appreciated. SEF, thanks for your input too.
 
Okay... yes, I too would like to clean up the excess boot flags. I did already try to do this with gparted yet somehow failed to see the option for changing the boot flag. I shall look up a help file on gparted and figure that out.

What you have explained re the way Grub works is as per what I thought. Nice to have that confirmed. Not so nice to find out I did it all the correct way--which means there ain't some simply folly on my part we can correct and get the show on the road. Oh well.

Yes, I am aware of the case sensitivity of Linux. Thanks for the attention to detail.

The error message says exactly as indicated (no typos, it's just an odd error message)
```
EL] to enter SETUP(spade)

```(with the word SPADE being a little asci picture of a spade)

I shall try changing the boot flags and see if that helps.

Back soon...

J ;)

---

### Post by inspired on 2006-12-15
> **Sef said:**
> I agree.  You can download [GParted]("http://gparted.sourceforge.net/livecd.php") as a stand alone Live CD too.
I have found that the version of gparted on the livecd was for some reason not letting me change the flags. It was version 0.1 (or something like that). I updated it to v0.2.5 and this fixed the flag editing issue.

In the mean time I also learnt how to do it using fdiskk. It was easy and quick. Here is the info on that for those who are interested:
Changing Boot flag with Fdisk
```

HOWTO: Manually set the boot flag with fdisk.

Use the command fdisk -l to see a list of the device name(s) of your hard drive(s).

Here an example: An IDE hard drive is connected at the primary IDE controller as Master:

fdisk /dev/hda
(this opens the fdisk command prompt)

Now type in successively:

a to activate the partition
      (it will ask you which partition by number)
1 to choose the first partition
w to write the changes 

```

I have not yet rebooted to see if these changes helped. Doing that now.

---

### Post by inspired on 2006-12-17
Hi Folks,
I am still trying to resolve this grub issue.
At present the outcome is that when I boot I get the message:

```
EL] to enter SETUP(spade)
```
(with the word SPADE being a little asci picture of a spade - as from a deck of playing cards)

I have tried booting with the supergrub disk. I have also tried using the gparted boot disk.
The super grub disk finds my windows and Ubuntu partitions, but I can not boot Ubuntu from there.

I'd really like to sort this out, and I REALLY don't want to reinstall Ubuntu. That's a major reason I switched to Linux in the first place...to get away from the Windows reinstalls I had to do every 8-12 months due to it having performance issues over time.

If you have any idea what step I can take please advise.

With thanks,
Jonathan  :confused:

---

### Post by Herman on 2006-12-19
Hello inspired,
When you used your Super Grub Disk, did you try using the 'Advanced' menus?
The Gnu/Linux menus and Windows Menus are for when you only have a single hard disk with a simple single or dual boot installation.
Since you have three hard disks, you need the 'Advanced' menus , which are a little slower to use, just because they have to ask more questions. Try going 'English Super Grub Disk'-->'Advanced'-->'Gnu/Linux Advanced'-->'Boot Gnu/Linux Directly'-->'Different root and boot partition', and select hd2 as your hard disk for boot, and partition 1, then tell Super Grub Disk if your disk3 is an IDE disk or SCSI (Sata), hten select (hd2) , and partition (hd2,2) if you think that's your root partition. If you guessed correctly, Ubuntu should boot.
If it doesn't , try again but specify different partitions, or try 'same root and boot partition' and see if you can boot a partition on disk 3 that way.
You might get it first time or you might need to use a little trial and error, but you should be able to get Ubuntu to boot. 

Another thing that you can try with Super Grub Disk is to press your 'c' key from a menu and get grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). Try going through some of the steps in that link I just gave you and see if anything there helps you.

Also, you should be able to press your F8 or F12 key (depending on what brand of computer you have), when your computer is booting up for a menu where you can select different hard disks or other bootable devices to boot. Try selecting your other hard disks and see what happens. 
You can install Grub to the MBR on you second or third hard disk too, if you want, and then boot from that MBR, since your first hard disk doesn't seem to be working for some reason.

One of these things should help or at least give us some valuable clues about what's wrong and how to fix this.

Regards, Herman :D

---

### Post by inspired on 2006-12-21
Thanks Herman,
I'll try out what you have suggested and get back to you.
I really do hope I can sort this out. I don't mind reinstalling Windows (real use to that "feature" by now :rolleyes: ), but reinstalling Ubuntu I'd rather avoid... simply because that's the system used 95% of the time on this machine and it's have 1.5 years of customisation and tweaking etc. whilst I've explored Linux and the like.

Will be back soon.

Jonathan :KS

---

### Post by inspired on 2007-01-13
THE UPDATE::
I have been unable to correct this issue.
I am able to boot into Windows using the Advanced Boot (Windows) on the SuperGrub disk, but I am not able to boot into Ubuntu.

Nothing has changed on the Ubuntu disk, that I am aware of. In fact I completely removed the HDD whilst formating another new hdd. So the linux hdd was not even present. Yet upon putting it back in it is unbootable. All the files and partitions are there and look normal.

What else can one do? I am ignorant of what could be so sensitive with Ubuntu/linux that it is now unrecoverable. Does anyone with more Linux knowledge have any ideas?

With thanks,

Jonathan

---


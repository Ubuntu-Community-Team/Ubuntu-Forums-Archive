---
title: "Ubuntu Fails to Boot, Only Launches GNU GRUB"
date: 2015-01-04
forum: General Help
---

### Post by Ubultron on 2015-01-04
Hi, guys. I'm having a problem where I turn on my computer, and the operating system seems to fail to boot (I have Ubuntu 14.04 LTS). All it does is go into something called GNU GRUB. Now, I am not well versed at all in Linux, but it said I could access the list of available commands if I pressed the Tab key, which I did, and upon entering the "boot" command, it said it couldn't do it because I had to load the kernel first.

Like I said, I'm not Linux-savvy, and I have no idea why this happened. Yesterday I installed the ZSNES, and PCSX-2 emulators, so that's about the last major change (so to speak) I made to the OS. Today I turned it on, browsed around for SNES game ROMs, and then launched Transmission. I went away, then came back and noticed that for whatever reason, the stuff I was downloading had stopped and was highlighted in red, so I figured I could close the software and relaunch it to correct whatever had gone wrong, but as soon as I did so, the whole system got very slow and Transmission itself ultimately had to be force-quit. So I restarted the computer, and that's when it began going into that GRUB thing. I turned the computer off and back on, but it keeps doing that.

Any suggestions would be very welcome, as I have no idea what happened, or why. Thanks, guys.

---

### Post by cariboo on 2015-01-04
Try starting in recovery mode, to see if there are any messages indicating what the problem is.

---

### Post by oldfred on 2015-01-04
Force quit may have corrupted file system.

You may need to run fsck.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

And always best to remember the elephants:
      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by Ubultron on 2015-01-04
I tried starting a live-disc session, but it never goes past a black screen. I also found [this guide]("http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/"), which apparently addresses my specific issue, but I can't go through with it because for some reason, GRUB says the "linux" command can't be found whenever I try the following:

[COLOR=#333333][FONT=Courier News]grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1[/FONT][/COLOR]

This is ridiculous; in the three (or so) months that I've been using Ubuntu, it's been complication after work-around after problem...

---

### Post by oldfred on 2015-01-04
If file system is corrupted then it cannot see files in it. Did you run the fsck?

This uses links to most current kernel. change sda1 and hd0,1 to partition where your install is, if not sda1 as shown in this example:

 set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

---

### Post by Ubultron on 2015-01-05
> **oldfred said:**
> If file system is corrupted then it cannot see files in it. Did you run the fsck?

This uses links to most current kernel. change sda1 and hd0,1 to partition where your install is, if not sda1 as shown in this example:

 set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

I haven't given fsck a run yet, oldfred. I'm a total newbie, so I don't know how to manually unmount the drives, and I read that running fsck without having previously done so is a bad idea. I also haven't tried those commands you listed there, but that's because I'm only seeing your reply until now. I'll be sure to try it out.

What I did do, however, is download the [Boot-Repair-Disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") and give that a try. Unfortunately, I'm not having any luck with it either. Here's an error report from one of the scans I ran: [paste.ubuntu.com/9674967]("http://paste.ubuntu.com/9674967")

What can you make of it? I'm getting a bit worried now. I have a lot of data in there that had I haven't backed up.

---

### Post by oldfred on 2015-01-05
If you have booted Boot-Repair and not clicked on any partitions, then they are not mounted. Boot-Repair typically mounts them to see what is in them and then unmounts them unless you have issues.
It looks more like you have major issues with your sda5 NTFS partition. Either you left it hibernated or it need chkdsk. But as a logical partition it is not directly bootable. Windows has to have a primary partition to boot from. When you installed Ubuntu did you delete a small 100MB partition that was the Windows boot partition?

It looks normal. You can reinstall grub to MBR with Boot-Repair. That sometimes works. Or you may need to use advanced mode and do a full uninstall/reinstall of grub. That resets everything.

---

### Post by Ubultron on 2015-01-05
Oh, gotcha. I'll try running fsck from Boot-Repair's terminal. Is there a specific line I should input, or is it alright if I just type "fsck" and hit ENTER?

About that 100 MB partition... yes, I deleted it. The partition itself doesn't have Windows installed, though; I only use it to store data, but it *is* NTFS... Is that what's preventing Ubuntu from booting? Also, how can I run chkdsk on it? Can that be done in Linux?

Now, in case that the filesystem has been corrupted beyond repair, is it possible to recover data from a partition if the filesystem is damaged? Could it be done with Knoppix, or something like that?

---

### Post by oldfred on 2015-01-05
Copy & paste the fsck commands I posted in post #3 in terminal.

You have to have at least a 100MB NTFS primary partition with the boot flag so you can boot Windows. And you need a Windows repair CD or Flash drive or a full installer and go into repair console to run chkdsk on the NTFS partition and make repairs so it adds back the boot files.

If you deleted files you need, you may be able to use testdisk or photorec. Testdisk is to restore deleted partitions, but they cannot overlap any existing partitions. Photorec just scans a drive for anything that looks like a file. It took me overnight to scan my system and it was a small drive.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

            [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Ubultron on 2015-01-06
So I ran fsck from the Boot-Repair's terminal and this is what I got:

[FONT=verdana]lubuntu@lubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1/
e2fsck: Not a directory while trying to open /dev/sda1/
/dev/sda1/: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>[/FONT]

Does this mean I'm completely screwed? I tried entering sudo e2fsck -b 8193 /dev/sda1/ and sudo e2fsck -b 32768 /dev/sda1/ but I got the exact same response. I'm not sure if that was the correct way to do it, though.

Also, I went into the advanced options of Boot-Repair and set it to purge and reinstall GRUB, but it couldn't complete the process. It stops and gives me a prompt to enable some repository on sda1 (where my Ubuntu install is). But how could I do that if I can't even access the OS?

---

### Post by oldfred on 2015-01-06
Try again without / at end.

If partition is same as example just copy & paste from example. Or edit to correct partition but do not add / at end.

Also fsck is only for the ext family of ext2, ext3 & ext4. If NTFS, you must use chkdsk from a Windows repair disk. This will show formats.
sudo parted -l 

sudo e2fsck -C0 -p -f -v /dev/sda1

---

### Post by Ubultron on 2015-01-06
I tried again without the "/" at the end and it finally reacted, but it gave me an error. It said that I had to run fsck manually, so I used the other command you had suggested (not the one that started with "man," but the other one). I think it found a lot of errors (and automatically rewrote them). This is what I got at the end. Sorry for sounding like an idiot once again, but what does it mean? :P

[FONT=lucida console]/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

      268066 inodes used (21.92%, out of 1222992)
         167 non-contiguous files (0.1%)
         259 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 221259/29
     1593896 blocks used (32.65%, out of 4882432)
           0 bad blocks
           1 large file

      172074 regular files
       32273 directories
          57 character device files
          25 block device files
           0 fifos
  4294967260 links
       63625 symbolic links (46685 fast symbolic links)
           3 sockets
------------
      267102 files[/FONT]

---

### Post by Ubultron on 2015-01-06
Oh, I forgot to mention: I restarted the computer afterwards and for a moment it seemed like it was going to finally launch the OS. You see, when I turn on my computer, right when the OS boots up, there's like a purple frame that appears for a couple of seconds onscreen. It did that this time, and then it went black, but it looked like it was loading something. Then a message appeared saying that it had failed to load filesystems, and then it went back to GRUB. But hey, at least I managed to do something else thanks to your help! Is this progress? Might there actually be light at the end of the tunnel?

I only ran [COLOR=#000000]sudo e2fsck -f -y -v /dev/sda1[/COLOR] on one partition (sda1), though. Do I need to apply it to every ext4 partition before Ubuntu can finally boot up again? Also, even if I did, would the faulty NTFS partition prevent Linux from working, though?

I know I ask a lot of questions, sorry for that, haha. But hey, you're helping me out a lot; I really appreciate it. :)

---

### Post by oldfred on 2015-01-07
A bad NTFS partition should not prevent booting. If in fstab to be mounted it may try to mount and have to time out so it can make for a longer boot time.

Hold shift key from BIOS and you will get grub menu, before starting. Can you then use second entry, which may be in the sub-menu. The recovery mode gives you command line, and several options to load drivers and make repairs from inside your system which can be easier than using live installer.

---

### Post by Ubultron on 2015-01-07
I'm gonna sound like an idiot, but I don't think I understood, hehe...

Also, I tried running e2fsck today on my other partition (sda3, which is only for storing data, and is also ext4), but it gave an error. It says:

[FONT=lucida console]"[COLOR=#000000]Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3[/COLOR]
[COLOR=#000000]Could this be a zero-length partition?"[/COLOR][/FONT]

[COLOR=#000000]What does that mean? Should I be worried? All of my data is in there...
[/COLOR]

---

### Post by oldfred on 2015-01-08
From your original summary report, I do not see a sda4, so yes it would give an error.
```

/dev/sda1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sda3          39,065,598 1,465,147,391 1,426,081,794   f W95 Extended (LBA)
/dev/sda5         693,469,184 1,465,147,391   771,678,208   7 NTFS / exFAT / HPFS
/dev/sda6          39,065,600   693,469,183   654,403,584  83 Linux

```

---

### Post by Ubultron on 2015-01-08
Yeah, that's what I typed down: sda3. And it says something about a zero-length partition, so I can't run fsck on it. Is there a way to go around that error? Is that a severe error? I'm beginning to freak out.

---

### Post by oldfred on 2015-01-08
You can only fsck on Linux partitions formatted with the ext family of formats. 
Your ext3 is not an ext format, it is an extended partition which is really just a container for all the logical partitions. It has no real format of its own.

So sda1 & sda6 are the only ext formatted partitions.

---


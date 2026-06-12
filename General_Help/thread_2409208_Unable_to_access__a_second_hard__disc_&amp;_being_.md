---
title: "Unable to access  a second hard  disc &amp; being locked out of it"
date: 2018-12-29
forum: General Help
---

### Post by raul-mccai on 2018-12-29
Unable to mount a Hard Disk with a ver. 16 Ubuntu OS on it. I believe it is due to a prior mount  and no dismount before powering down.  
 
 
 This is what I did:
 I have front bays on my PC for the purpose of swapping discs with different OS ( or data) on them. I have two hard discs (1 & 2) both running  Ver 16 and both with the same passphrase.  
 -  
 1) I was running a Ver 16 OS and had Disc 1 in the computer.
 2) I put Disc 2 into one of my front bays.   The goal was to access the data on disc 2 but not  to run the OS on disc 2.
 3) The newly inserted disc 2 was recognized by the running OS.
 4)  I was prompted for the passphrase when I sought to access disc 2.
 5) I entered the passphrase.
 6) Disc 2  spun up I heard it engage  and access something.
 7) the icon for disc 2 disappeared  and there was no access to  disc 2  available and that disc was still spinning when I removed it.
 8) I could unplug it and re-insert it and the whole process started all over again.
 -
 9) When I sought to reboot the whole computer with Disc 2 as the only disc in the computer  (to run the OS on disc 2) instead of the usual boot process;  I got as far as the Ubuntu countdown and then the splash screen disappeared and was replaces  by  a Black screen with white text and an error message &#8220;initramfs&#8221;
 11) there is a message that I can input &#8220;help&#8221;  in the command line and get a list of commands available

 12) that command list will appear but there are no punctuation to indicate where one begins and another ends so I can&#8217;t tell if they are one or two word commands and  I have no idea what any of them do or how to assemble them in a command line.
 13) SUDO is unavailable.  If I try to use SUDO  the error that returns is  no such command.
 -
 I believe that my OS  on disc 1 mounted disc 2 .  And that mount was never reversed.  So the disc 2 remains mounted and by disc 1. And that&#8217;s the source of my problem.
 
 
 Interestingly I have tried to access Disc 2 from a later version of Ubuntu (Ver. 18.04).  The same events as described ( supra)  occur.  I am prompted for the passphrase and then the disc disappears from sight no access granted. 

 I have not tried to access it from a Windows  OS ( simply because I don&#8217;t believe it is possible), but I do have Win 7 on another disc.  
 
 
 Any help would be much appreciated.

---

### Post by CatKiller on 2018-12-29
The issue isn't that you mounted it, it's that you yanked it out while it was still spinning.

Boot from the other drive and run fsck on the partitions of the broken one, and there's a chance it can fix it.

---

### Post by raul-mccai on 2018-12-29
> **CatKiller said:**
> The issue isn't that you mounted it, it's that you yanked it out while it was still spinning.

Boot from the other drive and run fsck on the partitions of the broken one, and there's a chance it can fix it.

Thanks for the reply:
Indeed I yanked the drive.  But  in fairness to that action;  the thing just disappeared after entering the passphrase.
Am I looking in the wrong place for it? the icon identifying  just goes away.


  I am unsure how to accomplish this since  The moment I enter the passphrase to access that second drive it just disappears
Initally the OS recognizes it as a 3.0 TB encrypted drive
Then I'm asked for the passphrase when I seek to access it
Then  when I enter the passphrase; it disappears.
How do I apply fsck to a volume that  I can't access without it disappearing. 

I have the drive installed now  and my OS can recognize it.

---

### Post by raul-mccai on 2018-12-29
when I open a terminal  I enter  fsck and I get a warning that I will damage my filesystem.  I don't know how to direct it to address the 3.0 tb encrypted second drive.
I can enter 
fsck [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sda2 
thinking  that the "2" will direct it to that other drive and I still get the  same warning and no assurance that the "2" is in fact directing it to focus on the other drive.

Maybe from a terminal   I enter
fsck -M [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sdc2
To exclude any mounted volumes?
EDIT
I just tried the above and got this

fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: No such file or directory while trying to open /dev/sdc2
Possibly non-existent device?
I can  try a /sdc1 and see
EDIT
Nope same error message
I think I can't until I access the drive so I'll try it after entering the passphrase
No Joy
I entered the passphrase on the 3.0 TB encrypted drive and  it disappeared and I tried to fsck on it from a terminal and got the same error messages.

I'd like to find a book on Ubuntu/linux  that is as well written as were the Waite Group books  on DOS  from the 1970s. Those books taught me to do handle almost anything in DOS

---

### Post by CatKiller on 2018-12-29
> **raul-mccai said:**
> I can enter 
fsck [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sda2 
thinking  that the "2" will direct it to that other drive 

It won't. /dev/sda2 is the second partition of the first drive. That's unlikely to be the one you want except by enormous coincidence.

I'd imagine that you'll need to decrypt the drive before fsck will work. That might not be possible if you've broken the filesystem, but I don't have any experience of encrypted filesystems.

```
sudo parted -l
``` should show you the partition layout, though, so you can point your commands at the right partitions.

---


---
title: "Vista 64-Bit internal, Ubuntu 7.10 external....no go!"
date: 2007-11-12
forum: General Help
---

### Post by Mattaus on 2007-11-12
OK, 

I've looked around (admitedly not very hard but there are so many threads on here its nuts!) to try and find a solution but no luck thus far (Vista in my opinion is a different kettle of fish to XP)...however I did see one thread that has got me worried about the whole ext3 thing.

First up, im a newb. Im very inexperienced with linux in general, so please don't crucify me for what may seem like glaringly obvious mistakes :S

Here's my deal. I have a Vista 64-bit home premium machine. I have 3 internal HDD's purely for Vista and its variosu games/applications/music etc etc. I also have a  western digital 320 external mybook HDD. On this external USB2.0 drive, after ALOT of mucking around,  I have Ubuntu 7.10. I managed to get it booting to the ubuntu drive here at work, and even tested it by taking the external drive to a different machine and booting off it. It worked fine both times, both machines were XP.

I took the drive home and what you know, it wont work. Been the newbie that I am I cant really make out what is going on, and seen as I cannot do a print screen I've typed out below what I get when I try to boot ubuntu on the machine with vista installed....
--------------------------------------------------------------------------------------------------------------------------------
fsck 1.40.2 (12-Jul-2007)
/dev/sdd5: clean, 101630/38567936 files, 1736789/77118016 blocks
                                                                                                                             [ OK ]
* Checking file systems....
fsck 1.40.2 (12-Jul-2007)
open UUID=0861-2704:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
fsck.ext3: Unable to resolve 'UUID=4342f2cb-924f-4057-94a3-837296c727a6'
fsck.ext3: Unable to resolve 'UUID=85565b8b-2663-44de-ab4c-1f3e5de565f6'
fsck died with exit status 9
                                                                                                                             [ fail ]
 * File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
 * A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@matts-ubuntu-PC:~# _
--------------------------------------------------------------------------------------------------------------------------------
From that point on I cant do anything. If I try to type reboot it says I can only do it as root. I try to switch to root and the password and username I set dont work. As per one of the posts I read it may be important to know that the external HDD is formatted to 4gig of swap space and 300gig of ext3 space.

Any help at even understanding what is wrong would be great. Im on my last straw as this is about to enter its 5th day of attempting to get this working the way I'd like. Im almost ready to give up and just install it on an internal drive and go for dual boot with Vista, though I couldnt even get XP to dual boot with Vista 64-bit so what hope have I of doing it with Ubuntu....god I'm a mong!

---

### Post by virtualXTC on 2008-02-02
HI,
I'm getting the same error with an internal drive with a similar setup:

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 23760 files, 3169500/3297537 clusters
open UUID=1961-1CE2:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open UUID=7DBC-F252:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open UUID=BC9B-6B99:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
fsck.ext3: Unable to resolve 'UUID=bdcf8f2a-aa40-4a44-a398-de7f800044d8'
fsck died with exit status 9

If you can get windows to boot, try running chkdisk and see if that fixes it.  (I don't have windows anymore).

---

### Post by SpiderGorilla on 2008-02-02
I'm actually running my Ubuntu on an external 250GB Western Digital IDE hard drive connected to my Vista machine using USB 2.0.

Here were the things I ran into while getting this running:

I did the install by hand on my home machine. I used the LiveCD to do the install, but I encountered an issue with the boot loader that required me to edit the boot options and remove --silent_splash (I think that was it).

When I went through the installation, I got to the point where it was asking me to finalize the options for formatting the HD. In there, I clicked "Advanced" and clicked NO BOOT LOADER. This is IMPERATIVE! If you install over your boot-loader with Vista already on your main system, there's a good chance Vista will take a nose-dive on you. I've heard you can get LILO or GRUB to install on a partition on the external HDD, but I seriously don't recommend trying it.

I got into my BIOS configuration after reboot and told it to look for the external HDD first and boot from that. Thing is, when I boot into Windows again (because I turn off my external HDD), it'll always try to boot from Windows from then-on. I have to get into my BIOS boot-menu before it loads from the Windows partition and tell it to boot from the Linux partition. The reason I don't mind this is because it's about the same as thwarting the GRUB auto-load process anyway, plus I don't reboot very often.

So, to sum up:

1) Install using the LiveCD again on the external HDD.
2) Do NOT let it install to the master boot record!
3) Catch your system at start-up and redirect it to your external HDD.

This, of course, assumes you've got a system that can boot from a USB 2.0 device. The odds that you have a 64-bit Vista system that can't do that is pretty low, but you might wanna check that first.

That's my 2 cents. Since I'm not a pro, I can't say my experience will be reproduceable, but I did this installation 3 times (once for the initial, once when I tried to get the 32-bit version running which went VERY badly and once again when I decided to go back to the 64-bit version and just power through). Again, take my advice on your own head. If you mess up, I hope you've got the Vista reinstall CD. Or that you have a rescue partition.

---


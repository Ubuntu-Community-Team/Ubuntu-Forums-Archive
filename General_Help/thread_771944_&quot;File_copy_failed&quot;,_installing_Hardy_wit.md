---
title: "&quot;File copy failed&quot;, installing Hardy with Wubi on WinXP"
date: 2008-04-28
forum: General Help
---

### Post by bulldozer on 2008-04-28
Hi

(Sorry if this is a duplicate post, but I could not at least find this from this or any other forum. And believe me, I did try searching :)

Prologue:
------------
Spent the weekend trying to get a quick install of Ubuntu working on my desktop Windows box, with very limited success :/

Started by downloading the i386-desktop.iso, burnt it on a CDR, and it worked like a charm. But did not actually fulfill my needs (I intend to test some DVB cards and VDR etc., but that will be another issue. Those cards are not even yet inside the PC)

So, I need to make a "real" install, but don't have a suitable extra partition, or really a wish to make one. So let's try Wubi instead.

Chapter I - BusyBox
---------------------------
As instructed, I copied the wubi.exe from the CD to the same directory in my HD that had the .iso, and run wubi. Windows part of the installer worked fine, but after booting to Ubuntu, it got this BusyBox / initramfs thing.

Okay, for that I found the fix (add "irqpoll" in the boot command line), and a bit later also the solution (get newer wubi from [http://www.]("http://www.wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev501.exe"). But this was not yet all...

Chapter II - Formatting swap
-------------------------------------
After getting past the BusyBox thingy, the installer categorically hung on "formatting swap". But as before, the forum was of great help, and suggested excess fragmentation to be the cause. Indeed this was the case, swap.dsk was around 2000 fragments while root.dsk almost 8000. Not good, so I run the jkdefrag (and did some other cleanup on the HD as well), and it did help, so the install proceeded further. But wait, this can not be the end, right? No...

Chapter III - File copy failed
------------------------------------
So now the installer got much further, and was happily copying files, until it hit some sort of error ("destination file does not match the source", or something similar, I do not have the logs with me, as I'm typing this from the office), and a question if I wish to Skip, Retry or Abort. (It also suggested that this might be caused by a bad CD media, but as the install was running from the ISO from HD (with md5 checked ok), I suspected that this could not be the case.)

I chose Retry, thinking that maybe this was some random error, and indeed the installation seemed to continue for few seconds, until another prompt pop up, saying "Installation failed. The system will now reboot."

After reboot, if trying to boot into Ubuntu, it found the half-way installation and refused to continue, but proposed an uninstall and a clean install. Tried that as well (couple of times), with no success. The file that caused the error seemed to vary, perhaps randomly or perhaps based on the size of the installation chosen in Wubi initial screen, I'm not exactly sure. But it was definitely not always the same file. (And i could not find that particular piece of information from any logs either.)

I doubt that this could be a hard drive problem, as I have not had any other problems with that (from Windows), and also windows checkdsk reports no errors.

So, any suggestions? I am committed to get this thing installed (with Wubi, prefereably), no matter what it takes :)

The system setup:
- Intel D845PESV board (I think, some of those anyhow)
- Intel Celeron 2 GHz processor
- 1 GB main memory
- 80 GB IDE Hard disk (Samsung SpinPoint series, I think)
- nVidia GeForce4 Ti 4800 graphics card
- SoundBlaster Audigy2 sound card
- Some LG IDE DVD-RW drive 
- Windows XP Professional SP2
- One thing, perhaps worth mentioning, the system in installed on D: -partition (which is the only partition on that HD), there is no C: -drive on the system at all)

Any help is more than welcome :)

Best regards,

  -kari

---

### Post by ago on 2008-04-28
It looks like your filesystem could do with some love. Uninstall Wubi, run chkdsk /r, then defragment all the disk. Then install Wubi again. 

If the installation stops, press ctrl+alt+f2 and run the following command

sudo sh /custom-installation/hooks/failure-command.sh

That will produce some logs in C:\ubuntu\installation-logs.zip under windows. Post them here.

---

### Post by bulldozer on 2008-04-28
> **ago said:**
> It looks like your filesystem could do with some love. Uninstall Wubi, run chkdsk /r, then defragment all the disk. Then install Wubi again. 

Have done this. Defragmentation did help to get past the second issue ("formatting swap"). Checkdisk (I run it from Windows Disk tools -> Error checking, but it should be the same, I think) did not produce any errors.

> **ago said:**
> If the installation stops, press ctrl+alt+f2 and run the following command

sudo sh /custom-installation/hooks/failure-command.sh

That will produce some logs in C:\ubuntu\installation-logs.zip under windows. Post them here.

I will try once more later today, and post the logs. Btw, they were produced also earlier without having to pack those manually. I did not find anything suspicious, but I trust you can do better there :)

---

### Post by ago on 2008-04-28
If you already have the logs post them! They are even more useful if you boot in verbose mode. Relevant items will be under /var/log/syslog and /var/log/installer.

---

### Post by bulldozer on 2008-04-28
Thank you for spending time and effort into this. 

I will post those, as soon as I get to them (they are at home, I'm at work, and the PC in question is not running).

---

### Post by bulldozer on 2008-04-28
Here is the installation_logs.zip. In file "errmsg.log" is (roughly, from my poor memory) the dialog box error messages that popped up during the install, if they are of any help.

The logs are from todays attempt, which was preceded by chkdsk /r (no errors) and JKDefrag (almost unfragmented, as that was handled already during the weekend :)

Again, any help or suggestions would be highly appreciated.

---

### Post by ago on 2008-04-28
Please file a bug in [https://bugs.launchpad.net/wubi/+bugs](https://bugs.launchpad.net/wubi/+bugs) mentioning "Squashfs errors during file copy" under Wubi and Ubuntu+Ubiquity

And attach your log there

---

### Post by bulldozer on 2008-04-29
Ok, done that. Thanks for the pointer, as being a bit new(ish) into this I did not know how should i proceed with the matter.

---

### Post by ago on 2008-04-29
Got that, thanks, will now check with other devs

---

### Post by bulldozer on 2008-05-05
Thought that it might appropriate to report this here also... This was NOT a bug in wubi/ubuntu, but an error in my hardware after all. One memory module was bad (showed errors in the ubuntu livecd memory test), and after removing that, everything worked like a charm.

So, this issue is, at least for me, more or less "solved".

---


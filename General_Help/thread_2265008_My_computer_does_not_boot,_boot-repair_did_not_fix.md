---
title: "My computer does not boot, boot-repair did not fix it"
date: 2015-02-11
forum: General Help
---

### Post by mistermagio on 2015-02-11
Hi everyone, 

I find myself in dire need of your help. My laptop boots into Grub fine, but then it gets stuck on the spash screen. The splash screen does keep going, but I left it for more than 30 minutes without touching it at once to no avail before giving up and force shutdown.

I have then proceeded to boot into my Utopic liveusb, install and run boot-repair, which didn't solve the problem but it did give me a notice that there was an error in the procedure. However I don't have the knowledge necessary to make sense of the log it gave me: [URL="http://paste.ubuntu.com/10179211/"]http://paste.ubuntu.com/10179211/
[/URL]
I really one of you will understand something there and know how to fix it... Anyway, a bit more context:

My laptop is an Asus UX301, it has been running Ubuntu (13.10, then 14.04 and now 14.10) more than fine for about a year now, I hadn't had any issue (not even slight ones) for months until now, what led to the state it is now seems to have happened after I closed the lid to suspend the computer, only to find it heated up a few hours later and unresponsive, forcing me to force shutdown and to find it not booting up after letting it cool for a few minutes.

The laptop is running two 256 gigs Sandisk SSDs in Raid0, which has me scared that one of them has had a failure and killed the array. However, I'm no expert (not at all), but when I booted up the LiveUSB and got into gparted, it did recognize the Raid array and its filesystems and both drives individually, as well as what seems like the right proportion of used/unused space on the array, which makes me hopeful that the drives are both fine-ish at least. I may be completely delusional, not knowledgeable enough to make such assumptions...

So yeah, here's to hoping one of you has the answer to my issue. If you think the drives are OK, but the system is lost, I would appreciate it if you let me know of a way to access the array and salvage what unbacked-up data I had lying around before reinstalling.

Thanks in advance for your answers !

PS: If you need any further information to help, I'll try and provide it as fast as possible.

---

### Post by mistermagio on 2015-02-12
Little update, I have managed to access my root partition from the LiveUSB (it was sitting in Nautilus and I just didn't notice it before) and all the data on it, so backing up the files I need from the home partition will be no problem if it is needed. Also mostly confirms that the array isn't corrupted, which means no drive has failed. 

It's just a question of whether or not the system per se is fixable or if reinstalling is my only option.

---

### Post by oldfred on 2015-02-12
If not backed up, do that. 

But issue seems like a video issue, but could be other boot parameters needed for unique hardware.

What brand/model computer? And what video card/chip?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---


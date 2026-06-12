---
title: "Swap space with Vista and Wubi 7.10"
date: 2007-11-28
forum: General Help
---

### Post by supersound on 2007-11-28
Hi Ago

Wubi 7.10 (rev 386) seems to work ok with me until I get to boot into Ubuntu for the first time for install- I then get an error 'Failed to create swap space' (because of NTFS?). If I ignore this and carry on the 'Next' button in the install dialog is unavailable. I'm using Vista home basic.

Thanks for your hard work on 7.10.... any help appreciated. Sorry if this has been answered before.

---

### Post by ago on 2007-11-28
might be that the swap file (/ubuntu/disks/swap.disk) is fragmented, you can recreate with any other tool, provided it is contiguous

---

### Post by supersound on 2007-11-28
By defragmenting in windows?

---

### Post by ago on 2007-11-28
As well or by creating a new empty file of the desired file

---

### Post by supersound on 2007-12-07
Forgot to post to say that this worked- was too busy enjoying Gutsy :)
I now have dual boot Vista Home and Gutsy on a Dell 1501, using Wubi alpha. Nice work Ago...

By the way, I could only run Wubi from root of C: in Vista, even as administrator- thought this might be of help to other noobs.

---

### Post by Mander on 2008-03-30
Sorry to revive an old thread, but I'm not sure I understand the fix here.

I'm getting the same message, but I don't really know how to create "a new empty file of the desired file".

I have a new laptop with Vista home premium and an AMD Athlon 64x2 processor (if that matters).  I created a new partition using the windows tools, called it U: (for Ubuntu) and ran the Wubi installer.

The first time I did this I let it run overnight so that it could download all the appropriate stuff.  Ubuntu then appears in the menu when I reboot, but it went through the "checking the installation" process then gave me the message about the swap file and shut down.  

I then tried the instructions here 

[http://ubuntuforums.org/showthread.php?t=438858](http://ubuntuforums.org/showthread.php?t=438858)

and now have two "Ubuntu" entries in the menu.  If I select the first one, I get a message "missing MBR-helper" and I have to reboot (ctrl+alt+del works here).  The second one takes me through the same process mentioned above.

So, I then uninstalled Wubi (leaving the iso file in the directory, because I figured there was no point in downloading it again) and then tried re-installing, explicitly as an administrator.  This time it gave me several screens worth of error messages, finally getting stuck on 

mktemp: cannot create temp file /tmp/tmp.L1XdKK5843:  Read-only file system

After which I had to hard reboot.  I then went through the bcdedit instructions again and this time it got stuck on "Starting ACPI services" and I had to hard reboot again.

Any suggestions? My computer is one of those ones with the hidden partition rather than a separate CD, and although I burned a backup copy I'd rather not test whether I can install Vista second.

---

### Post by ago on 2008-03-30
Uninstall everything (you can use easybcd to cleanup boot entries) and reinstall. No need to take manual steps.
Swap errors may happen when the swap file is fragmented

---

### Post by Mander on 2008-03-31
How does the swap file become fragmented on a brand-new, empty partition?  Or should I create another small partition for swap, like I did when dual-booting with XP and Fedora on a different computer?

I'm sure I'm missing something really obvious here...thanks for indulging me.

---

### Post by ago on 2008-03-31
> **Mander said:**
> How does the swap file become fragmented on a brand-new, empty partition?
That is a new bug. [https://bugs.launchpad.net/wubi/+bug/206113](https://bugs.launchpad.net/wubi/+bug/206113)

Fragmentation is only one hypthesis at this stage... In fact any help on that would be appreciated (I cannot reproduce that myself). If it can be pinned it down (in time), it will be fixed.

To begin with you can use chkdsk or jkdefrag to test for fragmentation of a single file.

---

### Post by ago on 2008-03-31
Simply deleting /ubuntu/disks/swap.disk might also make it work. Is there anything peculiar about your partition (is it compressed, encrypted, on raid...)?

---

### Post by Mander on 2008-03-31
Nothing unusual about it as far as I know.  I've only had it for a few days now, so there isn't much on the hard drive at all.  Following previous comments, I tried installing wubi on the standard C: partition, rather than the empty one I created for it.  No RAID, encryption, etc. unless Vista has some default setting that I haven't managed to break yet. :)

I should mention that I wasn't being quite clear on what version I was using earlier (I probably should have started a new thread...sorry).  I was trying all this with the 8.04.467 version, not the 7.10 version.

I thought that perhaps it was a problem with the beta version, so I uninstalled it and tried the older 7.04 version before I read your message.  Which has brought on a whole other raft of problems...

I'll try reinstalling the beta and see what happens.

---

### Post by jjpgn73 on 2008-05-21
My problem has been solved, but I'm  posting this in hopes that it may help someone else with the same problem.

I've been trying to install Ubuntu 8.04 into Windows vista with Wubi and I kept on receiving _[U][FONT="Courier New"]"The creation of swap space in partition #1 of /host/ubuntu/disks/swap.disk failed."[/FONT]_[/U] when it booted up for the first time after each installation. I deleted /ubuntu/disks/swap.disk like "ago" mentioned, which seemed to have gotten me farther.  I ended up also deleting /ubuntu/disks/root.disk,  which finally allowed me to completely install ubuntu within windows(after rebooting, of course).  I don't know why it worked, but it did.

---

### Post by ago on 2008-05-21
> **Mander said:**
> I was trying all this with the 8.04.467 version, not the 7.10 version.

Use the wubi version on the website (rev501)

---

### Post by ago on 2008-05-21
> **jjpgn73 said:**
> My problem has been solved, but I'm  posting this in hopes that it may help someone else with the same problem.

I've been trying to install Ubuntu 8.04 into Windows vista with Wubi and I kept on receiving _[U][FONT="Courier New"]"The creation of swap space in partition #1 of /host/ubuntu/disks/swap.disk failed."[/FONT]_[/U] when it booted up for the first time after each installation. I deleted /ubuntu/disks/swap.disk like "ago" mentioned, which seemed to have gotten me farther.  I ended up also deleting /ubuntu/disks/root.disk,  which finally allowed me to completely install ubuntu within windows(after rebooting, of course).  I don't know why it worked, but it did.

When you have a swap error that is usually due to a fragemented swap file.

Also note that if the installation fails half way through you cannot run the installer again but gave to uninstall and reinstall.

Hence the procedure is:

uninstall, install wubi, run jkdefrag on the swap file, reboot and continute the intsllation

Also note that the swapfile is generally small, and if that is fragmented it usually means that your hard disk is in bad shape. Hence you should run jkdefrag on the whole disk and then chkdsk /r (that is before running wubi).

---


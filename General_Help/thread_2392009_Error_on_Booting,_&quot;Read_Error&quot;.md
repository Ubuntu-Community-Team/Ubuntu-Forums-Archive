---
title: "Error on Booting, &quot;Read Error&quot;"
date: 2018-05-15
forum: General Help
---

### Post by magus1108 on 2018-05-15
Hello. So, first off, I am a noob at Linux and Ubuntu. I usually just use results from forums like this to solve any problems I come across, and while I found a similar thread to this from 2013, the solutions there have not helped me out. 

So, first, I am using Ubuntu 16.04, I use an Acer Aspire laptop, and I am writing this from an 16.04 Ubuntu installation USB right now.

Throughout today and yesterday, I've had several errors and problems with Ubuntu, culminating in me restarting my computer, only to get a 'Read Error' message in the upper left corner of the screen upon booting up. I seemingly cannot type anything else when I reach that black screen. I tried using the boot-repair function to fix the issue, but it has seemingly not worked for me. It did give me a pastebin link to post here, so I'll be including that link here. 

And, while it may not be an issue now, I also had a prior problem of my computer booting and rebooting itself constantly before I got that Read Error message. I wouldn't get past the logo screen before the computer shut itself off and started up again. Even when I switched to booting up the USB, it took several cycles for this to come up properly. So far that problem seems to have gone away, and now I'm just loading up to a Read Error message.

And as for the problem/issue that lead up to this, my computer was having this read-only error bug cropping up with my files through several restart cycles. I'd always get booted up to the BusyBox shell, and I'd run the 'fsck /dev/mapper/ubuntu--vg-root -y' command to try and fix it, though it still seemed to pop up again after maybe ten minutes on the new restart cycle. 

If there are any more questions I need to answer, I'd be happy to. I really just want to get my computer working again, and I have no idea how to do that right now. Any help would be deeply appreciated!

[http://paste.ubuntu.com/p/4dykD22Hpk/](http://paste.ubuntu.com/p/4dykD22Hpk/)

EDIT: I decided to try boot-repair again, and it gave me a new pastebin link. It looks different from the first one, and I'm not too sure what to make of it.

[http://paste.ubuntu.com/p/rs2FZBjYqq/](http://paste.ubuntu.com/p/rs2FZBjYqq/)

---

### Post by oldfred on 2018-05-15
You have a LVM with encryption full drive install on sdb.
The errors prevented even Boot-Repair from seeing drive. But maybe some of its fixes then the second report shows drive.

With LVM and encryption you must have very good backups as any corruption or drive error often causes data loss. The encryption is intended to prevent access and if you cannot access drive with pass phrase, then your only recourse is your good backup procedures.

I do not know LVM nor encryption. 
But if you can use Boot-Repair and manually mount the LVM and decrypt install, run Boot-Repair's fixes. It may not normally ask to decrypt drive.

       Ubuntu 16.04.3 LTS - correct fsck method for encrypted LVM? 
[https://ubuntuforums.org/showthread.php?t=2375964](https://ubuntuforums.org/showthread.php?t=2375964)

See first part for mounting:

 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---


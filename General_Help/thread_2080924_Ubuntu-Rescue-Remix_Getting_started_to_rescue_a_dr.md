---
title: "Ubuntu-Rescue-Remix: Getting started to rescue a drive"
date: 2012-11-05
forum: General Help
---

### Post by Steve00 on 2012-11-05
I am trying to rescue a Maxtor external HD, formatted for WinXP. This drive will not mount when plugged into Windows. When plugged into USB, Windows recognizes enough to load the Maxtor drivers, but the drive never appears in Windows Explorer.

I ran Ubuntu-Rescue-Remix 12.04 and before trying Gnuddrescue my first step was to determine which device was allocated to the drive. I used the steps shown at:

[http://ubuntu-rescue-remix.org/node/66](http://ubuntu-rescue-remix.org/node/66)

 I first tried 'sudo lshw -C disk -short'. The system appeared to scan and then wound up on SCSI and hung there. When I unplugged the Maxtor's USB cable, the Remix live CD responded with:

H/W Path        Device      Class       Description
===================================================
/0/100/1f.2/0   /dev/sda    disk        500GB Toshiba MK5065GS
/0/100/1f.2/1   /dev/cdrom  disk        DVD RW AD-7700S
/0/100/1f.2/1/0 /dev/cdrom  disk

There is nothing showing as a USB device.

I then tried running 'tail -f /var/log/messages', before I could plug the Maxtor back in, got the message: "tail: cannot open '/var/log/messages' for reading: No such file or directory"

I was able to get into the director /var/log/ but, not surprisingly, there is no 'messages' file.

Where do I go from here? I hope to rescue this drive and write its image to a second USB drive.

Thanks.

---

### Post by Steve00 on 2012-11-05
Further reading of ddrescue's info pages indicates that "if the damaged drive is not listed in /dev then you cannot rescue it [with] ddrescue."

Based on this and what I show in my first post I gather I'm out of luck unless I tear the Maxtor apart and pull the drive out.

Is this a correct assumption or are there other options?

---


---
title: "GRUB help - remove an old HDD and install a new one in its place"
date: 2014-07-28
forum: General Help
---

### Post by chamira on 2014-07-28
My motherboard only has 4 SATA ports and I need to remove and dead HDD install a new one in its place and format it.

The problem is when I simply unplug the old HDD and plug the new one in, I get a error on boot: "No such device: ......" and the grub rescue prompt.

What is the easiest way to remove the old device form Grub so I can use that SATA port for a new HDD?

I have run update-grub, but that did not help.

---

### Post by slooksterpsv on 2014-07-28
You'll need to boot from a Live DVD or USB and reinstall grub on the drive you want to handle OS boot operations. What OSes do you have installed? Do you have EFI or use EFI (Windows 8, Windows 7, Ubuntu, etc.)?

---

### Post by chamira on 2014-07-28
Hello,

Sorry for not making things clear.

GRUB is on the drive I want. If I disconnect the new HDD that is on the dead HDDs SATA port I can boot without any issues.

The dead HDD had an older version of Ubuntu.

I need to replace it with a new drive and get that drive formatted but I can't plug that new HDD - I get that Grub error.

---

### Post by yancek on 2014-07-28
> GRUB is on the drive I want. If I disconnect the new HDD that is on the dead HDDs SATA port I can boot without any issues.

Is that without the old drive attached or with it?  If your operating system and Grub are on a different drive and the bad drive is just a data partition, I would expect a message indicating the partition is not ready, or something similar.  Which Ubuntu are you using (14.04)?

You might go to the site below and download and run the bootinfoscript which should be helpful in resolving the problem as it provides a lot of information on boot files/partitions.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by oldfred on 2014-07-28
Grub does do a search for UUID after the set root command. Adding or changing drives may change set root drive order so boot drive is not hd2, but search by UUID should overide an incorrect set root.
But perhaps since drive is not formatted grub is not correctly scanning drive.
Is old/new drive port a lower number port on mother board that boot drive.

You should be able to manually boot from a rescue prompt. 
       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

I skipped a port on my mother board and when I plug in a flash drive it is sde, but when I reboot it is sdb. And in grub the boot drive in BIOS is always hd0, so if grub is on same drive as Ubuntu you should still use hd0. But if another drive it can get confusing as order may change. I have sdc as boot drive and in grub it is hd0, but drive is sdc normally but if flash drive is plugged in it becomes sdd. Whew, I am not sure I understand and sometimes just keep trying different numbers.

      
 ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

OR and change hd0,5 and sda5 to your drive & partition and if not seen as sda, it may be hd0,5 but not sda:
      
 set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

### Post by chamira on 2014-07-28
Thank you very much for all your help.

**yancek** - I am sorry my information was not accurate or complete. In my previous post (now edited) I said "The dead HDD was a data drive I used to back-up my documents." This was wrong -  it was an older version of Ubuntu on there. So obviously it was recorded in the Grub file as a bootable OS.

The latest OS (14.04) and grub were both one separate drive. The problem was with removing the other HDD with an older OS, and connecting new unformatted HDD in to the same SATA port - this threw Grub off completely.

I managed to get things working:
[LIST]
[*][*]I downloaded the Boot Repair image and, disconnected the new HDD and ran the basic repair option.
[*]This fixed the problem, I guess Grub did not find another OS on that port and cleared it.
[*]I then shut down, connected the new HDD and booted OK, then formatted &etc.
[/LIST]

**oldfred** your post helped me to figure out my issue, and of course learn, which seems to never end with Ubuntu!

---

### Post by oldfred on 2014-07-28
Glad you got it working. ;)

One thing I do not like about Boot-Repair's autofix is that with multiple drives it will install one grub to every MBR. Often with multiple drives you may want a different boot loader in each MBR. And you can do that with Boot-Repair but only in advanced options.

---

### Post by chamira on 2014-07-28
> **oldfred said:**
> Glad you got it working. ;)

One thing I do not like about Boot-Repair's autofix is that with multiple drives it will install one grub to every MBR. Often with multiple drives you may want a different boot loader in each MBR. And you can do that with Boot-Repair but only in advanced options.

Yes, it does seem like a 'magic' button and a bit disconcerting for a non-expert because I don't know what is being done. 

But it does look like the default settings in 'Advanced' are the things being performed via the autofix. So, tweaking the autofix slightly should avoid grub being installed everywhere, as you say.

---


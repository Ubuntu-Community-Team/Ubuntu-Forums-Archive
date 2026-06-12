---
title: "Grub2 Loading on Wake from Sleep"
date: 2014-07-28
forum: General Help
---

### Post by Yan_Birch on 2014-07-28
Hi everybody!

I've recently installed Ubuntu 14.04 alongside Windows 7 on my laptop and I've just noticed a slight annoyance, not a dealbreaker, but I'm curious as to whether anyone else has experienced this and/or come up with a fix.

The problem in question concerns behaviour when the laptop wakes from sleep. I close the lid as I would normally to send the laptop to sleep with no problems. However, on waking I am greeted with the Grub2 menu and I am able to boot into either Ubuntu or Windows at my leisure which as far as I am aware, I shouldn't be able to do!

As I said, it's not massive, but sometimes it can be annoying having to select either Windows or Ubuntu each time to get to the login screen when I send the laptop to sleep as opposed to being greeted with it automatically.

Thanks in advance!

---

### Post by oldfred on 2014-07-28
I still have 12.04 on my laptop and have no issues.

But that seems more like you are shutting down and it is not shutting down correctly?
As grub 2 has a flag and if not shutdown correctly will always present grub menu and have no timeout so you can boot in recovery mode if needed. And if able to boot without issues it is not a major issue.

Not sure how to check on sleep, or shutdown settings. 
Startup log files are in /var/log/dmesg and there are many log files in /var/log which I have not reviewed.
You should have log file viewer or just use your favorite text file editor to look at files.

---

### Post by Yan_Birch on 2014-07-28
I've managed to determine that this problem is specific to closing the lid. Initiating sleep (or hibernate, I tried to replicate the problem with both) through any other method does not result in this problem.

Like I said it's not a major problem, but I'm one of these people who would like to figure why these things happen. Not sure if this helps in anyway but I'll try and have a look at the log-files next time I'm booted in Ubuntu.

It could even be a problem with the laptop itself in how it initiates sleep when prompted by a lid close, but I have no way of confirming that unfortunately.

---

### Post by oldfred on 2014-07-28
This user with an Acer Aspire had a shutdown problem that was related to USB ports.

[http://ubuntuforums.org/showthread.php?t=2236676](http://ubuntuforums.org/showthread.php?t=2236676)

---

### Post by Yan_Birch on 2014-07-29
I'm not really having problems with shutdown per se. I've done some more digging and it would appear that my laptop (a Sony Vaio VPCEH, about 4 years old now) enters hibernation on closing the lid rather than sleep. I've managed to replicate the scenario by manually entering hibernation.

I've managed to fix the problem when it occurs in Ubuntu. If I suspend/hibernate while in Ubuntu then turn the laptop back on I am booted straight back into Ubuntu with no sign of GRUB. So as it stands, this problem now only occurs when I'm booted in Windows 7 and I enter hibernation. This leads me to think that it may be the way GRUB chainloads the Windows bootloader, but I have no idea where to begin with a fix there.

I should also note that if I hibernate in Windows, turn the laptop back on and boot into Ubuntu instead, Ubuntu recognises my Windows partition as being in a hibernation state. Not sure if that is useful, but I thought it was interesting nonetheless.

---

### Post by oldfred on 2014-07-29
Then it should be a setting in BIOS on which mode system goes into when lid is closed. 
But some defaults and designs that assume only Windows do not then work as well dual booting.

---

### Post by Yan_Birch on 2014-07-29
This is a good point. I think I'll have to have a rummage through my BIOS settings to see if I can identify a culprit. Thank you!

---


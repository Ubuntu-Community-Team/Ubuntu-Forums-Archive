---
title: "Update with something about secure boot rendered my computer unusable"
date: 2016-07-15
forum: General Help
---

### Post by giga+bytes on 2016-07-15
Hello Ubuntu community! I just joined specifically to get help since nothing I've found has worked.

My household has been solely Windows users, until we decided a couple months ago to start adjusting to Ubuntu to get away from Windows. I bought a Lenovo laptop, immediately replaced the hdd with a new ssd (Samsung 850 EVO), and installed Ubuntu 14.04 LTS by usb flash drive. Even after reading many guides and threads about the process of installing and setting up Ubuntu, right from the start things didn't follow anything I knew of; we even had to switch to another server to get missing files (or something like that). So far we've honestly been rather disappointed with Ubuntu, as updates keep complaining about missing signatures, the system often locks up with green lines across the screen, and a few times it even restarted on its own for no apparent reason. We've never had anywhere near such problems with any of our Windows computers.

Anyways, we've been chugging along hoping updates will fix some of the issues, and as threads regarding security say to, we always check for and install all updates at every boot. Last night one of the family did this, and a popup about secure boot appeared, saying something about disabling it because of third drivers (everyone was tired and getting ready to pack it in for the night, so no-one was thinking clearly and we forgot to take pictures or write it down). The only choices it gave were help, forward or disable, they took a look at help, then asked me to check into what this was all about. From what I could see it looked better to leave secure boot enabled, so they selected forward, which seemed to be fine for the updates installed and it asked to restart the system like usual. But it didn't boot like normal, it had a new login screen, and the usual login information didn't work. I don't remember what all we tried, following various similar situations from "ask ubuntu", but we were brought to a black screen with the basic Ubuntu information at the top and the username with a blinking cursor, presumably a full-screen terminal. The last thing we tried, which I think was to repair or install the AMD fglrx driver, rebooted the system to a completely black screen that no longer shows anything being typed. We gave up for the night, manually shut it down, and haven't started it since. What happened to this computer?

Honestly, if we can simply save what we don't have backed up (one game savefile, and the google favourites/bookmarks), we would prefer to just do a fresh install with step-by-step help from experts, in the hope of whatever errors we must have from the first install being eliminated, thereby providing a more stable and reliable system. If not, we'll see how much trouble diagnosing and fixing everything is.

---

### Post by carl4926 on 2016-07-15
You can boot the install media and access your files
Is it possibly a Hybrid graphics machine? That sounds like it may be the issue? Personally I avoid them.
And on my machines, I disable secure boot, especially since I don't ever keep Windows

---

### Post by giga+bytes on 2016-07-16
Right, I remember reading something about that. I'll try it the next opportunity I get.

It isn't a hybrid graphics machine, here's the specs: Lenovo G50 Notebook (80E301Y6US); 15.6" HD screen, AMD A8-6410 with integrated AMD Radeon R5 graphics, 4GB RAM, 1TB HDD, Win10. I looked in the bios for the option to disable secure boot before installing Ubuntu, but almost everything's locked so there was nothing I could do, not even check or change the speed of the new RAM sticks (the cpu is supposed to really benefit from 1866 RAM, so I installed a pair, but I have no idea if it's set to that speed or not).

---

### Post by oldfred on 2016-07-16
Your UEFI Secure boot may just be called "Windows" and "other". The clue is in fine print somewhere it may say if installing Windows 7 you must use "other". Windows 7 does not support UEFI Secure Boot.

If you left Secure boot on, then you must have installed in UEFI Secure boot mode. That should work, but I also turn off secure boot for now. In future we may need it.

Do not know about AMD graphics and that may be part of your issue.
       16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  
      
 AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075)

Lots of info on UEFI installs in link in my signature.

---

### Post by giga+bytes on 2016-07-16
Thanks oldfred! To point out, I removed the hdd it came with (that had Win10 OEM on it), without starting the computer to begin installing the OS, and put a fresh ssd to install Ubuntu on. I'll check into that "windows" and "other" to see if I can find it. Also, I'm using 14.04 LTS until the AMD driver issues with 16.04 are sorted out.

---

### Post by giga+bytes on 2016-07-16
Okay, to update: trying Ubuntu on the usb drive without installing worked, so I got all the data off the computer. Then I went to the BIOS and found secure boot, which I had somehow missed originally. It was enabled, so I disabled it. Then the computer started up like normal! However we're still leery that there's errors lingering somewhere, and are concerned that having installed Ubuntu with secure boot enabled may be why we've been experiencing the lockups and restarts. This thread's topic has been solved, so I'll ask my new questions in a new thread.

---


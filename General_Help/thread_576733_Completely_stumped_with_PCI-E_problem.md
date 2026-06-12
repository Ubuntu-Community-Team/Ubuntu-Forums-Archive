---
title: "Completely stumped with PCI-E problem"
date: 2007-10-15
forum: General Help
---

### Post by Imsati on 2007-10-15
A few weeks ago, I obtained a new MoBo (ECS 945GZT-M) and Ubuntu stopped working. Upon trying to reinstall it, the X-server wouldn't start from the Live CD. The only thing different from my old board was the PCI-E slot. My old board was x16 and this one is at x4. Well, I experimented with some other MoBo's (both with full x16 speeds) and the Live CD booted right up. On a whim, I tried the ECS board again and the Live CD worked. Unfortunately in the process, I fried my spare HDD :mad: I decided to keep the ECS since I really didn't need all the features the other boards offered, and since Ubuntu was now apparently working, it would be fine.   ...

Fast forward to this morning. My new HDD arrived and I installed it right away and booted up the 7.04 i386 Live CD. It loaded up find and installed to the HDD perfectly. Zero issues whatsoever. Upon completion, I rebooted and loaded up Ubuntu. It would load normally until the very end, at which point the status bar would freeze for about 20 seconds and then move to a terminal-like display with the following:

*Mounting local filesystems
*Activating Swapfile swap
*Configuring network interfaces
*Loadind ACPI modules
*Starting ACPI services
*Starting system log daemon
*Doing Wacom setup
*Starting kernel log
*Starting system message bus dbus
*Starting hardware abstraction layer hald

After the last line, the system would hang for 2-3 minutes, then more code would pop up too fast to copy. After, the background to the Splash screen appears, but it's about 20 seconds before the Login appears.

After I'm logged in, the system itself is incredibly slow. I'm not able to enable the Nvidia driver, the system does not detect any updates, and when I use Terminal or Update Manager, it tells me that the repositories don't exist. Synaptic shows nothing detected as upgrades either. Loading up Feisty 64-bit, it also installs perfectly (although at a lower resolution) but once everything is loaded and restarted, the same as the i386--no upgrades, Nvidia, etc.

I went into BIOS and looked at the PCI Settings. My options are to either use on-board VGA adapter (which works perfectly, actually, but why have a video card if you can't use it?), PCI x16(which does not run at x16), or PCI x4.

I'm completely stumped now. I still have the other MoBo's ready to be shipped out. As I mentioned above, I'd prefer to keep the ECS, but will use the Abit IL9 Pro (which has a PCI-E running at full x16 speed) if necessary. Is this as simple as a PCI-E slot running at x4 speed or something else? The video card is an e-GeForce 7100 GS and worked perfectly with my previous Abit IP-95 Board, and currently works perfectly with XP.

Any and all suggestions would be great! Thanks so much!

--Jay

---

### Post by Imsati on 2007-10-15
Well, I just downloaded the latest rc of 7.10 and still the same thing. One thing I did notice though is that during the install, a message popped up that said something about not being able to apply security repositories and to add them manually. I didn't think anything of it, but when I tried to use Firefox to post up the problem from Ubuntu, I couldn't get to any websites. A 'sudo apt-get update' command yielded this result:

jason@JasonU:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
  Could not resolve 'archive.canonical.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages

And much much more lines similar to the above. Terminal/Synaptic/Updater were not able to identify any updates on 7.04 either. Could it be something other than just a PCI-E slot? Maybe my chipset is not supported perhaps? Still very confused!

---

### Post by Imsati on 2007-10-16
This is the error that I get when trying to enable the Nvidia restricted Driver, thus leading me to believe it's a ethernet connection problem.:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-14.8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-14.8_i386.deb) 
  Could not resolve 'archive.ubuntu.com'

---

### Post by Imsati on 2007-10-16
Well, I'm going to go ahead and post this Thread over in Absolute Beginner Talk (since that's what I feel like this problem) or Multimedia and Video in a bit to see if anyone has any input.

---


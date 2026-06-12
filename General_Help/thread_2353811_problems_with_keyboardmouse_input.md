---
title: "problems with keyboard/mouse input"
date: 2017-02-25
forum: General Help
---

### Post by inkameep on 2017-02-25
I've just installed Ubuntu 12.04.5 (dual boot with Windows 7). Quite often when I click on a button or enter some text, the display does not refresh itself until I move the cursor. I have to move the cursor around like a paintbrush to repaint the screen. This problem started happening during the install, when I was making selections to configure the system. There are some peculiarities in "Keyboard Layout." Under the Language tab, there is a duplicate entry for "English (Canada)", of which the second one is selected. None of the entries can be deleted. Another peculiarity is that under the "System" tab, my display language is "English (Canada)" while the system display language is blank. "English (US)" appears after "Input source." Is that how it's supposed to be?

How do I fix the keyboard and language configuration? Is that likely to fix the problem with the display not refreshing?

---

### Post by Bucky Ball on 2017-02-25
Just a suggestion. If you have only just installed, have you tried a newer release? 12.04 LTS is supported until the middle of this year at which point you'll need to upgrade the OS to a newer release, probably 16.04 LTS. Why not install that to start with and save yourself some time. That is supported until 2021. ;)

As for the display not refreshing, could you please give details of your machine specs, please. RAM and graphics card, make and model, etc. You may need to install a driver for GPU.

---

### Post by inkameep on 2017-02-25
I tried installing 16.04 LTS but the installation failed due to some bug with NVIDIA drivers. "No NVIDIA graphics driver probed!...Try unloading the conflicting kernel module and/or reconfigure your kernel without the conflicting drivers..." Well, I'm afraid that reconfiguring kernels is beyond my capabilities. Anyhow, after I applied the available updates for 12.04, the graphics problem disappeared. 
Maybe I'll try installing 14.04. Does that support the "gnome classic" interface?

---

### Post by Bucky Ball on 2017-02-26
Why not install 16.04 LTS if you're going to reinstall??? Give yourself another two years support compared to 14.04 LTS. Anyhow, up to you. Yes, Gnome Classic runs on any release. If you simply typed 'gnome classic ubuntu 14.04' (or 16.04) in a search engine you'd soon find plenty of evidence. ;)

If you're lovin' Gnome, perhaps you'd like to [check this]("https://ubuntugnome.org/") if you haven't already. ;)

---

### Post by inkameep on 2017-02-27
Installing 16.04 LTS is what I was originally trying to do, but the installer kept dying due to an issue with the GPU driver. The install did succeed for 12.04 LTS, but under &#8220;System Details&#8221; the Graphics showed as &#8220;unknown&#8221;. I then removed nvidia-*, installed nvidia-current, and activated one of the 2 listed nvidia drivers. That fixed the Graphics entry,which is now displayed correctly as GeForce 210/PCIe/SSE2. But there are still some funny things going on with the display. The bottom line is that I have an outdated video card. I plan to upgrade it before trying to install 16.04 again.  


Thanks for the heads up on Gnome Ubuntu. I'm wondering though if vanilla Ubuntu is likely to be more robust, more widely used, and better supported.

---

### Post by Bucky Ball on 2017-02-27
> **inkameep said:**
> Thanks for the heads up on Gnome Ubuntu. I'm wondering though if vanilla Ubuntu is likely to be more robust, more widely used, and better supported.

They're all Ubuntu. It's the desktop environments and some default apps that are different. :)

Basically, they all sit on the Ubuntu kernel and are then 'tweaked' and customised from there to make the different flavours. Ubuntu-Gnome is Ubuntu with the Gnome desktop and a few default apps they've decided to use. Ubuntu is the Ubuntu kernel using the Unity desktop environment.

You say you want to use the vanilla Ubuntu because it might be more robust and stable. You intend adding the gnome desktop to it. That is not vanilla and, as you will then have Unity and Gnome desktop environments installed, probably less stable than installing Ubuntu-Gnome in the first place. Ubuntu-Gnome, incidentally, is also considerably lighter weight than Ubuntu, meaning there's more chance that would be more stable than a Ubuntu install with Gnome plonked on top.

Good luck. ;)

---


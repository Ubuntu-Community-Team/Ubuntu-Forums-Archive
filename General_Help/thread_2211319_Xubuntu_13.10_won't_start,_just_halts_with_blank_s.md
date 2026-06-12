---
title: "Xubuntu 13.10 won't start, just halts with blank screen??"
date: 2014-03-15
forum: General Help
---

### Post by AlliumPorrum on 2014-03-15
What might be the reason that when I try to start my newly installed Xubuntu 13.10 PC, I always get just a black screen with non-blinking cursor on the upper left corner??

My setup is:
- MB: MSI Z87-G45 GAMING
- Graphics card: Sapphire Vapor-X 280x
- Xubuntu 13.10
- Newest AMD drivers, 14.2 beta

Are there any BIOS settings that could cause this? Any ideas how could I solve the cause for this problem?

---

### Post by bookrt on 2014-03-15
You probably installed it in BIOS mode when it should be installed in UEFI mode. This is happening with a lot of motherboards made in the last couple of years. You need to redo the installation and in your boot options you should have an option to boot the USB stick in UEFI mode. If it boots correctly in this mode, you then just run the automatic installation. 

See this tutorial under "Set up the BIOS in EFI or Legacy Mode":
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by AlliumPorrum on 2014-03-16
But in that page it says: "if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not".

And in a few threads I have read, they all said that legacy mode should always be a best choice.

---

### Post by slooksterpsv on 2014-03-16
If you go into recovery mode (one of your grub options) you can read the logs and see where it's halting at.

---

### Post by AlliumPorrum on 2014-03-16
Thanks for the hint, slooksterpsv! :D

I'm quite noob with the Linux, so could you please give me a bit more detailed instructions; how exactly I get into the recovery mode, and which logs from where I should check??

---

### Post by bookrt on 2014-03-16
Yes, you can install Ubuntu in EFI mode but you have to set your BIOS to EFI mode. If your BIOS is set to boot the USB stick in BIOS mode, it will install in the wrong mode and you will get the blank screen. Go to the UEFI help page, look in the section "Set up the BIOS in EFI or Legacy mode" and follow the instructions to pick EFI mode.

---

### Post by slooksterpsv on 2014-03-16
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) - essentially you hold the shift key before Ubuntu starts to load like where it shows your motherboard logo/info like MSI logo boot screen area.

---

### Post by slooksterpsv on 2014-03-17
I just ran into this problem, even had the AMD 14.2 drivers installed, here's how i fixed it.

Booted up using a different kernel (3.0.11-12 instead of 3.0.11-18); reinstalled the 14.2 beta drivers. Ran sudo rm /etc/X11/xorg.conf
After that I restarted to 3.0.11-18 pressed CTRL+ALT+F2 logged in, and ran - sudo Xorg -configure && sudo mv ./xorg.conf.new /etc/X11/xorg.conf - restarted, Xubuntu finally came back. It was hung up on a non-flashing cursor with 3.0.11-18 until I did the above steps.

---

### Post by AlliumPorrum on 2014-03-19
Thanks slooksterpsv, I'll try that!

One more detail; how exactly did you remove the older version of AMD- drivers? There seems to be numerous ways to do it, I found out after a little googling...

---

### Post by slooksterpsv on 2014-03-19
That worked for me, but I ran into an issue with Qt5-based apps, so I actually got the fglrx drivers from the local repositories to work (but only with kernel 3.11.0-18

EDIT:
And for the fglrx to work I had to remove the xorg.conf file from /etc/X11 and have no xorg.conf file there.

---

### Post by AlliumPorrum on 2014-03-20
Unfortunately that did not work for me. After I removed AMD drivers, the whole system got somehow unstable and the installation of new drivers did not work at all, it just crashed the system again and again :=( I think I'll have to install the whole system from the scratch.

> **slooksterpsv said:**
> If you go into recovery mode (one of your grub options) you can read the logs and see where it's halting at.

What logs exactly; where I could see what happened when the system halted during booting?

---

### Post by slooksterpsv on 2014-03-20
dmesg

You may have to pipe it through less to read it all (pressing up and down to read it). 

R9 Series won't work with the fglrx I apologize I didn't see that that was the video card; you will have to use the beta drivers or wait and see if 14.04 is more stable or wait until 14 drivers are stable (non beta).

---

### Post by AlliumPorrum on 2014-03-23
I installed the whole Xubuntu 13.10 from a scratch, and got the newest Catalyst 14.3 drivers from AMD. Well, the system still won't start, but now it seems the get a bit further... I always get the blue Xubuntu screen with a logo and a white dash going circle. But, then the dash just stops, and it's there, nothing helps. Any ideas for solving this...?

---

### Post by slooksterpsv on 2014-03-23
If you get to the terminal, if you can, by pressing CTRL+ALT+F2 you can log in with your user. Your password won't show as you type it. So just type it and press Enter.

After that's logged in you should be at something like:
john@john-laptop-pc:~$

From there type in:

sudo Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

Now type:

start

and see if that puts you into the GUI.

---

### Post by AlliumPorrum on 2014-03-23
I tried dozen of times, but I just cannot get to the terminal. The screen with username- text in it flashes quickly, but a second it halts the system with a non-blinking curson on a upper left corner :=(

---

### Post by slooksterpsv on 2014-03-23
You'll need to go to recovery mode and remove fgrlx or run /usr/share/ati/fglrx-uninstall.sh

---


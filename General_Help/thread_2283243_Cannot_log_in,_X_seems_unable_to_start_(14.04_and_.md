---
title: "Cannot log in, X seems unable to start (14.04 and 15.04)"
date: 2015-06-20
forum: General Help
---

### Post by cfmackey on 2015-06-20
This problem started about a week ago. I was comfortably running Xubuntu 14.04.2. I decided at some point to do a dist-upgrade.

After my first restart, I was greeted with an all-white screen. Clicking a mouse button revealed the login prompt (strange because I have auto-login enabled), but when I entered my password, the screen went black for a moment and then returned to the prompt. I was able to do a CLI log in via another TTY, but I can't seem to start X.

So thinking it was a bad upgrade, I decided to do a fresh install...first of Xubuntu 15.05. When booting the install media, I got these errors:
[http://i.imgur.com/g9WZefD.jpg](http://i.imgur.com/g9WZefD.jpg)

After the install, the *exact* same issue happened, white screen and all

Then, thinking it was a bug in 15.04, I tried to do a fresh install of 14.04 again. This time there was no white screen, but I the login manager still looped back when I attempted to log in.

When I opened another TTY, I'm greeted with this:
[http://imgur.com/UeCME77.jpg](http://imgur.com/UeCME77.jpg)

I'm really stumped here, I've searched high and low for a solution...the only thing I could find was a suggestion to install an updated version of the session manager, but the PPA provided no longer existed...i tried a different PPA, but the issue was still the same.

The specs of my rig are as follows:
Gigabyte 990FXA-UD3 motherboard, 16G RAM, AMD FX 8350 8-core processor @4.00GHz
AMD Radeon R9 270X with 3 monitors
2 PNY 240gb SSDs, first one with /boot and a Windows 7 installation, second with root and /home for Xubuntu installation
500gb HDD for storage (NTFS formatted)

Any and all help will be *greatly* apprecaited, thank you in advance.

---

### Post by dino99 on 2015-06-20
That makes me thinking about a possible ram voltage issue which i've met on my system (the bios was set on 'auto' about the cpu/ram frequencies, but i realized that this bios was falsely setting a lower ram voltage than required; after switching to 'manual' and setting the good ram voltage for the sticks, the kernel panics and other strange issues have automagically disappeared)

---

### Post by cfmackey on 2015-06-20
Hmm, interesting. I haven't had any issues w/ this mobo and RAM, but I'll have a look at the voltages & frequencies.

I should mention that my Windows 7 dual boot runs flawlessly, haven't had any issues there, but I know as well as anyone that hardware issues manifest themselves differently in different OSes.

I'll have a look at the RAM BIOS settings, and I'll also reseat my RAM for good measure.

---

### Post by wildmanne39 on 2015-06-20
Hi, please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth. 
Thanks

---

### Post by cfmackey on 2015-06-21
My apologies, I thought I *had* posted the URLs. Will fix.

---

### Post by cfmackey on 2015-06-21
Okay so major progress. I had been using Rufus usb ISO writer for windows. I decided to try using PenDriveLinux's usb writer to make and install 15.04, now suddenly the machine boots.

It still seems there are some errors, it takes a while to boot up (and it shouldn't since I'm running off of SSDs).

The only other thing I did differently was I formatted my /home partition, which really shouldn't have mattered because I erased all the config files before installing.

I think the cause of the issue was Rufus, so I'll mark the thread as solved now.

---


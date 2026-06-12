---
title: "File dialogs incredibly slow"
date: 2024-07-23
forum: General Help
---

### Post by yuanzhoulu on 2024-07-23
I just upgraded to 24.04 and file dialogs are incredibly, incredibly slow. The first startup Nautilus takes 30 seconds to show, and any time I hit "save" on anything in Chrome it takes 15-60 seconds to show the dialog and it scrolls like a snail.

I looked like a fool in a virtual interview today because of this when it took me 2 full minutes to send a document over with my video frozen.

How do bugs like this happen, and how do I even start debugging this?

gnome-shell takes 27% CPU just doing nothing, btw. I didn't buy a 7950X for nothing. 32 goddamn cores, 192GB RAM, and this is what I get?

Ubuntu 14.04 was WAAAAAY faster than this.

---

### Post by Rubi1200 on 2024-07-23
Trying to wrap my head around this: you upgraded all the way from 14.04?

Do you get the same issues if you switch from Wayland to Xorg?

---

### Post by currentshaft on 2024-07-23
> **yuanzhoulu said:**
> 
gnome-shell takes 27% CPU just doing nothing, btw. I didn't buy a 7950X for nothing. 32 goddamn cores, 192GB RAM, and this is what I get?

Where is this entitlement coming from? You're not "owed" any performance just because you build a powerful system, but failed to administer it properly. It's like getting pissed at a Ferrari because you curbed the rims.

Also, why did you start an important meeting before testing your equipment? Don't blame Ubuntu for your failure to prepare.

What kind of storage medium are you using? Run "sudo dmesg" and look for I/O errors. Maybe run a SMART check as well; the behavior you described might be due to a failing disk.

Is the graphics driver up to date? You can test it by playing a 4K video and see if it lags/stutters.

Have you installed the latest firmware/bios revision from your mainboard manufacturer?

---

### Post by TheFu on 2024-07-23
An easy way to test whether the issue is with the installed OS/settings or the hardware is to boot into an Ubuntu "Live" environment and see of the same issues happen.  If they don't, then it is something tied to your system.  If they do, try booting from 22.04 ISO to see if the older, but still supported, release also has the same issue.

Also, being precise with specific, accurate, data is important.  The output from an **inxi -Fxxz** command would let people here see the system and software from a high level, perhaps making suggestions.

Sometimes Chrome has less than great defaults.  Try a different browser and see if that helps.  I've never, ever, used Chrome, but I have used other browsers based off Chromium and Chromium itself, until Canonical decided to insist on snap-only distribution.  That actually was the last thing in about 10 things to make me leave Ubuntu Desktops as an OS. I still use some Ubuntu Servers.

I don't know what trying to play 4K video does. It doesn't make sense to me, since I don't have any 4K capable monitors anywhere.  I do know that h.264 and h.265 video decoding is highly dependent on GPU drivers.  Even with the correct drivers, I also know that VP9 video tends to lock up on some of my systems, so I always have to transcode that to a different video codec.

About 4 yrs ago, I had really, really slow dialogs when running programs over an X11-Forward ssh tunnel.  It was only thunderbird. Not Firefox, nor any other program.  Eventually, thunderbird got updated and it became fast again.  I use remote X11 forwards for about 50% of the desktop applications I run.

Is a 7950X some sort of GPU or a CPU?  32-cores sounds small for a GPU and the RAM seems like overkill for any normal workloads.  I struggle to use 32GB of RAM even with 10 VMs running concurrently 24/7/365.

---

### Post by dragonfly41 on 2024-10-12
Try switching between different sessions at point of logon.

I have ...ubuntu, X11, Plasma etc.

---

### Post by seralamp on 2024-10-22
Hi,

I'm experiencing the exact same issue with a Ryzen 9 and 128 GB of RAM. I&#8217;ve noticed that it might be related to Chromium. When Chromium is open, Nautilus takes an incredibly long time to display a folder with many files. However, when I close Chromium, the same folder loads in less than a second. Hope this helps in narrowing down the cause.

---

### Post by dragonfly41 on 2024-10-22
Use a GUI tool Stacer to view processes (6th button down in laft bar) and monitor CPU usage per process and kill hungry processes. You can of course simply use command line (top etc.) but  Stacer can quickly be brought into focus from docky bar to view various resources. It is a cockpit.

---

### Post by darren780 on 2024-10-27
> **currentshaft said:**
> Where is this entitlement coming from? You're not "owed" any performance just because you build a powerful system, but failed to administer it properly. It's like getting pissed at a Ferrari because you curbed the rims.

Also, why did you start an important meeting before testing your equipment? Don't blame Ubuntu for your failure to prepare.

What kind of storage medium are you using? Run "sudo dmesg" and look for I/O errors. Maybe run a SMART check as well; the behavior you described might be due to a failing disk.

Is the graphics driver up to date? You can test it by playing a 4K video and see if it lags/stutters.

Have you installed the latest firmware/bios revision from your mainboard manufacturer?

I have also experienced this since upgrading to 24.04. The files program has clearly been updated and I'm not a fan. But whatever, so long as it can access files in a normal manor, it's fine. But, unfortunately it cannot do that either so thanks to whoever did the bad update. All hardware is brand new and dmesg does not contain anything related to opening a file browser. At the very least, I expect Ubuntu to be capable of opening 'directories' within a reasonable time with default settings. Ferrari does not, to the best of my knowledge, require you to assemble it as well.

---

### Post by ron-smith on 2024-11-24
This is still a major issue for me. It seems to be work in some applications like Opera. Could this be related to snap?  It also seems to happen when it first loads the list of existing files/folders. As long as I keep saving to the same folder it's fine, but if I navigate to another folder, every step that requires it to load the list is slow.  This was definitely not an issue in 20.04 or 22.04. My hardware didn't change. It's something new in 24.04

---

### Post by vlad20012 on 2024-12-08
```
sudo apt remove xdg-desktop-portal-gnome
```

Surprisingly, this seems to help with the issue

---


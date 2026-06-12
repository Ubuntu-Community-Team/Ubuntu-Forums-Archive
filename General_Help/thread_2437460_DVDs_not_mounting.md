---
title: "DVDs not mounting"
date: 2020-02-24
forum: General Help
---

### Post by brightstargiftss on 2020-02-24
Fully updated 18.04. 3 optical drives. 1-DVD 1-Bluray 25G 1-Bluray 100GB.

The only way I can get any disc to mount and display in dolphin is by running k3b in the background. If I don't have k3b running, a disc inserted into any drive gets mounted maybe one in 15 tries. If I open and close the disc tray 15 times, a disc may get mounted properly.

If I inset an optical disc in any drive without J3b running, the drive spins up for a few seconds then goes quiet. If I launch K3b, the disc gets immediately mounted properly. 

As long as K3b is open, all discs get mounted normally when inserted in any drive. Why? What is K3b doing that the automounting isn't?

This has to be a simple one to solve for anyone that understands what happens when a disc gets inserted into a drive. Unfortunately, I don't have clue what to change. 

No errors show up in any file when the disc is inserted and does not get mounted. 

I searched the forums for a long time, but haven't found anything that would lead me to a solution. I tried checking the drive in system settings/removable devices, but nothing makes a difference.

Any suggestions where to look or try would be greatly appreciated.

---

### Post by TheFu on 2020-02-24
What format are the problem disks?  Are they data or video?  With or without DRM?
[https://www.omgubuntu.co.uk/2010/01/bluray-playback-on-ubuntu](https://www.omgubuntu.co.uk/2010/01/bluray-playback-on-ubuntu) says there is a solution - makemkv is a commercial product to rip media from DRM, then it can be viewed.

With DVDs, [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) explains.

Always check the system logs for DVD/BR related messages.

---


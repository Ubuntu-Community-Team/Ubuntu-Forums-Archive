---
title: "No love from Hardy, and no help either"
date: 2008-05-27
forum: General Help
---

### Post by Jvaldezjr on 2008-05-27
Maybe this should be titled "Why I can't and won't update to 8.04"

I've installed Kubuntu 8.04 Hardy to an extra partition on my drive, so I don't wipe out my current system- 7.04.  In doing so, this allowed me to test 8.04 and see what issues I may have, if any.  Well, I never got past the video stage so I didn't get to check things like Samba, print issues, sound, etc.  Also, I was planning on switching from i386 to x86_64 with this release, but that will have to wait now.

When I went to install the nvidia package to the updated drivers and rebooted my system, the driver could not detect my display.  I tried the newest beta drivers, and still the same thing.  I've tweaked my xorg.conf file to try to force detection, and I get EDID errors and a blank, black screen.  So I tried to start a thread about it to get some help, in the meantime I've searched these boards, the nvidia boards, and the nvidia README for answers, only to find that nothing has worked.  I started a thread about it [here]("http://ubuntuforums.org/showthread.php?t=807478") about it, and I've got no responses, which means no one has a clue, no one cares, or other people have similar problems and are looking for help also.  When I tried an earlier driver, I was able to get X working properly, except for one problem.  I lose my login screen if I try to log out, and log back in.  Since I had to remove the package drivers and install the NVIDIA driver's manually, I doubt I'll get help from Ubuntu to fix the problem.  I tried to register with NVIDIA forums to get help, and I can't get a forum admin to authorize my account.

Is the logout "bug" a major issue for me?  No not really since this is a single user system, however if it's not one thing, then it is something else with this release.  I haven't tried to dig deeper, but reading more about the problems, and the sticky thread about the workarounds, leads me to think that "upgrading" would actually be a downgrade for me.  Maybe it's because I'm switching to 64-bit OS, but who knows.  I think I will give up on Hardy and will just stick with Feisty until 8.10 and try my luck again.

I'm simply frustrated, and Hardy has not been as "polished" as I thought it would be.  If any one cares, I was trying Kubutnu 8.04 (with KDE 3.5.9).  I tried KDE4 but that was real unstable, the KWIN effects never worked, and there were some display problems with the window manager.

Maybe in 6 months.

---

### Post by Bubba64 on 2008-05-27
> **Jvaldezjr said:**
> Maybe this should be titled "Why I can't and won't update to 8.04"

I've installed Kubuntu 8.04 Hardy to an extra partition on my drive, so I don't wipe out my current system- 7.04.  In doing so, this allowed me to test 8.04 and see what issues I may have, if any.  Well, I never got past the video stage so I didn't get to check things like Samba, print issues, sound, etc.  Also, I was planning on switching from i386 to x86_64 with this release, but that will have to wait now.

When I went to install the nvidia package to the updated drivers and rebooted my system, the driver could not detect my display.  I tried the newest beta drivers, and still the same thing.  I've tweaked my xorg.conf file to try to force detection, and I get EDID errors and a blank, black screen.  So I tried to start a thread about it to get some help, in the meantime I've searched these boards, the nvidia boards, and the nvidia README for answers, only to find that nothing has worked.  I started a thread about it [here]("http://ubuntuforums.org/showthread.php?t=807478") about it, and I've got no responses, which means no one has a clue, no one cares, or other people have similar problems and are looking for help also.  When I tried an earlier driver, I was able to get X working properly, except for one problem.  I lose my login screen if I try to log out, and log back in.  Since I had to remove the package drivers and install the NVIDIA driver's manually, I doubt I'll get help from Ubuntu to fix the problem.  I tried to register with NVIDIA forums to get help, and I can't get a forum admin to authorize my account.

Is the logout "bug" a major issue for me?  No not really since this is a single user system, however if it's not one thing, then it is something else with this release.  I haven't tried to dig deeper, but reading more about the problems, and the sticky thread about the workarounds, leads me to think that "upgrading" would actually be a downgrade for me.  Maybe it's because I'm switching to 64-bit OS, but who knows.  I think I will give up on Hardy and will just stick with Feisty until 8.10 and try my luck again.

I'm simply frustrated, and Hardy has not been as "polished" as I thought it would be.  If any one cares, I was trying Kubutnu 8.04 (with KDE 3.5.9).  I tried KDE4 but that was real unstable, the KWIN effects never worked, and there were some display problems with the window manager.

Maybe in 6 months.

You seem frustrated, I think we all have been there and will be in the future. Your original thread would probably get a response if you bumped it, maybe several times, since this forum runs on a 24 hr basis the 2 at most hours it sits in the main daily post window if it got there at all, and may have not been read by somebody who can help you. This is a free service and so is Linux so criticizing it will not move towards getting help, I say this in the most friendly way possible, hoping in the end you get the answers you need.

---

### Post by kafkaian on 2008-05-28
I've just upgraded from 7.10 and now have issues with lm-sensors scaling and critical temperature shutdown for which I understand is a problem but still can't find a definitive answer to.

The most stable release for me has been a heavily updated Dapper. Got that working brilliantly and then the features upgrades of feisty, gutsy and heron seemed to have been done at the expense of reliability, solidity and useability.

Edit - However, wouldn't go back to Windows for love nor money.....well unless the money was significant

---

### Post by Jvaldezjr on 2008-05-28
> **Bubba64 said:**
> You seem frustrated, I think we all have been there and will be in the future. Your original thread would probably get a response if you bumped it, maybe several times, since this forum runs on a 24 hr basis the 2 at most hours it sits in the main daily post window if it got there at all, and may have not been read by somebody who can help you. This is a free service and so is Linux so criticizing it will not move towards getting help, I say this in the most friendly way possible, hoping in the end you get the answers you need.

Yea I am frustrated- I dont' remember having this many issues with a release since Warty.  That doesn't mean I'm hating on Ubuntu.  I just feel like a big let down with this release.

---

### Post by Xyem on 2008-05-28
The Ubuntu development team decided to "do away" with xorg.conf and move more towards auto-detection. Perhaps there is a conflict between the nvidia-written xorg.conf and the auto-detect?

I can't really help per se as I don't have 8.04 installed and I don't think I will. Finding out xorg.conf isn't *the place to go* to fix graphics issues really has me riled...

---

### Post by Jvaldezjr on 2008-05-28
I think the auto detection is more of an NVIDIA thing than Xorg.  For some reason I'm still having problems, even with the newest beta drivers.

---

### Post by pmaconi on 2008-05-28
I was having issues with nvidia-glx-new - did you try using nvidia-glx instead? That fixed it for me.

---

### Post by Jvaldezjr on 2008-05-28
no i havent..I'm using that version now with Feisty, and the only problem I have with them is that if I logout, I don't get KDM back to log back in, I only get either a blank Screen or a USplash screen.

---

### Post by Xyem on 2008-05-29
> I think the auto detection is more of an NVIDIA thing than Xorg

If only... > [http://ubuntuforums.org/showthread.php?t=799841](http://ubuntuforums.org/showthread.php?t=799841) ( starting at my post #10 )

8.04 tries to auto-detect by default. nvidia-xconfig ( which you now have to run after installing nvidia-glx* as far as I can gather ) tries to write the xorg.conf "as normal". Which breaks because half of it is still being auto-bork^H^H^H^Hdetected. I can't get nVidia drivers to work on the 8.04 LiveCD ( they don't even show in the Restricted Drivers ).

---


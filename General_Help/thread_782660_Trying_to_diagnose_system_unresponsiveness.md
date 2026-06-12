---
title: "Trying to diagnose system unresponsiveness"
date: 2008-05-05
forum: General Help
---

### Post by enbuyukfener on 2008-05-05
=========================

**EDIT ( June 2008 )**:
For the record, Arch 2008.03 i686 with Arch's nvidia package and a Gnome/Compiz-Fusion/Emerald/NVidia 169.12 environment is working flawlessly, finally I have tab and window switching that can be measured in milliseconds.

I am currently setting it up further and enjoying a proper desktop set up but I'll try to find out what was the factor.

=========================

Hi,

I have the following setup:

Ubuntu Desktop 8.04 with Gnome ([re-]installed about a week ago)
Intel Core 2 Duo 1.8Ghz
NVidia 8600M GT w/ 173.08 drivers
Compiz Fusion + Emerald/Metacity

Since installing (and before with the previous install), I have been experiencing lags and general unresponsiveness particularly in Firefox. This has been accentuated today and it has reached the stage where typing this message is painful. Interestingly, if I run a full screen game or other process intensive application, it runs smoothly.

This has been a problem since Gutsy and trying re-installations, different graphics drivers, different driver versions (currently trying a beta 173.08 which may have caused the current worsened condition), playing around with themes, window managers etc. as well as over an hour of searching the wiki, forum archives and other postings to no avail. I have also tried stripping down the startup programs and services with no noticeable effect.

I am trying to work out ways to diagnose the problem (beyond "ps -A" and "top"). I am also having trouble isolating the problem, disabling Compiz Fusion and Emerald improves matters however the problem is still there.

Some pointers:
- I am using an external monitor for a laptop. Closing the laptop lid turns the external monitor display off. Could it be the system is drawing to both screens (causing extra load)? "nvidia-settings" shows the laptop screen is disabled and using the laptop screen and unplugging the external monitor doesn't help.
- Needless to say, the system is more than capable

I'm reluctant to say this but it is becoming more and more so that Linux is not for me, this has been one problem too far and is a major problem for the reason that it has really performed below my expectations, I was expecting problems but I am not seeing any of the diagnosis and low level control that I expected to be able to solve the problems, or I am missing something (after all, I am a new Linux convert of about 1 year).

Now, I am not an average user in that I am more comfortable and adventurous with the technical aspects as a part time software/web developer and technological hobbyist so is it because I am messing up Ubuntu? Would I be better off with something like Gentoo?

---

### Post by Monicker on 2008-05-05
Have you used System Monitor or the top command to check if any particualr processes have a high usage of the cpu or memory?

I run Gentoo on my primary desktop,and have done so for about a year and a half.  It will definitely force you to "get under the hood" a lot more.  Once you get past the initial install, maintenance is fairly straightforward.

You might consider Debian, from which Ubuntu is derived.  I have used that on my laptop for several years now.  Debian doesn't have the polish of Ubuntu, but learning it will give you a better idea of what is actually happening when Ubuntu tries to shield you from things.

---

### Post by davidpbrown on 2008-05-05
I've had similar and am thinking it's an issue with FF3 being beta version..

I have system monitor in one of the panels, and see high CPU and disk usage when this happens and ps/top show no other unusual processes.

Go back to Firefox 2 maybe.

---

### Post by enbuyukfener on 2008-05-05
> **davidpbrown said:**
> I've had similar and am thinking it's an issue with FF3 being beta version..

I have system monitor in one of the panels, and see high CPU and disk usage when this happens and ps/top show no other unusual processes.

Go back to Firefox 2 maybe.
I must not have phrased what I said clearly, Firefox only makes the issue more obvious, using a lightweight Epiphany/Kazekhadze improves the system responsiveness but the issues are still there, my capable system should not be seeing any of that. And I guess I'm too stubborn to use FF2 considering how much I like the new one and the reduced memory consumption, besides, the release should not be far off (June/July?). I'd try Opera again before Firefox 2.

> **Monicker said:**
> Have you used System Monitor or the top command to check if any particualr processes have a high usage of the cpu or memory?

I run Gentoo on my primary desktop,and have done so for about a year and a half.  It will definitely force you to "get under the hood" a lot more.  Once you get past the initial install, maintenance is fairly straightforward.

You might consider Debian, from which Ubuntu is derived.  I have used that on my laptop for several years now.  Debian doesn't have the polish of Ubuntu, but learning it will give you a better idea of what is actually happening when Ubuntu tries to shield you from things.
Interestingly, nothing seems to show itself as a culprit. I have 2GB RAM and nothing comes close to that, a problem seldom exceeds 5% CPU and if it does, it is a spike and returns to normal state quickly.

I went through about 20 of those performance guides and disabled some more services and rebooted and things are going much more smoothly. Not perfect though but back to the level it was for the months before the reinstall. I'll probably try Gentoo on another partition. And thanks for suggesting Debian, that would be an easier learning curve too.

---

I think it was one of the tracking services that caused the problem. I tried to get rid of tracker and installed beagle but maybe both were running concurrently causing the excessive lag. Disabling both of them seems to solve the issue and makes sense as to why it solves the issues. It seems that they were aggressive with idle processing time computation so every action I done had to wait a while for the indexing to stop hence causing some initial lag, this also explains why resource intensive applications work fine once they get started.

In short, I'm back to "content", even with compiz+emerald on.

---

### Post by enbuyukfener on 2008-05-09
Things have improved, not to an ideal level but satisfactory nonetheless.

Unfortunately, I have tried so many things that I cannot isolate the fix.

Here are some of the things I done:

[LIST]
[*]Played around with CPU frequency scaling
[*]Added the following to /etc/X11/xorg.conf under the "Screen" Section
```
    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
```
[*]Tried to get the custom EDID to only apply to the screen that needs it
[/LIST]

---

### Post by enbuyukfener on 2008-05-10
10 fold reduction in response times by switching to XFCE/Xubuntu. Should have tried that earlier but thought that XFCE would only mask the problem. I still have XFCE + Compiz + Emerald and am currently using NVidia 100.14.19 drivers so things may improve yet with 169.12 and above.

I'm also seeing much less CPU usage with simple actions such as switching tabs in the web browser and other GUI actions such as moving and resizing windows. Maybe it wasn't XFCE that solved the problem, I still have vanilla Ubuntu set up so I may try go back to that and check it out. Maybe something in Xubuntu finally got the computer to start using the GPU instead of overloading the CPU? It's not xfwm as I've mainly been using the Compiz window manager...

Anyway, any thoughts about switching back to Windows or trying a more involved distro are now gone. Hurrah for Ubuntu :D

Am I supposed to mark this thread as resolved? If so, I have not found a way to do so.

EDIT:

For the record, Arch 2008.03 i686 with Arch's nvidia package and a Gnome/Compiz-Fusion/Emerald/NVidia 169.12 environment is working flawlessly, finally I have tab and window switching that can be measured in milliseconds.

I am currently setting it up further and enjoying a proper desktop set up but I'll try to find out what was the factor.

---


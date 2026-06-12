---
title: "[SOLVED] update manager"
date: 2008-02-16
forum: General Help
---

### Post by Riffer on 2008-02-16
[SIZE="2"]On the whole update manager is great, miles better then the MS one.  And I've been updating everything thats been suggested by the manager.  I've noticed though that more then a few updates seems to be un-needed, such as today, support files for Intel graphics.  I have a nVidia card and have the latest drivers etc. why would I need updated support for intel graphics?  Thers been more then a few times that this has happened, but if I choose not to update these things I stll get the flashing icon on the panel.

So how can I choose what is updated and get rid of the flashing icon, and just how stupid is it to second guess the update manager.

                                                                                                     [/SIZE]

---

### Post by bwhite82 on 2008-02-16
Alot of times, what may seem like unneeded updates/packages are actually needed dependencies by other packages. At any rate, the way to get rid of updates to offending packages, is to simply uninstall the packages which have the updates. (Updates wouldn't be offered if you didn't already have those packages installed).

-Cheers

---

### Post by Riffer on 2008-02-16
[SIZE="2"]Was wondering about that, but when I get updates for laptops when I have a desktop, well you wonder.                    [/SIZE]

---

### Post by geirha on 2008-02-16
Ubuntu installs all video-drivers regardless of what graphics card you actually have. You can simply uninstall it if you like. ```
sudo aptitude remove xserver-xorg-video-intel
``` Attempting to remove it will trigger a conflict though, so it will also try to uninstall xserver-xorg-video-all, which is a virtual package that just depends on all video-drivers. Say yes to uninstall that one as well. If you later install xserver-xorg-video-all again, all video-drivers will be installed again. ```
aptitude show xserver-xorg-video-all
``` will display all video-drivers it installs.

An alternative is to look it up in synaptic and lock it. Then no updates will be installed for it again.

---

### Post by MighMoS on 2008-02-16
As stated, you can remove video drivers you don't use and you'll never have to update them again, however I like keeping all the hardware support around, because "in the event of an emergency" I can pull my hard drive from one computer, put it in another, and know that it will still work pretty great -- and the only thing that has to happen is that GDM will tell me that I need to fix my setting if the video card changed, for example.

This is much more robust and preferable to me, than some other popular operating systems that don't deal too well with change. But if you don't plan on doing this, then its pretty safe to remove it.

---

### Post by Riffer on 2008-02-16
[SIZE="2"]Well I did what was suggested and after a couple of reboots and a brief tearing out of hair it worked, so thanks :).  All together by doing that it freed up over 300 mbytes on the HD.

But then again why am I worried about saving disk space?  Just an old habit from the 20 meg HD days I guess.  It doesn't sound like I will get anymore speed or anything by doing this.   

Thanks guys.

                                                                  [/SIZE]

---


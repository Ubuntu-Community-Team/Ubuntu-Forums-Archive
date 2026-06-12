---
title: "Click lock issue on thinkpad's trackpoint when touchpad is disabled"
date: 2017-05-28
forum: General Help
---

### Post by jjdudu on 2017-05-28
I have a laptop thinkpad T450s, it has trackpoint (red pointing stick with physical buttons) and touchpad like this: [https://www.notebookcheck.net/fileadmin/Notebooks/Lenovo/ThinkPad_T450s-20BWS03F00/touchpad.jpg](https://www.notebookcheck.net/fileadmin/Notebooks/Lenovo/ThinkPad_T450s-20BWS03F00/touchpad.jpg)

I would like to use only trackpoint and disable the touchpad on ubuntu. There is a setting to disable the touchpad on the ubuntu.

But I found strange behavior with the trackpoint. Sometimes the trackpoint's left button click registers a click lock effect (as like holding the left button). For example, you're clicking a firefox's tab, then you move the pointer, if the click lock is triggered, you would see the tab is being dragged when you move the pointer. It's very annoying if it happens.

It looks like it happened randomly at first, but I found out it has something to do with the touchpad. I managed to find out how to make the issue happens more often:

1) With the touchpad has been disabled, put your two fingers on the touchpad.

2) With your other two fingers are laying on the touchpad, click the trackpoint left button (click once, don't hold it) on the desktop area, then immediately move the pointer.

If the click lock get triggered, you would see the cursor performs a dragging movement. Here is the video showing how it looks like: [https://vid.me/hLNF](https://vid.me/hLNF)
If the click lock doesn't happen, retry again the step 2.


It seems the touchpad is still generating some signals when touched, even when the touchpad has been disabled. It looks like the two fingers touch could interfere with the trackpoint's left button click and thus produces the click lock effect.

FYI the issue only occurs on linux, it doesn't happen on Windows. The linux distro I've tested so far which produces same issue: ubuntu v17 & v16 (all variants), linux mint v18 & v17 (cinnamon, mate, kde, xfce, lmde), fedora, opensuse, gentoo, manjaro, puppy linux. I think the issue is coming from the touchpad driver which is not compatible with the touchpad hardware on thinkpad T450s. For older thinkpad laptop like T430 or X230, it doesn't have this issue. Same issue could happen on same generation thinkpad with T450s like X250, T450, E450, and probably the newer versions too as it uses same clickpad type design touchpad.

Anyone know how to solve the issue? I have tried disabling the touchpad using synclient & xinput command, but still no avail.

**UPDATE:**
It's a kernel issue. Solved by using kernel v4.12.x or v4.13

**UPDATE2:**
Sadly, the kernel v4.13 on Ubuntu v17.10 still has this issue. Seems only fedora and arch linux that has fixed this issue.

---

### Post by jamesward on 2017-06-21
I have the same issue but it wasn't resolved by upgrading to the 4.12 kernel.  Is it possible there was something else you did?

---

### Post by jjdudu on 2017-06-26
I tried it on fedora v27 and it worked fine. It seems the kernel fix is specific to fedora distro only. More info at here:
[https://bugzilla.redhat.com/show_bug.cgi?id=1313939](https://bugzilla.redhat.com/show_bug.cgi?id=1313939)

---

### Post by jjdudu on 2017-11-22
I just tried Antergos (arch linux based) with kernel v4.13.x and found no issue. So it seems only fedora and arch linux distros that has applied a fix patch on the issue.

A bug report on this issue in ubuntu bug tracker:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1694225](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1694225)

---


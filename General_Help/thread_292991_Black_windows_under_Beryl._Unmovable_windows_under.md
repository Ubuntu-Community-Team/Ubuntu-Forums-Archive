---
title: "Black windows under Beryl. Unmovable windows under Compiz."
date: 2006-11-04
forum: General Help
---

### Post by caspian on 2006-11-04
I've followed the official guides to install both Beryl and Compiz under my computer -- and neither of them are working properly. (I'm not trying to use both of them at the same time -- I just want either one to work)

I've installed the latest Nvidia drivers, which completed successfully. But neither Beryl or Compiz works.

When I launch Beryl, all my windows turn black. Some windows, if I minimize then restore them, the content will reappear -- but some windows (line OpenOffice) will just stay black. The desktop is also black, and restarting Nautilus doesn't bring it back.

When I launch Compiz, nothing apparent happens. But when I try to move my windows, nothing happens (I can't drag them around or minimize them). The applications still respond (They're not locked up) -- the window manager just doesn't work.

This problem is very strange, since neither Beryl or Compiz is working correctly.

I'd greatly appreciate anyone who can help me resolve this issue... or point me in the right direction.

Thanks!

---

### Post by spd106 on 2006-11-05
Have you been following this guide [http://www.ubuntuforums.org/showthread.php?t=263851?](http://www.ubuntuforums.org/showthread.php?t=263851?)

I suggest you remove either compiz or beryl, it isn't good to mix and match. I have problems when I put beryl-manager in the session start-up, I start it manually each time and have better results.

---

### Post by caspian on 2006-11-07
Yes, I used that guide to install Beryl. To install Compiz, I used [http://ubuntuforums.org/showthread.php?t=263840&highlight=compiz](http://ubuntuforums.org/showthread.php?t=263840&highlight=compiz)

I unistalled both compiz and beryl, updated my packages, then installed compiz. Compiz still doesn't work (windows won't move). I can switch windows through the taskbar (No alt-tab), but I can't move the windows at all.

Beryl wasn't working before I installed Compiz, so I know uninstalling compiz and reinstalling beryl won't help.

Am I doing something wrong? Beryl and compiz both worked fine on Edgy Beta -- but they don't work anymore now that I've upgraded.

---

### Post by caspian on 2006-11-07
This might sound really weird... but I reinstalled Beryl, and it now *sortof* works.

Some of my windows are black, but I just need to minimize/mazimize, shade/unshade, close/reopen applications a few times before the windows work properly. As long as I do this dance and jig right each time, my windows work ;).

Ok, so my windows are sortof working... but is there a better way?

Thanks.

---

### Post by risbac on 2006-11-08
If you use the NVidia driver, it's a known bug, not yet fixed. Use Xgl if you want to get rid of the black windows.

---

### Post by caspian on 2006-11-10
Yes, I installed Xgl and it works great. Thanks! Thank you! Thank you SOOO much!!

One (small) problem... when I log into an Xgl enabled session, the taskbar looks old (looks like the old GTK). This might be relating to another problem -- the Gnome theme manager doesn't work, even when I'm using metacity.

Is there a tweak I can use to get this working?

Thanks again!!!

---

### Post by caspian on 2006-11-17
I just found the solution to my old-GTK problem: [http://ubuntuforums.org/showthread.php?t=287317](http://ubuntuforums.org/showthread.php?t=287317)

---

### Post by dpm on 2006-11-17
I just wanted to add my two cents. I'm also affected by the "black windows bug" in beryl, but compiz works fine. I had no need to install Xgl.

I'm using an nvidia GeForce2 MX 400, the proprietary (9629) nvidia drivers and compiz-freedesktop.org 0.2.2.

---

### Post by inexistentia on 2006-12-07
I am having the same problem.  I found that if I resize a 'black' window so that it is smaller it restores the contents.  Interestingly, if I then expand another window past a certain threshold, it will lose its contents.  I suppose it's something to do with memory allocated to drawing the windows in Beryl?  I've only had this problem when my display has been larger than 1600x1200 (running a 7100GS)

---

### Post by caspian on 2006-12-07
Yes, I've experienced this problem occasionally. I've found that restarting X normally solves it.

---


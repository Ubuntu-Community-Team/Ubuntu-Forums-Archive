---
title: "Touchpad problem after update"
date: 2020-01-17
forum: General Help
---

### Post by sarisisop on 2020-01-17
Ubuntu 18.04.3 LTS
Samsung laptop

Hello, my laptop updated this morning and since the update my touchpad is now only working on one side. The left hand side works as it did, but the right hand side can only be used for scrolling up and down. 

All was fine before the update.

Any help appreciated. 

Thank you.

---

### Post by sarisisop on 2020-01-19
I have done a little digging around but ended up following some advice on the internet about installing synaptec, that ended up with everything freezing and in the end I had tp do a complete new install. 

It looks like I have ETPS/2 Elantech Touchpad

Also this someone else is having the same problem: [https://ubuntuforums.org/showthread.php?t=2433912](https://ubuntuforums.org/showthread.php?t=2433912)

If I turn off Edge Scrolling I can use all the touchpad, but when I turn it on the touchpad only works on the left hand side and the scrolling takes up 50% on the right. 

Before the update the scrolling was only on the very right hand side about a finger width.

Anyone help please ?

---

### Post by sarisisop on 2020-01-28
Still looking for help with this if anyone can help please.

---

### Post by MoebusNet on 2020-01-28
Although I do not have that touchpad, if the touchpad worked properly before the update then it sounds like a bug to me. I would see if other people have found the same bug and probably file a bug report. This webpage will tell you how: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by sarisisop on 2020-01-29
> **MoebusNet said:**
> Although I do not have that touchpad, if the touchpad worked properly before the update then it sounds like a bug to me. I would see if other people have found the same bug and probably file a bug report. This webpage will tell you how: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Mmmmm sorry but I don't understand how to report a bug even after reading that page.

---

### Post by MoebusNet on 2020-01-29
OK, first let's decide what you want to do. If you're willing to live without Edge Scrolling, you can probably just live with things as they are until the next kernel update which will hopefully solve the issue. Everything I've read about this leads me to believe that this is a kernel issue; however I can't test this because I don't have that touchpad. If you must have Edge Scrolling, I would try to use the previous kernel (the one that was working before the last update). You basically do that by booting with the 'Shift' key depressed and selecting the older kernel when the Grub menu appears. Details on how to do this are here: [https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

Finally, since this appears to be an issue that affects a number of people, you can either wait for a fix to appear - or you can use this as an opportunity to see how things get fixed in Ubuntu (and Linux in general). The bug reporting website I referred you ([https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)) to has a section down the page that applies in your case: 'Reporting non-crash hardware and desktop application bugs'. At a basic level it involves getting a username and password registered with the Launchpad bug-reporting site, and following the examples to report a bug in the package that affects you; in your case the kernel.  If you care to take the time to read and experiment a little, you should be able to make it work. Or, it might be that you want to learn more about Ubuntu and Linux before trying that out. That's fine, too.

---

### Post by sarisisop on 2020-01-30
Hello MoebusNet, as you can probably tell I'm that up on the technical side of these things. 

I tried following the how to report a bug and put this in a Terminal ubuntu-bug kernel
But it gave me this: dpkg-query: no packages found matching kernel
Gtk-Message: 15:54:21.659: GtkDialog mapped without a transient parent. This is discouraged.

I would like to try and give feedback to help with a fix, but I'm obviously trying to do it the wrong way.

As for using a previous kernel, I think I better give that idea a miss as I've had to do a new instal and woulld hate for it to go wrong. Plus as it's anew install I doubt there would be an old kernel ?

I do need side scrolling as I have problems with my fingers, but for now I can carry on using half the touchpad. It's not ideal, but if a fix is on the way then I better just wait. 

Thank you though for your help.

---

### Post by MoebusNet on 2020-02-04
Sorry for not responding earlier; haven't been on the forum. As a workaround, you might consider plugging in a USB mouse and using that until a fix arrives. Indeed, some people prefer to use an external keyboard and mouse or external keyboard/trackpad combination. The  ETPS/2 Elantech Touchpad apparently has a known history of issues with Linux which has been fixed before and probably will be again.

You mention that your issue appeared after an update because the trackpad worked correctly before the update. Since you seem to have been comfortable enough  to reinstall once, I suppose you could always reinstall one more time and then go without updates for a month or so to give time for a fix to appear. As far as using a previous kernel is concerned, the method I mentioned would initially be only for that one session unless you made the choice to disable the new kernel. I hope I've offered some choices to keep you going; best of luck!

---


---
title: "How to stop screen tearing by enabling Vertical Retrace Synchronization (vsync)"
date: 2019-04-05
forum: General Help
---

### Post by silverdice on 2019-04-05
Hello forum,I am using Ubuntu 18.04.2 LTS amd64, with an AMD Radeon 590  graphics card.

By default, there appears to be massive tearing in just about everything you do. Moving windows, watching a movie, watching Youtube, everything!Besides being annoyed, I am surprised! How is it possible that in 2019, by default with modern hardware and software, users get to see screen tearing? How is that possible? Why is the default not to avoid screen tearing by waiting for vertical retrace (vsync) ?Many search results go back to 2010 and stuff, which appear to be outdated. 

One source for 18.04 and AMD graphics cards suggested the following, which i tried
```
sudo nano /usr/share/X11/xorg.conf.d/20-radeon.conf
```
And enter:
```
Section "Device"    
Identifier "Radeon"    
Driver "radeon"    
Option "TearFree" "on"    
Option "DRI" "3"    
Option "AccelMethod" "glamor"
EndSection
```
Sadly, it did not work. Also not after ```
sudo service gdm restart
``` and a full reboot.Even worse, before i rebooted, it appeared that the gnome panel was broken, because launching certain applications such as the file manager (nautilus) and the text editor (gedit) did not work; clicking the icon did nothing except showing a 'loading' mouse cursor. When launching 'gedit' from the gnome-terminal, it worked again. After rebooting, the issue appears to be gone.

I so much hope one day there will be an open-source operating system where 'things just work' like virtually all users want to! Until then, can you people be so kind as to direct me to instructions on how to fix the screen tearing issue on my system?
Many thanks in advance for your efforts and time!

---

### Post by silverdice on 2019-04-05
And can somebody tell me how to properly insert line breaks on this forum? My previous post is unreadable without it.

---

### Post by ajgreeny on 2019-04-05
I can't help you with the AMD graphic card but for the line breaks in your post, which I have now added along with [Code Tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168"), we need to know how you added the text to your post; did you create a text file and then copy that into the "Post new thread" text-entry box or did you type it directly into the box?

I just type and the box wraps text at the right hand edge as you would expect with no specific line breaks added manually; it does it automatically.
For a new paragraph just hit Enter when you want one or hit Enter twice for a double spacing of paragraphs to aid readability even more- just like my post here.

---

### Post by silverdice on 2019-04-05
Indeed i copy-pasted it from 'gedit' which i use so that if anything goes wrong with my browser, i do not lose my text. Particularly when asking things, it tends to be a longer post.Just testing a paragraph here; maybe it works like you suggested, that i have to press enter inside the text box, and not copy-paste things.EDIT: hmmm unfortunately it still does not work! I just tried enters to have line breaks, but it does not work :(

---

### Post by freemedia2018 on 2019-04-05
> **silverdice said:**
> Indeed i copy-pasted it from 'gedit' which i use so that if anything goes wrong with my browser, i do not lose my text

I would think that gedit (or geany) would more than suffice for this, but if those don't work you can always use leafpad for the task. Be sure to enable word wrap.

---

### Post by speartip on 2019-04-06
> How is it possible that in 2019, by default with modern hardware and  software, users get to see screen tearing? How is that possible?
I would think because AMD do not provide a decent graphics driver for Linux.
Have you checked in "Additional Drivers" to make sure there is no proprietary drivers available there?

---

### Post by Autodave on 2019-04-06
You could always install the PRO drivers.  I have done this on my old machine: there was a little gain in FPS.

[https://www.amd.com/en/support/kb/faq/gpu-635](https://www.amd.com/en/support/kb/faq/gpu-635) will tell you how to do this.

---

### Post by deadflowr on 2019-04-06
Doesn't that card use the amdgpu driver instead of the radeon driver?
I guess there has been some work recently to get it running right:
[https://www.phoronix.com/scan.php?page=news_item&px=RX-590-Linux-All-Is-Good]("https://www.phoronix.com/scan.php?page=news_item&px=RX-590-Linux-All-Is-Good")
and the aforementioned padoka ppa:

[https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa]("https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa")
(scroll way way down to the how to add this ppa , the description section is sorta long)

---


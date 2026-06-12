---
title: "frozen mouse"
date: 2012-11-06
forum: General Help
---

### Post by gleble on 2012-11-06
I have  just instaled ubuntu and I have a frozen mouse
Help

---

### Post by bjforesthowell on 2012-11-06
Is your keyboard frozen as well? Because I'm working on three other threads right now where that's the issue...

[http://ubuntuforums.org/showthread.php?p=12337832#post12337832](http://ubuntuforums.org/showthread.php?p=12337832#post12337832)

[http://ubuntuforums.org/showthread.php?p=12337827#post12337827](http://ubuntuforums.org/showthread.php?p=12337827#post12337827)

[http://ubuntuforums.org/showthread.php?t=2059135&page=2](http://ubuntuforums.org/showthread.php?t=2059135&page=2)

If it's a logitech wireless mouse (and I know that this sounds elementary) try unplugging the receiver and plugging it back in. That's helped for me in the past.

---

### Post by gleble on 2012-11-06
I havn't got an exIernal mouse.  
It boots with  the mouse frozen in the middle of the screen

---

### Post by bjforesthowell on 2012-11-06
I've got an NVIDA vido card and this worked for me after working with NikTh (nick-athens30) on launchpad....

During boot you're going to see a purple screen with no Grub options if you're not dual booting. When you see that purple screen hold the [SHIFT] key until grub menu appears and select "Advanced settings".

At this point, you're going to want to select the kernel with the recovery mode options and just hit enter at the next screen.

Once I was in recovery mode I had my input devices and everything was gravy. I was able to run the software update then, while I was in I installed drivers with the directions from this site...

[http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html)

Now my global menu and launcher aren't coming up, but this shouldn't be a problem to fix now that I've got input devices.

I hope this helps...

---

### Post by bjforesthowell on 2012-11-07
If you've got an Nvidia video card here's how you get your top menu and launcher back after you have access to your input devices...

[http://askubuntu.com/a/202587/104413](http://askubuntu.com/a/202587/104413)

---


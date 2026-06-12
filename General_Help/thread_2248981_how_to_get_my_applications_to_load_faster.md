---
title: "how to get my applications to load faster"
date: 2014-10-18
forum: General Help
---

### Post by kccv42 on 2014-10-18
I have notice that my applications have taken some time to load up. The application i have notice the problem the most is Mozilla Firefox. Here are my specs of my computer: 2.3ghz amd single core processor, 2gb ram, 250 gb ssd.

---

### Post by Vladlenin5000 on 2014-10-18
Depending on your graphics card/chip and its driver, standard Ubuntu (with Unity) may be part of the "problem"...

---

### Post by glyczak on 2014-10-18
The most likely issue is that you have **insufficient RAM**.  All applications use RAM, some more than others (**especially browsers**). You can view how much RAM is available in "**System Monitor**" under the "**Resources**" tab.  If you decide to invest in more RAM you can find a variety of online tutorials on how to replace your RAM.

---

### Post by deadflowr on 2014-10-18
You might look at the package called preload.

---

### Post by buzzingrobot on 2014-10-18
One way to avoid startup delays is avoiding closing the app. If you don't need to shutdown, don't. Set a time out to suspend, and/or suspend manually.

Firefox is a large app, and requires more memory if you install some extensions. Two gigs, though, is more than sufficient.

---

### Post by O9aIevckc0 on 2014-10-18
you might want to try preload as suggested by  deadflowr (assuming you have enough spare ram)
 

 you can install it with the below command
 sudo apt-get install preload
 

 Its  possible that your using an old processor that cant keep up with your ssd
 I found that when using a ssd there is quite a difference in load time (and boot time) between an old processor and a newer one.  
 

 Judging by the amount of ram the clock speed and the fact that the CPU is single core I would guess the computers somewhat old and that it may be the CPU though without more detailed information on your hardware I cant be sure

---

### Post by papibe on 2014-10-18
Hi kccv42.

A few thoughts:

To gain most of the performance an SSD can offer make sure:
[LIST]
[*]you are running a version that supports 'trim'.
[*]the trim script is set and working, and
[*]that the SSD's trim capabilities is supported by Linux.
[/LIST]
The amount of RAM may or may not a factor. If you reboot your computer, get into the desktop and experience the same speed while loading FF, then adding more RAM won't solve that problem. On the other hand, if you experience lag when launched while several applications are open, or while switching between applications, adding RAM would improve the performance.

I'm not very good evaluating AMD processors, but it looks like it is an equivalent of a Intel celeron, or a P4 maybe? If that's the case you are stretching the limit of experiencing smooth performance while running regular Ubuntu. Vanilla Ubuntu uses a composite desktop that requires video hardware acceleration to render smoothly. Adding a discrete graphic card may improve performance, but since (IMHO) your hardware is on the limit, I'd suggest trying Xubuntu or Lubuntu.

If you open and close FF frequently, you may gain some speed using 'preload' from the 'Software Center'. Note that if you, like most of us, open FF and then leave it open for most of the session, preload won't help you much.

Just some thoughts. Let us know how it goes.
Regards.

---

### Post by ibjsb4 on 2014-10-18
> **deadflowr said:**
> You might look at the package called preload.
+1 
[http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html](http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html)

---

### Post by kccv42 on 2014-10-18
Tried to install preload. Will it automatically work or do i need to type "preload" into the terminal?

---

### Post by ibjsb4 on 2014-10-18
It will run automatically in the background.  Also it will not work as soon as you install it.  Preload will monitor your apps usage and apply changes, it can also be tweaked a bit.

[https://www.google.com/search?client=ubuntu&channel=fs&q=preload+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=preload+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by tgalati4 on 2014-10-20
Try clearing your cache in firefox or deleting your profile and starting with a fresh profile.

---


---
title: "Access To Terminal w/o Loading xserver"
date: 2007-08-07
forum: General Help
---

### Post by iAndrew on 2007-08-07
Hi, i've searched for this. Nada.

Anyways, I downloaded Automatix, and installed it. It went fine, I installed nvidia drivers, and now xserver won't load. It doesn't display the normal error message where it turns it off. The screen is just black.

I was wondering if there was something I could do a boot up to stop xserver from loading.

I cannot access linux, I'm using my second computer to type this.
Because after getting to the terminal, I'd just reset the xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

Unless there are any other ways?

---

### Post by merlinus on 2007-08-07
What happens if you press Ctrl-Alt-F1?

Are you getting to the opening grub menu?  If so, you can try booting into recovery mode.

-merlin

---

### Post by iAndrew on 2007-08-07
Let me try it again. I kinda forgot.

---

### Post by aysiu on 2007-08-07
Alternatively, boot into recovery mode--this will give you a full-screen terminal logged in as root. From there, you can ```
dpkg-reconfigure xserver-xorg
apt-get remove automatix2
shutdown -r now
``` By the way, is the Restricted Driver Manager not working for you?
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by hikaricore on 2007-08-07
> **iAndrew said:**
> Hi, i've searched for this. Nada.

Anyways, I downloaded Automatix, and installed it. It went fine, I installed nvidia drivers, and now xserver won't load.

In the future be aware that Ubuntu Forums does not recommend the use of installer scripts such as Automatix, they can (and have) broken many a system configuration.

Here is a recent (and very popular [digg/slashdot]) technical article on the troubles with using Automatix: [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by iAndrew on 2007-08-07
@ hikaricore: Oh okay, I was just following HowToForge Tutorial.

@aysiu: yeah, restricted drivers aren't popping up.

I got a video,

bear with me its hard balancing a camera and moving the other hand.

STILL UPLOADING ==[n/a]

I'll try booting in recovery mode.

---

### Post by aysiu on 2007-08-07
> **iAndrew said:**
> 
@aysiu: yeah, restricted drivers aren't popping up. Weird. When you get your X server working again, can you post the output (especially error messages) of this command? ```
gksudo restricted-manager
```

---

### Post by iAndrew on 2007-08-07
I'd be happy too. Just as soon as I get it working ;).

Video is still uploading.

---

### Post by por100pre1 on 2007-08-07
> **hikaricore said:**
> In the future be aware that Ubuntu Forums does not recommend the use of installer scripts such as Automatix, they can (and have) broken many a system configuration.

Here is a recent (and very popular [digg/slashdot]) technical article on the troubles with using Automatix: [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

Here's an example of those troubles; after some reading about Automatix, I decided to uninstall it. But before uninstall I opened Automatix and click the "remove Automatix repositories" and then Automatix did it's thing: it removed its repos and messed up the others. So I ended up editing my sources.list manually. Good Bye Automatix! :rolleyes:

---

### Post by iAndrew on 2007-08-07
Its fine, I just speed right through the reconfiguring of xserver.

Anyways: @aysiu : I didn't get a log or anything.

Just keeps saying the same dialog box:

[IMG]http://i180.photobucket.com/albums/x160/igotandrew/Ubuntu/DRM-Pic.png[/IMG]

Yet, it did not detect my video card.
----

This is why I like open source, all the help.
Thanks alot guys and girls.

---

### Post by aysiu on 2007-08-07
I know this is a dumb question, but are you sure you have an Nvidia graphics card?

---

### Post by iAndrew on 2007-08-07
Yeah, it works with the windows xp I dual boot with.

NVidia GeForce 8600 GT. I even have the box to show for it. If you really need to see it.

---

### Post by aysiu on 2007-08-07
> **iAndrew said:**
> Yeah, it works with the windows xp I dual boot with.

NVidia GeForce 8600 GT. I even have the box to show for it. If you really need to see it.
Can you perhaps install it through Synaptic Package Manager? Either *nvidia-glx* or *nvidia-glx-new* should do.

---

### Post by hikaricore on 2007-08-07
If I'm not mistaken aysiu the drivers in the Feisty repo are pre 100 series and may not support that card.

He may have to get the binary installer from Nvidia.

> Version: 100.14.03
Operating System: Linux x86
Release Date: April 20, 2007

Release Highlights

    * _Added support_ for GeForce 8600 GTS, _GeForce 8600 GT_, GeForce 8500 GT, GeForce 8400 GS, and GeForce 8300 GS



---

### Post by aysiu on 2007-08-07
> **hikaricore said:**
> If I'm not mistaken aysiu the drivers in the Feisty repo are pre 100 series and may not support that card.

He may have to get the binary installer from Nvidia.
In that case, pasting this command in the terminal may do it: ```
wget -c http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run && sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```

---

### Post by hikaricore on 2007-08-07
Sorry to interrupt.  ^_^

I just remembered posting about it on UGA.

*runs away and hides*  hehe

---

### Post by iAndrew on 2007-08-07
I'll try this out. I've seen thsi driver on the nvidia site. Just didn't know how to execute it.

---


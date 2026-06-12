---
title: "Small black squares in upper left corner of screens"
date: 2008-05-01
forum: General Help
---

### Post by duggum on 2008-05-01
Hiya all!

I just installed Hardy and have a strange issue.

For some unknown reason there is a small black square (approx. 10x10 pixels) in the upper left corner of each of my screens. In the attached screenshot I have a Nautilus window expanded across the top from the left screen to just past the upper left corner of the right screen. In the title bar you can clearly see the two black squares.

At first I thought they might be a stray tray icon that got detached but that wasn't the case. In fact, clicking on the square passes through to the window beneath it and I am able to, for instance, access the client menu that is available when clicking on the application icon in the upper left corner of the app window.

So far there have been no ill effects from this issue, but it is a bit annoying. Before I try reinstalling I was hoping someone might be able to help me sort this out.

It is worth noting that I have installed Hardy on my wife's computer and this problem has not shown up on her machine. Also, I am running a dual monitor setup with a single nVidia 6600GT, dual-DVI graphics card. My wife's computer has an nVidia card as well, so I don't think it is an nVidia issue.

Thanks,

duggum

---

### Post by ryanhaigh on 2008-05-01
Strange issue, my only thought would be a problem with compiz as it can use those areas to perform defined tasks. What happens if you turn of desktop effects.

---

### Post by duggum on 2008-05-01
ryanhaigh,

The screenshot was taken with compiz disabled. That was my first thought as well.

It turns out the problem was with usplash. While changing all the settings required to get a higher console resolution (activating vesafb, adding vga=XXX to kernel opts, etc.) I also added my resolution settings to usplash.conf. Unfortunately, I changed usplash.conf AFTER running "update-initramfs" to finalize the vesafb changes.

It seems the black squares are the result of an incomplete usplash modification. They have since been eradicated completely.

Thanks for the reply.

duggum

---

### Post by Sutur on 2010-10-10
> **duggum said:**
> It turns out the problem was with usplash.

Thanks mate, confirming that removing usplash packages fixes the original issue on my system. Don't care for usplash anyway :)

---


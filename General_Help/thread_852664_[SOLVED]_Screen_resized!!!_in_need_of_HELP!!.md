---
title: "[SOLVED] Screen resized!!! in need of HELP!!"
date: 2008-07-07
forum: General Help
---

### Post by Kain000 on 2008-07-07
Hey everyone,
I've been searching around but have yet to find anything that works.

I need to change the screen resolution of my server computer, I use remote desktop viewer to use and update it without having a monitor or keyboard sitting around, but last night it wouldn't boot all the way.  when I plugged a monitor in, it tells me that I need to configure the display device or run in low graphics mode, I pushed configure and now it defaulting to a 640x480 resolution mode and doesn't give me any options to change it.  It wasn't always that way even with no monitor plugged into it.

any help?

-sean

---

### Post by DJYoshaBYD on 2008-07-07
are you running a flat screen? If I remember correctly, you have to use some special file to make a flat screen work.. that was just for me and feisty, though.. I think it depends on the chipset of the motherboard, and that file(s) being in the system.. just a suggestion.. its a problem I ran into, and I found a post on how to fix it..

sooo.. flat screen?

---

### Post by Kain000 on 2008-07-07
yeah it was a flatscreen originally but once configured the server had no screen attached and i remote desktoped into it to admin everything.   However even when I plug the screen back into and try an auto detect under the screen resolution option under system>prefs>resolution and it wont auto detect anything, and remains the same size.

---

### Post by DJYoshaBYD on 2008-07-07
yeah.. do a bit of searching, and you will find that.. my friend had an Intel chipset, and a flat screen.. on my tv and crt monitor, it was fine.. but it did the same thing on his flat screen, after working fine here.. thats more than likely the problem..

what chipset is on your motherboard? If its an nvidia chipset, with an onboard nvidia graphics adapter, you should be able to download envy, and use that to install the nvidia drivers and screen settings program associated with it..

if its an nvidia chipset, then download envy from here

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

install that.. then restart the pc

go to a terminal, and type the following

```
sudo nvidia-settings
```

change your resolution, click apply, then click save to x configuration file

but this will only work if you have an nvidia chipset.. if its not, then you need that file I mentioned.. I really wish I could remember the name..

try searching for

intel chipset flat screen ubuntu

or something like that... hope this helps, somewhat...

---

### Post by Kain000 on 2008-07-08
> **DJYoshaBYD said:**
> yeah.. do a bit of searching, and you will find that.. my friend had an Intel chipset, and a flat screen.. on my tv and crt monitor, it was fine.. but it did the same thing on his flat screen, after working fine here.. thats more than likely the problem..

what chipset is on your motherboard? If its an nvidia chipset, with an onboard nvidia graphics adapter, you should be able to download envy, and use that to install the nvidia drivers and screen settings program associated with it..

if its an nvidia chipset, then download envy from here

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

install that.. then restart the pc

go to a terminal, and type the following

```
sudo nvidia-settings
```

change your resolution, click apply, then click save to x configuration file

but this will only work if you have an nvidia chipset.. if its not, then you need that file I mentioned.. I really wish I could remember the name..

try searching for

intel chipset flat screen ubuntu

or something like that... hope this helps, somewhat...

thanks for the help!  thats one problem off my list. lol
it's working again fine, I can actually see all my desktop again!  hazzah!

---

### Post by Kain000 on 2008-07-09
turns out that when the monitor isnt plugged into the server it freaks out and defaults into low graphics mode.. hence the low resolution.

---


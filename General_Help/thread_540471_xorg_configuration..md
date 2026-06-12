---
title: "xorg configuration."
date: 2007-09-01
forum: General Help
---

### Post by crabhunt on 2007-09-01
Hi,

I have a thinkpad laptop which I connect to two different flat monitors depending on workplace or home, they have different resolution max limits. Is it possible that when I boot the laptop with any of these two laptops it automatically detects the resolution of the monitor and sets up the configuration, how can I do that with configuring the xorg.conf file ?

regards,

---

### Post by forestpixie on 2007-09-01
I have two connected to my desktop - monitor and tv - set up as separate X screens - I only use the tv for films. They are generally both connected - BUT if one is disconnected the other still works fine.

So I guess it shouldn't be a problem - depending on your graphic card/chip - with nvidia you can use nvidia-settings to do it. Not sure about ati or intel 

You need to make sure your graphics are set up first

---

### Post by crabhunt on 2007-09-01
> **forestpixie said:**
> I have two connected to my desktop - monitor and tv - set up as separate X screens - I only use the tv for films. They are generally both connected - BUT if one is disconnected the other still works fine.

So I guess it shouldn't be a problem - depending on your graphic card/chip - with nvidia you can use nvidia-settings to do it. Not sure about ati or intel 

You need to make sure your graphics are set up first

The basic setup for the graphics just to work on the laptop is set and its works fine for the laptop... the problem is that the external monitor supports a higher resolution that my laptop monitor and its larger in size so I would like it to work at its best resolution but by just adding another entry for the MONITOR section and SCREEN section in xorg.conf file the external monitor doesn' t work at the resolution I would like it to work.

---

### Post by forestpixie on 2007-09-01
no expert here - but I would expect you'll need to make the graphics set  up work properly for the external monitor 

Are there restricted drivers available for the graphics - if so are you using them?

Are the resolutions you want for the external monitor actually available ?

Maybe you can reconfigure X and specify the resolutions you need there - then apply them in xorg?

What graphics card is it using - a bit more info/specs might help someone else sort it for you.

```
lspci
``` in a terminal would give a bit more

---


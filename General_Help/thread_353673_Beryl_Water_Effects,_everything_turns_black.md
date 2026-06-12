---
title: "Beryl Water Effects, everything turns black"
date: 2007-02-05
forum: General Help
---

### Post by Fade Away on 2007-02-05
Whenever I do anything with water, all the windows except the one I'm using turn dark and almost black.

If <shift><super>Button 1 and drag around, it all goes black/dark.

I get the water effect, it just covers everything up.

---

### Post by eXisor on 2007-02-05
The water effect seems to have been rewritten in ages past and now it only works on some vga cards (not mine).

Check the .xsession-errors file in your user home directory (it's hidden) to see what errors beryl is throwing.

or 

You'll need to start beryl from the terminal to see what errors are being thrown. 

If you don't know how: first set window manger to meta (or whatever your desktop default is).
Then,

```

sudo killall beryl
sudo killall emerald
beryl-manager

```

and try the water again. Post back what you get.

---

### Post by Freaky_Llama on 2007-02-05
I have the issue too, but I just lowered the 'initial vertices' setting significantly, and now I have waves when i move windows, but it don't turn black (it still sometimes flashes black really REALLY fast on resizes only). However, yes, the waves are shorter, but IMHO, it looks better and more subtle.

Under water effect:

Offset Scale:        .5500
Water Viscosity:  .2000
Initial Vertices:    200

---

### Post by Fade Away on 2007-02-05
So, when I run it through terminal, nothing happens, it throw me any errors.

If I turn it down to your settings, it work when I move windows, except for about half a second it still turns all black.

I think if I turn it down more, maybe it will work.. but it's lame..

I had it working perfectly before.

When I had beta before it went to rc1.

Everything was great, and now I don't have water :( I am sad.

EDIT--Thing is, I know it can display it when it's pushed up higher, because when I set it higher, meaning it has big waves, I can move a window, it will turn black, then I move it around and it'll show the big wave on my normal background as long as I'm moving the window around.. so.. it's not like I can't do it.

---

### Post by Freaky_Llama on 2007-02-05
I understand what you mean. I'd like a little move waves on mine too. 

What graphics card do you have? I'm running an XFX nv 7900GS pci-e.

I saw something in the beryl-manager that mentioned turning off blur for nvidia users having the black window issue, so I'm sure its a known bug. Even with blur off, I still had issues. The black window issue may have 'spread' too if its something with nvidia drivers.

---

### Post by Fade Away on 2007-02-06
I dunno what the deal is, because it worked with beta.. but now it just fails..

I have either a NVIDIA Quadro NVS 110M or a NVIDIA Quadro NVS 120M, I don't remember which.

---

### Post by Fade Away on 2007-02-08
Anyone know anything about this? Like... how to fix it?

---

### Post by Fade Away on 2007-02-22
I figured it out!

General Options>Main

Uncheck Sync to VBlank.

Did it for me!

---


---
title: "Ubuntu on Tablet PC"
date: 2008-02-13
forum: General Help
---

### Post by Yonderknight on 2008-02-13
Hi, I'm running ubuntu on my Gateway C-140x

So far it's been great! All the drivers and things got configured correctly and now everything's running smoothly.

I am having some trouble finding software made for tablets though. Mainly, I need a good program to take class notes in (maybe pressure sensitive), and also a utility that can rotate the screen properly when my swivel is rotated. When I go to the gnome system resolution utility, the "Screen rotation" option is disabled. Is this because I'm using restricted ATI graphics drivers?

Thanks in advance.

---

### Post by Yonderknight on 2008-02-13
Okay, sorry to double post but I've kind of narrowed down my problem...

I figured out to get the screen to rotate I can use the command "xrandr -o left". The problem is that this gives me an error (like many other cases I've seen on this forum):

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

Anybody know how to fix this? My tablet is pretty much useless without it, I'd have to be using the thing upside-down with the screen slanted away from me in order to use it closed. =(.

Also, I need something that will let my "type" when the screen is closed. I found a program called cellwriter ([http://risujin.org/cellwriter/](http://risujin.org/cellwriter/)). When I try to install the .deb package though, it says: "Error, wrong architecture 'i386'". Is this because I'm running 64-bit ubuntu? I wasn't even sure if I needed to run 64 bit or not (I'm using intel core 2 duo so i figured it's 64 bit.). Is there any way for me to use this? I couldn't find any other software that offers a "writing pad" that can just convert what I write into text. Anybody know of any alternatives?

And I guess that's about it. I'll need to figure out how to map the buttons on the screen to rotate the screen and stuff though, but I think i can figure that out on my own.

Oh yeah, also, I'm having a trouble with Suspend. When I put the system into suspend, I can't get it to wake up again. I press the power button and any other key but nothing happens. It doesn't seem like it's in sleep mode either (The power light usually dims on and off when i did this in winXP, but in ubuntu it just remains on even when it's in suspend mode).

Thanks in advance if anyone can solve any of these problems!

---

### Post by fragos on 2008-02-14
Not all software has 64 bit versions.  I find life much easier by running a 32 bit kernel.

---


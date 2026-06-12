---
title: "Tv Tuner in Hardy (ITV 301) is not auto recognizable"
date: 2008-05-23
forum: General Help
---

### Post by Randall Flagg on 2008-05-23
Hello..

I'm having a problem with a Tv-Tuner.
The Chipset is ITV-301, and the brand.. well, its suppose ti be a brand like you can say ACER or something.. this is more.. no brnad like .. :P

well, but making a research of this, looking if my UBUNTU hardy will see my hardware that is Not recognize when OS run, I find out that since kernel 2.6.24, there is support for this tv tunner, and even better, I'll be able to use the control remote it has integarted ...

Now, the thing is that I don't know how to make my OS to see my hardware... A friend of mine who uses CentOS told me he ReCompilate the kernel to make the OS to see the hardware... (the recompilation part I didn't like it that much.. )

Googling I find my self with this...
But don't want to screw my ubuntu for making some kind of weird instalation I don't understand that well...
(i found this --> [http://popey.com/cgi-bin/wiki.pl?NigelsHushBox](http://popey.com/cgi-bin/wiki.pl?NigelsHushBox) )

any clue??
becouse It works in WinXp... but don't like using the win just for use my tv tuner..

---

### Post by bwhite82 on 2008-05-23
Keep Googling until you find the name of the driver. When you do, issue the command:

> modinfo [insert driver name]

If present, load it with:

> sudo modprobe [insert driver name]

---

### Post by Randall Flagg on 2008-05-23
mmm .. ok, I'll keep looking

waiting any kind of help thou .. ;)

---


---
title: "[SOLVED] Ridiculously large fonts"
date: 2008-03-12
forum: General Help
---

### Post by itix on 2008-03-12
First a little background info on this problem.
I have recently pre ordered an Asus Eee (due to the ridiculous demand, I probably won't get it until early April) and encountered this problem while trying to copy the EeeXubuntu onto my external hard drive for later installation on the Eee. I inserted the EeeXubuntu disc in my Acer Aspire 3610 from which I am now writing this, and when the x-server started I got a strange sense of dé ja vu. Half of the screen was filled with the first 6-7 letters of applications which had a microscopic icon next to it which probably indicated the original font size.

The same thing happens when I insert a live disc of fedora core 8 which I decided to try a while ago when the computer needed reinstallation since i had experimented so much with it (god invented the external hard drive for my sake!). The same thing also happens on the Ubuntu Gutsy Gibbon live disc that I have which is why I always install Ubuntu from my Fiesty Fawn disc and then upgrade.

Does anyone know why the fonts are so ridiculously large on three separate distributions??

---

### Post by kerry_s on 2008-03-12
my guess is the dpi is screwed, it's usually set at 100, i change mine to 75. who needs to waist all that space on fonts.

---

### Post by itix on 2008-03-12
The what??
I have bad eyesight in close range, but I don't have so bad eyesight that I need fonts that cover half the screen.

And would really that "dpi" (dots per inch?) be screwed in all three distros??

---

### Post by unutbu on 2008-03-12
Do you happen to have a file called .Xdefaults in your home directory?
If so, look inside. Some applications' font size can be configured there. If this file was present in each of your linux distros, each OS might have behaved as you described.

Also, if this is the case, you could just define smaller fonts here to maybe fix your problem.
(Remember to run xrdb -merge ~/.Xdefaults to make your choices stick.)

Finally, if this does not help, it might help to post what apps are behaving badly.
(e.g. Nautilus? gnome-terminal? firefox?)

---

### Post by itix on 2008-03-13
There's no real problem with my current hard drive Ubuntu 7.10, but theese were live cd's. I don't really know were I'd check for .xdefaults. I don't have it in my working HD-ubuntu and all the settings on the live CD is kept on the Primary memory (I have tried to install ubuntu on a computer with no hard drive once so I know what I'm talking about :) ).

The applications are basically any application with border text like panels, window bars, etc. The panels and firefox are normal on Fedora Core 8 and Ubuntu 7.10, but the window bars are still massive. On the EeeXubuntu-live cd it's every application. Terminal, firefox, panels, window bars, etc. The font's are also bigger on EeeXubuntu.

---

### Post by kerry_s on 2008-03-13
the ~/.Xdefaults is a file you create to pass settings to X programs. if you never made it, it won't be anywhere.

you would do like this
mousepad ~/.Xdefaults

you would put
Xft.dpi: 75

then save it.

then in a terminal, you run
xrdb -merge ~/.Xdefaults

to activate it. you'll need to put that command in your startup, so it's set at every start.

i keep mine small, here's what it looks like.

---

### Post by itix on 2008-03-13
But how would this affect live-CDs?

---

### Post by kerry_s on 2008-03-13
> **itix said:**
> But how would this affect live-CDs?

dude, it's a bug with your vid card, the fix is adjusting the dpi, it don't matter livecd or installed, it's a hardware issue. just do some googling, it's a common problem.

---

### Post by itix on 2008-03-13
I'm feeling a bit stupid and I'm sorry to bother you any further here but I don't get it. Does this configure the hardware directly? Does this solve my live-CD problem because I have no problem at all with my current installed Ubuntu.

---

### Post by unutbu on 2008-03-13
This page might clarify things:
[http://scanline.ca/dpi/](http://scanline.ca/dpi/)

I don't know why things are working for you now but not from the Live CDs.
To test our understanding of what is going on, you might try the following experiment:

Boot from a Live CD.
Make a .Xdefaults file with the following line in it:

```

Xft.dpi: 100

```

In a terminal run:
```

xrdb -merge ~/.Xdefaults

```

Now run one of those programs with massive fonts. 
It should look okay now.

---

### Post by itix on 2008-03-14
Terminal says:
```
xrdb: no such file or dir...
xrdb: can't open ~/.Xdefaults
```

On both EeeXubuntu and Ubuntu 7.10.

---

### Post by itix on 2008-03-14
Oh, I forgot to mention; this last time I started 7.10 live disc, the huge fonts where everywhere (panels, icons etc) for a couple of seconds and where then restored to the normal size that I'm used to, with only window bars have these huge fonts.

---

### Post by unutbu on 2008-03-14
```

xrdb: no such file or dir...
xrdb: can't open ~/.Xdefaults

```
means that there is no file named .Xdefaults in your home directory.

Try this after booting from a Live CD:
Open up a terminal window. Type
```

echo "Xft.dpi: 100" > ~/.Xdefaults
xrdb -merge ~/.Xdefaults

```

---

### Post by itix on 2008-03-15
Great! It worked, thanx.

---


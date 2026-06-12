---
title: "WTF worthy problem! Graphics drivers??"
date: 2007-11-26
forum: General Help
---

### Post by TV-VCR on 2007-11-26
I don't know what happened, now whenever I try to boot into ubuntu I get this:
[IMG]http://img99.imageshack.us/img99/3925/screwedvu5.jpg[/IMG]

Argh!! What's going on here! :mad:

---

### Post by Craigus on 2007-11-26
Does the graphics hardware work with anything else, like windows or a linux live CD?

If not, it's probably a hardware failure.

Try booting in recovery mode - does that give a readable text screen? You could try renaming or deleting /etc/X11/xorg.conf and see what that does.

---

### Post by JBAlaska on 2007-11-26
Boot into recovery mode as craigus suggested, then type this at the command line;
```
dpkg-reconfigure xserver-xorg
```

Follow the prompts to reconfigure x.

---

### Post by Craigus on 2007-11-26
Further on JBAlaska's post, his is probably the better method, although if you are running Gutsy with Xorg 7.3 (I should have clarified this), X will actually work without an xorg.conf file in so called bullet-proof mode. Older versions can't do this.

---

### Post by TV-VCR on 2007-11-26
I am running Gutsy 7.10.

It is not a hardware failure, as Windows can see and use my 8800GTX just fine.

---

### Post by retrow on 2007-11-26
I had a similar problem when I added 7300GS and got video output from the graphics card. I had to reconnect my vga cable to the built-in vga slot of my machine in order for it to reboot without that garbled screen. You get some complaints before you reach grub saying how its not cool to connect your cable to your CPU's VGA port when you have a kickass video card but you can ignore it. Once you are able to boot in graphical mode, you can install the restricted driver for your video card - infact you'd be prompted to go so as soon as you log in.

Hope it helps.

---


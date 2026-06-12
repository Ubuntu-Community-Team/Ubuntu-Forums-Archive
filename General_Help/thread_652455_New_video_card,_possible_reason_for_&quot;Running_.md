---
title: "New video card, possible reason for &quot;Running local Boot  scripts&quot; hangup?"
date: 2007-12-28
forum: General Help
---

### Post by kelasia on 2007-12-28
I recently bought a nVidia 8600 GT gfx card and put it into my computer, my windows boot runs it just fine, but now whenever i boot into ubuntu (7.10), it goes through the graphical boot, then switches to a textual one, the last line reading "Running local boot scripts......[OK]"

The pc has been through some minor issues before the installation, that required a new power supply, etc. But I don't think that is the issue.

I am able to boot into a live cd, and "download" the drivers for the card just fine, etc. 

My question is how am I to get back to my desktop, or how can I back up all the files in it that I need so that I can reinstall?

Oh, not a newb/n00b to ubuntu, just to the forums.

---

### Post by randavance on 2007-12-28
So I'm thinking that X )the graphical part of the system) is having trouble with the card. Normally you would go into a low graphics mode, but it seems to not even be getting that far. So we'e going to reconfigure the xorg.conf file.

Try the following.

ctrl+alt+f1

 this will put you into a different command line

log in with your user name and password

type the following

```
sudo dpkg-reconfigue xserver-xorg
```

type your password

I think you should be able to handle it from here, just put in the information about your card, monitor, etc. Most of the time just hit OK.

The one you should pay attention to us when you have a list of types of cards, choose the one that says "NV'.

Hopefully this will help.

Edit: Also, when your done, just restart your computer. And if you can get up any desktop install the proprietary driver from the installer in your system menu.

---

### Post by kelasia on 2007-12-28
Alright, thank you! Everything boots beautifully, my only concern is that everything seems to lag a little bit.

---


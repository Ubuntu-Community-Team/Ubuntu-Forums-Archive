---
title: "wtf is going on? (edgy wireless)"
date: 2006-10-27
forum: General Help
---

### Post by Wallakoala on 2006-10-27
I just upgraded from dapper to edgy. My wireless card, which worked in dapper, does not appear to be working in edgy. So now I can't use the internet. Great. 

Is there any way I can fix this, or do I have to wait until the ubuntu team fixes it? If it isn't fixed soon, i'll have to wipe ubuntu and reinstall dapper, which I really don't want to do.

I noticed other people have similar problems, why wasn't edgy delayed? I think an upgrade should *fix* things, not make them worse than before.

And btw my wireless card is a netgear something. I would have to crack open my computer to give you the exact model number, and i really don't feel like doing that.

---

### Post by llamakc on 2006-10-27
Or you could post the output of lspci -v or lshw

But yeah, wireless is a pain now. I gave up using a Broadcom card and ran cat5 to my box.

Have you checked the bug reports for your specific card?

---

### Post by black_rob on 2006-10-27
First thing check if Edgy detected your card at all.  First try lspci, and look for your card.  Another thing I often do when hardware isn't working is "dmesg | less", then scroll through, looking to see if it found my card or not.

It may be that under Dapper you were using a driver that isn't in the base install.  Personally, I was pretty happy that Edgy did automatically find my wireless card, because it's the first distro I've tried that has.

---

### Post by Wallakoala on 2006-10-28
according to lspci -v, my card is the following:

```
Intersil corporation prism 2.5 wavelan chipset (rev o1)

Subsystem: Netgear MA311 802-11b wireless adapter
```

I really really need to get wireless working. Does anybody have any ideas?

---

### Post by black_rob on 2006-10-28
Try "lsmod" to see what modules are installed.  I don't remember what the module name is for that card, I think it might be prism54 or hermes.

If you don't see either, try "modprobe prism54", "modprobe hermes", whichever it is.  Can't hurt to try them both.  

Hopefully, your modules just wasn't getting loaded automatically.  If loading it this way works, then your wireless card should now show up if you do "iwconfig wlan0" (probably wlan0).  Once it's there, you can start it manually or with Ubuntu's graphical tool (sorry if I'm a little sketchy about names of things, I'm at a slackware machine right now, so I can't check.)

---


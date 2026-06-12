---
title: "Firefox monopolizes the hard drive, locks up the computer Merge Posts"
date: 2018-12-29
forum: General Help
---

### Post by peyre on 2018-12-29
Since upgrading to Xubuntu 18.10, Firefox has become unreliable.  Periodically it'll monopolize the hard drive.  The computer starts to respond jumpily to the mouse, music starts cutting, etc.  I look down and the hard drive light is flashing heavily.  Pretty soon it stops responding altogether.  Sometimes I'm able to clear things up if I close Firefox quickly enough, but more often it's stopped up the system before I can get FF to respond to an Alt-F4 or clicking on the close button in the top right.

It's happening erratically.  Most of this past week I haven't had much trouble, but this morning I've been on for like an hour and a half and already had to push the reset button three times.

I went into Synaptic and did a **Complete Removal** of Firefox, then reinstalled.  That doesn't seem to have helped.

This computer isn't new (it's from ca. 2009) but still, it shouldn't be doing this.  I'm running Xubuntu 64-bit on a 256GB SSD with a big mechanical drive for storage, and 4GB of RAM.  This is, of course, Firefox Quantum, and maybe that's the problem.

Ok, **four** times now.  I closed all my tabs but this one so I could post before my computer locked up, then I opened another to check my Yahoo! mail.  I sent a reply to a message, and Firefox locked up my HD again.  What gives??

---

### Post by dragonfly41 on 2018-12-29
For comparison you can try [Pale Moon]("https://www.palemoon.org/") which is a fork.
It is in the Software Centre to be installed.

---

### Post by peyre on 2018-12-29
Thanks, I might try that.  I do use Chromium as my backup/secondary browser, but I'm much fonder of Firefox.

Does Pale Moon support the add-ons for Firefox?

---

### Post by dragonfly41 on 2018-12-29
I don't use it too often .. only when I have experienced crashes elsewhere.

Search here ... [http://www.palemoon.org/faq.shtml](http://www.palemoon.org/faq.shtml)

> [COLOR=#000000][FONT=Museo500Regular]Pale Moon is forked from Firefox, and there are some significant differences between the two browsers. As such, Pale Moon has its own (exclusive) extensions that were specifically written for it, which should always work. In addition, Pale Moon also allows Firefox extensions to be installed, as long as these extensions are compatible with version 24 of Firefox (since that is the closest matching version from an add-on perspective). These Firefox extensions are not guaranteed to work, but in most cases can be made compatible with a few small alterations. This incompatibility can be caused by several different things, the most important:[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2018-12-29
You could try limiting the number of content processes (Preferences->(page) General -> (section, close to the bottom of the page) Performance->Content process limit). Lowering this from the default of 4 to 2 has made browsing less horrible for me on a similar machine.

Holger

---

### Post by CatKiller on 2018-12-29
> **peyre said:**
> I went into Synaptic and did a **Complete Removal** of Firefox, then reinstalled.  That doesn't seem to have helped.

It's quite frustrating that ex-Windows users think that will do anything helpful. It won't.

Your problem is nothing to do with the hard drive. You're running out of RAM, so it's hitting the swap, which is slow. It sounds like a memory leak.

Renaming your .mozilla directory to something else, so that you're starting with a fresh profile, is probably a good starting point. Then you can start to narrow down whether your issue is caused by the browser itself or an add-on or extension that you've installed.

---

### Post by peyre on 2018-12-29
> **CatKiller said:**
> It's quite frustrating that ex-Windows users think that will do anything helpful. It won't.
I mentioned that to avoid being asked if I'd tried removing and reinstalling.  Sure I'm a former Windows user, but I'm not a total noob.

I have had programs start to behave themselves again after removing and reinstalling.

> **Holger_Gehrke said:**
> You could try limiting the number of content processes (Preferences->(page) General -> (section, close to the bottom of the page) Performance->Content process limit). Lowering this from the default of 4 to 2 has made browsing less horrible for me on a similar machine.
OK, I've set that.  We'll see what that does.

> **Holger_Gehrke said:**
> You could try limiting the number of content processes (Preferences->(page) General -> (section, close to the bottom of the page) Performance->Content process limit). Lowering this from the default of 4 to 2 has made browsing less horrible for me on a similar machine.
*Five* times now this morning.

That was a good suggestion Holger.  Looks like it didn't work for me, but was worth trying.

---

### Post by raul-mccai on 2018-12-29
My work around has been to close Firefox and start over.

---

### Post by peyre on 2018-12-29
Sure, that's worked a few times. Usually though it stops reponding before I'm able to close it.

Two more times after I came back to the computer less than an hour ago.  Firefox just isn't usable on this machine any more.  %$#! this; I'm switching over to Pale Moon.

---

### Post by Yellow Pasque on 2018-12-30
> **CatKiller said:**
> It's quite frustrating that ex-Windows users think that will do anything helpful. It won't.

Well, if you've been modifying system-wide config files (in /etc) or you've been doing bad n00b practices (messing with stuff in /usr directly), then purging/reinstalling the package might do something helpful.

> Your problem is nothing to do with the hard drive. You're running out of RAM, so it's hitting the swap, which is slow. It sounds like a memory leak.

That's possible, but I wouldn't conclude it. Sometimes, I experience similar behavior OP describes if I leave a tab open a long time. This is on an older system with only 2GB RAM (running Debian and xfce). I initially thought it was thrashing, but 'free' command showed 0.5GB RAM available and hardly any swap used. I can usually recover just by closing Firefox, so it's annoying, but not enough for me to spend a lot of time/energy digging into it. The OP seems to have more problems getting back to a usable system than I do.

> Renaming your .mozilla directory to something else, so that you're starting with a fresh profile, is probably a good starting point. Then you can start to narrow down whether your issue is caused by the browser itself or an add-on or extension that you've installed.

Before modifying profiles, I would see if I could reproduce the behavior when starting in safe mode:
```
firefox -safe-mode
```

---


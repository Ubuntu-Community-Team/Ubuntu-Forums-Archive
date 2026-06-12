---
title: "Nixnote doesn't connect with Evernote"
date: 2014-10-29
forum: General Help
---

### Post by Gordonbp531 on 2014-10-29
I have an Eee PC Netbook with Ubuntu 14.04 (x86) installed as a fresh install, all patched up to date.
Nixnote 1.4, 1.5 and 1.6 install correctly - obviously not all at the same time! (I can't see any i386 versions after those) and open correctly, but the option Tools>Synchronise with Evernote is greyed out, and when I click on "Synchronise" in the toolbar or on Tools>Connect the "Please grant Nixnote Access" dialog box appears, then disappears and the following error message shows at the bottom left hand corner of the window:
"OAuth error retrieving temporary token"

The 64 bit version of Nixnote works perfectly OK on my laptop with 64 bit Ubuntu installed - has anyone come across this, and if so is there a fix?
(I've raised a ticket on the SourceForge web page - but there doesn't seem to be much activity from the developers there at all...)

Cheers

Gordon

---

### Post by rbmorse on 2014-10-29
I've given up on Nixnote in favor of using the Web interface to the Evernote portal via Chrome or Firefox when I'm on a Linux machine. It Just works.  Of course, this presupposes a reliable and reasonable fast network connection, although I've had no real problem using the Evernote apps on the iPad or iPhone via a cellular connection, either.

---

### Post by tgalati4 on 2014-10-30
You probably have to build your own 32-bit version, as the developer doesn't appear to build it anymore.  The folks at Evernote have repeatly said they don't plan to support linux.  And because we don't have a native, linux Evernote client, we have no way to save our Evernote notes locally in linux.  Nixnote will save locally, (which is a premium feature of Evernote), but Nixnote doesn't support all of Evernote's features and is subject to breakage anytime Evernote wants to change their API's.

The web client works reasonably well, and has most of the features of the native Windows client, so that is the work-around at the moment.

---

### Post by maier.m on 2014-11-02
I'm experiencing the same on Ubuntu 14.10 64-bit... Gordon, could you share the link of your ticket so I can follow up on that?

---

### Post by gijsbo2000 on 2015-03-10
> **Gordonbp531 said:**
> I have an Eee PC Netbook with Ubuntu 14.04 (x86) installed as a fresh install, all patched up to date.
Nixnote 1.4, 1.5 and 1.6 install correctly - obviously not all at the same time! (I can't see any i386 versions after those) and open correctly, but the option Tools>Synchronise with Evernote is greyed out, and when I click on "Synchronise" in the toolbar or on Tools>Connect the "Please grant Nixnote Access" dialog box appears, then disappears and the following error message shows at the bottom left hand corner of the window:
"OAuth error retrieving temporary token"

The 64 bit version of Nixnote works perfectly OK on my laptop with 64 bit Ubuntu installed - has anyone come across this, and if so is there a fix?
(I've raised a ticket on the SourceForge web page - but there doesn't seem to be much activity from the developers there at all...)

Cheers

Gordon

I have just installed NixNote 2-0 Beta 2 on my, admittedly, Kubuntu 14.04 LTS. It seems to connect, sync and work. I got it here: [http://sourceforge.net/projects/nevernote/files/NixNote2%20-%20Beta%201/](http://sourceforge.net/projects/nevernote/files/NixNote2%20-%20Beta%201/)

---


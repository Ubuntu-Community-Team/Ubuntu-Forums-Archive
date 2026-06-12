---
title: "Inspiron 1521 driver trouble"
date: 2008-05-05
forum: General Help
---

### Post by HelpIsNice on 2008-05-05
Ok I got a Inaspiron 1521 dual booting vista and ubuntu and I was wondering if the driver commands and stuff that are listed for ubuntu 7.10 would work for 8.04?If so then how would I get them on my computer without internet?Please help thank you.

---

### Post by HelpIsNice on 2008-05-05
> **HelpIsNice said:**
> Ok I got a Inaspiron 1521 dual booting vista and ubuntu and I was wondering if the driver commands and stuff that are listed for ubuntu 7.10 would work for 8.04?If so then how would I get them on my computer without internet?Please help thank you.

BTW I need the wireles to work on my laptop or I have no other way to get internet thank you and please post.

---

### Post by Sef on 2008-05-05
What are your system specs?

---

### Post by HelpIsNice on 2008-05-05
> **Sef said:**
> What are your system specs?

Hardware: AMD 64x2 2.2ghz, ATI Radeon Xpress 1270 video, integrated sound (ATI SBx00 which shows as HDA-Intel using STAC 9205 chipset), built-in Omnivision webcam 2gig RAM, 160gig SATA HD 8X DVD+/-RW DL, Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


just put the ubuntu 8.04 32 bit on the the other day and gave it 80 gigs of space, but i havent changed anything

---

### Post by HelpIsNice on 2008-05-05
oh its a dell by the way

---

### Post by HelpIsNice on 2008-05-06
help please, I would really like to get this setup

---

### Post by hogman500 on 2008-05-11
i have the same problem

---

### Post by OMRebel on 2008-05-11
On my 1501 I had to use NDISWrapper to install the Windows driver, because the driver that came with Ubuntu just wouldn't work.  I'd recommend going that route.

Here's the how-to that I used.  Just make sure that the broadcom wireless in your laptop is the same chipset as that in the 1501.  If so, then this should work:
[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html)

---

### Post by CheshireMac on 2008-05-22
I'm in the same boat, same specs, except that my card is a BCM4401 . . . I've downloaded the XP driver, but I'm wary about using Ndiswrapper because I've never needed it before now . . . this is a friend's machine, and I don't want to make a ton of redundant changes.
Any thoughts? Do I need Ndiswrapper? Should I try FWCutter?

---


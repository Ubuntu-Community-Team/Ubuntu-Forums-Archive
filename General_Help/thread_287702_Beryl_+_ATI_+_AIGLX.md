---
title: "Beryl + ATI + AIGLX"
date: 2006-10-29
forum: General Help
---

### Post by darrenm on 2006-10-29
Hey guys,

I used to run Compiz with XGL on my binary ATi FGLRX driver in dapper.

Now in Edgy I want to run native X with compositing (AIGLX) with Beryl but I can't seem to get XGL to work anymore which isnt too much of a problem because it always seemed like more of a hack than a proper solution.

Now it seems ATi are never going to release a binary driver that supports compositing with DRI I've had to make the jump and change to the Xorg radeon driver.

My VGA card is a 9600XT RV350 AGP on an Intel i865 board.

With the following options its works fine with Beryl and X
```
Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "XAA"
        Option "XAANoOffscreenPixmaps"
        Option "GARTSize" "64"
#       Option "RenderAccel" "true"
#       Option "AGPMode" "2"
#       Option "AGPFastWrite" "on"
        EndSection

```
If I enable any of the hashed out sections it locks my computer solid when starting X

My only remaining problem is overlay - When I open a video it plays fine until I do something like rotate the cube and the video disappears until I drop the cube again.

Same if I make the window semi-transparent, the video disappears until I make it 100% non-opaque. I assume I'm not using Xv or something.

Any ideas?

I'm waiting to make a vidcap of a lovely working GLX+Beryl system to show my friends just how good modern Linux is ;)

---

### Post by darrenm on 2006-10-29
Bump :)

---

### Post by idlewild on 2006-10-29
Sadly we're still waiting for ati to udpate their drivers to support aiglx. There's no ETA on this so xgl is the only way you're going to get compiz/beryl to work.
Sadly xgl does not seem to be getting worked on as much as aiglx, which is a shame since I think xgl is the correct development path to take.

Personally I don't have much faith in ATI delivering the drivers at any point in the near future. In fact I'm tempted to swap out my ATI card for a Nvidia one.

---

### Post by darrenm on 2006-10-29
> **idlewild said:**
> Sadly we're still waiting for ati to udpate their drivers to support aiglx. There's no ETA on this so xgl is the only way you're going to get compiz/beryl to work.
Sadly xgl does not seem to be getting worked on as much as aiglx, which is a shame since I think xgl is the correct development path to take.

Personally I don't have much faith in ATI delivering the drivers at any point in the near future. In fact I'm tempted to swap out my ATI card for a Nvidia one.

Same here. Like really tempted. Now the future of converting people to Linux is firmly rooted in eye candy ATi are going to get a worse and worse rep for this. I would email them and tell them if they would actually reply.

---

### Post by CarpKing on 2006-10-29
> **idlewild said:**
> Sadly we're still waiting for ati to udpate their drivers to support aiglx. There's no ETA on this so xgl is the only way you're going to get compiz/beryl to work.
Sadly xgl does not seem to be getting worked on as much as aiglx, which is a shame since I think xgl is the correct development path to take.

I'm interested to here why you think XGL is the the proper path.  Every other discussion I've seen seems to consider XGL to be a temporary workaround until drivers support AIGLX, which more and more seem to be doing.  If I could ever get visible output to my monitor with the open source drivers, I would try Beryl with Edgy's built-in AIGLX myself.

---

### Post by darrenm on 2006-10-29
Have you tried using the radeon driver with no options in there? I gave up on it a few times but it does seem to be working nicely here now with my posted xorg.conf ^

---

### Post by Fyda on 2006-10-30
Like the OP, I wish to try running Compiz (or Beryl) on AIGLX rather than XGL, with an ATI card (I have a Radeon 9550 GE).

I've already tried at least 5 times before now, using various tutorials for AIGLX... they've all failed spectacularly and left me a nice mess to clean up with *sudo vim /etc/X11/xorg.conf* (or *sudo cp ~/xorg.conf.bak /etc/X11/xorg.conf* when I was finally exhausted for the day).

Anyway, the whole reason I want to use AIGLX over XGL is for the supposed speed advantage (**anyone want to correct me on this?**), and because it seems better to use the integrated approach (AIGLX), rather than some hackish nested affair (XGL). Or am I wrong? I'm only going on what I've read; I might've misunderstood.

Oh, and it helps plenty that AIGLX is in Edgy. ;)

On a different note, d'you suppose it'd make any difference if people swapped their ATi cards for NVidia ones and wrote letters to ATi to explain their reasons for doing so? Or would this sort of passive activism (if such a thing exists) make no impact whatsoever?

In any case, I really hope what the original poster asked for is made possible soon... not everyone can afford to get a brand-new card just for this. :(

---

### Post by darrenm on 2006-10-31
AIGLX does seem far better than XGL, mainly because you can still use DRI. Also other little problems I had with XGL because of it being an add-on such as poor capturing in Kino have been solved by AIGLX (AKA Xorg7.1 compositing) so to me it does seem a far better solution.

Now AMD have taken over ATi there has been word of AMD open-sourcing the whole thing, which if true would be fantastic.

At the moment ATi have a really bad name with the Linux community, they obviously aren't worried about this otherwise I would expect to get at least one reply to the emails I've sent them.

---

### Post by idlewild on 2006-11-01
> **CarpKing said:**
> I'm interested to here why you think XGL is the the proper path.  Every other discussion I've seen seems to consider XGL to be a temporary workaround until drivers support AIGLX, which more and more seem to be doing.  If I could ever get visible output to my monitor with the open source drivers, I would try Beryl with Edgy's built-in AIGLX myself.

If I go into it too deeply I would most likely be poorly regurgitating other people words. Theres lots of interesting arguments on various blogs about aiglx vs xgl. The argument is basically aiglx builds on the original X server and keeps years of well developed code. Where as Xgl is the first step is a development line which will eventually aims to replace the xserver with something altogether slimmer and faster (egl).

The xorg code base is horribly complex and I think the maintainers have a really hard time trying to introduce new developers. Now, with the new desktop 'revolution' happening, to me it seems like it's the right time to drop the old code base and move to something which will be much easier to maintain for the next decade.

I'd advise you look at some of the real discussions about it. It's a very interesting topic and imo a very important decision (for desktop linux).

---


---
title: "It wont start up, Please help me =("
date: 2006-09-10
forum: General Help
---

### Post by Thanatios on 2006-09-10
Let me explain the whole story.

I have tried to install Ubuntu on my moms PC, but whenever I started up the Live CD. It woulnt start. I just got a black screen, with a line ( _ ) above it in white. 
When I tried to start it up in safe gfxs mode, I had a error, saying: Could Not Load x Server.

So yeah, I downloaded the alternative CD, as a friend suggested.

I have installed Ubuntu on my moms PC (Using that alternative CD) ( Specs: Pentium 3 512, MHZ PC, 512 MB RAM, GeForce 4 Videocard). And everything whas going good. Until the instalation whas done.
When I try to start it up now, I get the same as I had with my live CD. I just get a black screen, with a white line above ( _ ). And nothing happens.

Can someone please help me? =( I have no idea what to do. Ive searched the Forum, but nothing really helped.

Thank you in advanced.

---

### Post by Qrk on 2006-09-10
Try this:

Press <ctrl><alt><f1>
log in with your name/password that you made during installation
type in the command:

```
sudo dpkg-reconfigure xserver-xorg
```

Attempt to autoconfigure video hardware? Yes
Choose the "vesa" driver in the next screen.

Go through the rest, most stuff should already be set up for you. 

Once you have a gui, go to this site 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
to get a faster driver for your card.

Now go to the terminal (under apps-> accessories) and again type

```
sudo dpkg-reconfigure xserver-xorg
```

and select "nvidia" from the second screen.

Restart X with <ctrl><alt><backspace>

---

### Post by Thanatios on 2006-09-10
Thanks for your fast reply!

But, wenever I start up Ubuntu now, I get a white/blue error screen. With something like: X server failed to start.

So I looked at the log, but I didnt know exacly what to show here.
So I copy'd this:

```
(WW)VESA: No Matching device section for intance (BusID PCI :1:11:0) found
(EE)Vesa(0): Cannot read V.BIOS
Screen(s) found but none have a useable configuration.

Fatal error
No screens found.
```

Also, might I add. That my mom has 2 videocards. One onboard, and one is an nVidia videocard.

I myself have no idea what to do. Can someone help me out please?

---


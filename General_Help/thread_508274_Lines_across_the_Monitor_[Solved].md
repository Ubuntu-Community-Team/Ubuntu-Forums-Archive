---
title: "Lines across the Monitor [Solved]"
date: 2007-07-24
forum: General Help
---

### Post by Sef on 2007-07-24
I got lines across my monitor all the sudden.   I was just chatting and then these lines came up.   Also the sound comes up muted.    What is the problem?


Nvidea card, P3, 512 ram

---

### Post by huzzak on 2007-07-24
Are your speakers integrated into your monitor?  It may be a case of hardware failure.  Have you tried rebooting to see if the issue resolves itself?

---

### Post by Sef on 2007-07-24
> Are your speakers integrated into your monitor? It may be a case of hardware failure. Have you tried rebooting to see if the issue resolves itself?

Speakers not intergrated.   Rebooting does not help.

---

### Post by TigerWolf on 2007-07-24
Could it possibly a resolution or refresh rate that the monitor cannot handle - have you tried different combinations of this to rule this out?

---

### Post by Crafty Kisses on 2007-07-24
> **Sef said:**
> Speakers not intergrated.   Rebooting does not help.

You might want to try posting the following output:
```
lspci
```

---

### Post by Sef on 2007-07-24
> Could it possibly a resolution or refresh rate that the monitor cannot handle - have you tried different combinations of this to rule this out?

Still set for the correct resolution.

> You might want to try posting the following output:
Code:

lspci




Here it is:

```
sef@jokat1:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
sef@jokat1:~$ 

```

---

### Post by Sef on 2007-07-25
bump.  any ideas?

---

### Post by Crafty Kisses on 2007-07-25
> **Sef said:**
> bump.  any ideas?

This also might sound crazy, but if you have a fan next to your computer it can be causing this, I remember I had a fan next to my computer it was causing lines on my screen, can you post a screenshot? I've had a similar problem.

---

### Post by Sef on 2007-07-26
> This also might sound crazy, but if you have a fan next to your computer it can be causing this, I remember I had a fan next to my computer it was causing lines on my screen, can you post a screenshot? I've had a similar problem.

No fan near the puter.    Here's a pic.

---

### Post by Wim Sturkenboom on 2007-07-26
Picture looks fine to me.

---

### Post by Sef on 2007-07-27
> Picture looks fine to me.

Look at where there is writing.   There are lines going across that should not be there.  (Here's a second pic.)

---

### Post by Wim Sturkenboom on 2007-07-27
It's probably me, but I don't see what you mean. Either you have very good eyes or mine are going down th drain.

---

### Post by Soybean on 2007-07-27
Both of your screenshots look perfect on my computer. This means that the problem is likely with your monitor. You should try tightening the connections... if that doesn't help, try plugging the monitor into a different computer, if you have one available.

But given that your sound got screwed up at the same time, there's a decent chance it was a power surge or something, and the damage may be physical. :(

---

### Post by Sef on 2007-07-27
Thank you.   The lines just popped up.    The sound had been giving me a bit of a hard time lately, but always could get it to work before.

---

### Post by Sef on 2007-08-17
> But given that your sound got screwed up at the same time, there's a decent chance it was a power surge or something, and the damage may be physical.

The fan on the video card went bad, and some sound settings were changed in the BIOS.    With another video card and some changes in the BIOS, all is well.

Thanks all who helped me figure this out.

---


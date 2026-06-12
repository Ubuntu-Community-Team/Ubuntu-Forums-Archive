---
title: "[SOLVED] 32 or 64 bit on Intel Core 2 Duo?"
date: 2008-06-08
forum: General Help
---

### Post by Norrad on 2008-06-08
I finally got my new notebook today and I am ready to install Ubuntu, but I am wondering which version to choose. It's an Intel Core 2 Duo based IBM Thinkpad, should I install the 64 bit version? Anything I should know?

---

### Post by jrusso2 on 2008-06-08
If your using less then 4 gigs of ram which I am pretty sure you are with a Thinkpad I would use the 32 bit Ubuntu.

The 64 bit version doesn't offer much in the way of performance increase unless your over 4 gigs of ram, and its more difficult to setup and get all your hardware working.  And not all applications will run on it.

---

### Post by forger on 2008-06-08
You could try both, but if you're a beginner to ubuntu and generally gnu/linux, i suggest sticking to i386 (32-bit), you'll have less problems with say java and flash.

---

### Post by fenian on 2008-06-08
I would stick with 32 bit version.Getting some things (Flash for example) to work in 64 can be a bit of a hassle.However 64 bit programs for encoding audio/video and 3d rendering do have significant speed improvements compared to 32 bit so if you encode a lot of video or do a lt of 3d rendering you may want 64 bit.

---

### Post by stchman on 2008-06-08
> **Norrad said:**
> I finally got my new notebook today and I am ready to install Ubuntu, but I am wondering which version to choose. It's an Intel Core 2 Duo based IBM Thinkpad, should I install the 64 bit version? Anything I should know?

The only things I have found that have problems with 64 bit is Java and gDesklets.

You can use Icedtea for Java.  i have 64 bit running very well on an Athlon 64 I have.

Flash runs fine in Ubuntu.

---

### Post by cotcot on 2008-06-08
Do a dual boot 32 and 64. 32 as default. 64 to check.
I have no problems with my 64 bit.

---

### Post by heatblazer on 2008-06-08
You must have over 4G of RAM unless you do, it`s pointless.

---

### Post by Norrad on 2008-06-08
Thanks guys, I'm going to go with the 32 bit version. I only have 2 gigs of RAM and the ThinkPad maxes out at 4 gigs, so no need to address more.

---

### Post by Sef on 2008-06-08
> You must have over 4G of RAM unless you do, it`s pointless.

Not quite correct.  I have found that for downloading pictures, it is much faster.  I have about 3000 files with about 2000 pics and it took me about 30-40 minutes to download them to my usb on 32-bit; it takes 4 minutes on 64-bit.  Also some graphics are sharper.  

Flash is easy to install with Kliz's script.

OpenJDK is easy to install with Add/Remove.  For more information on it, click on my link 'Java on 64-Bit'.

I have only 2 GB ram.

---

### Post by oldos2er on 2008-06-08
> **heatblazer said:**
> You must have over 4G of RAM unless you do, it`s pointless.

 Not at all. I have a Core 2 Duo with 2G RAM. Occasionally I run Devede, which runs faster with 64-bit than it did with 32-bit.

 I've read several posts where people claim 64-bit Ubuntu is more problematic than 32-bit in ways they never specify. I've had no problems running Flash, Java, or anything else under 64-bit Ubuntu--of course doing some research on these things beforehand helps.

---

### Post by stchman on 2008-06-08
> **heatblazer said:**
> You must have over 4G of RAM unless you do, it`s pointless.

Not pointless.  64 bit apps run about 20% faster.  I will agree that until COMPLETE compatibility can be achieved the hassle is probably not worth it.

---

### Post by lklk on 2008-06-09
I switched to 64 bit when 8.04 came out. I had no problems installing flash and java. All I did was install the restricted packages through Synaptic. I only had a few problems with not finding 64 bit versions of apps. One was Koctave the other Real Media Player. Real did install and works fine but the Firefox plug-in doesn't work. I have a Thinkpad with 1 GiB RAM.

---


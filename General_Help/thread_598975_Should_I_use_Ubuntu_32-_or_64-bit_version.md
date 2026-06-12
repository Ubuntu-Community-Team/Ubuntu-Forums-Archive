---
title: "Should I use Ubuntu 32- or 64-bit version?"
date: 2007-10-31
forum: General Help
---

### Post by Uboontu on 2007-10-31
My CPU is AMD Athlon 64 X2 4800+. Should I install Ubuntu 7.10 32- or 64-bit version? I remember that back when 64-bit cpu's were first released, some people didn't install 64-bit Windows right away due to concerns about incompatibility issues. Will such problems occur for 64-bit Ubuntu?

---

### Post by p_quarles on 2007-10-31
> **Uboontu said:**
> My CPU is AMD Athlon 64 X2 4800+. Should I install Ubuntu 7.10 32- or 64-bit version? I remember that back when 64-bit cpu's were first released, some people didn't install 64-bit Windows right away due to concerns about incompatibility issues. Will such problems occur for 64-bit Ubuntu?
The latest version of Ubuntu (7.10) is a pretty big step forward in terms of 64-bit support. There are some pros and cons to the x86-64 version, though:

Pros:
-Processor intensive tasks (ripping & encoding music, rendering images, compiling source code) is going to get a noticable boost from using the full processor width
-You won't be wasting your CPU's resources
-You can make use of more than 4 gigs of memory
-You can legitimately complain when apps are not offered for the 64 bit architecture

Cons:
-It requires some workarounds to get some things working (i.e., Sun Java, DVD playback)
-There are some closed source Linux apps which don't have 64-bit support (Skype is the big one that I know of)
-There are some open source apps which you might have to compile yourself. 

So, basically, if you're planning on running a lot of RAM, and/or doing a lot of processor intensive stuff, go with 64-bit. If you're looking for the path of least resistance, go with 32 bits. 

(I'm typing this from a 64-bit Ubuntu 7.10 system, btw).

---


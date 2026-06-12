---
title: "Thinking about Ubuntu Studio"
date: 2007-06-29
forum: General Help
---

### Post by Sweet Mercury on 2007-06-29
I'm looking at having to reinstall Ubuntu do to what seems to be some serious breakage, no big deal.

I'm interested in Ubuntu Studio, being a musician and artist.

I've read that US uses a specially modified "low-latency" kernel which dedicates 95% of system resources to whichever application you're currently working on. Good for audio work and the like, but not as good for general day to day use.

My questions: I need to do some ndiswrapper work for my wireless to function, I can do that in US the same way I do in normal Ubuntu?

Can I install a second, "normal" Ubuntu Kernel, and boot up with that for day to day use and the "Studio" kernel for audio work?

If not, can I get the programming suites that US comes with and install them on regular Ubuntu or Xubuntu after I reinstall?

Thanks.

---

### Post by NeoLithium on 2007-06-29
Well, there is a list on the Ubuntu Studio webpage that you cand find, which has their applications; or very easily just add their repositotries and install ubuntustudio-desktop as well.  The lowlatency kernel, depending on your day to day stuff, wasn't terrible for the day to day things that I had used it for, so that might just be something to take a shot in the dark with.

Basically when you download Ubuntustudio, you get Ubuntu 7.04 with the studio metapackage- themes, programs and the custom kernel.  Of course, you can easily install a custom kernel as well, and just switch as you like with the grub list.

---

### Post by Sweet Mercury on 2007-06-29
> **NeoLithium said:**
> Well, there is a list on the Ubuntu Studio webpage that you cand find, which has their applications; or very easily just add their repositotries and install ubuntustudio-desktop as well.  The lowlatency kernel, depending on your day to day stuff, wasn't terrible for the day to day things that I had used it for, so that might just be something to take a shot in the dark with.

Basically when you download Ubuntustudio, you get Ubuntu 7.04 with the studio metapackage- themes, programs and the custom kernel.  Of course, you can easily install a custom kernel as well, and just switch as you like with the grub list.

Alright, seems simple enough. I know that GRUB allows me to pick my kernel at boot up, I didn't realize the other differences were so easy to change as well.

If I install US, I can find the generic kernel in the ubuntu repository?

---

### Post by Sweet Mercury on 2007-07-01
Here's another question:

I'm also interested in playing with fresh XFCE/Xubuntu Install.

Can I install Xubuntu, then get the low-latency kernel, and have that work with Xubuntu?

---


---
title: "Repository  for Linux Images within 6.10"
date: 2006-11-21
forum: General Help
---

### Post by terces on 2006-11-21
I installed 6.10 today - fresh installation.

Beforehand I had been running the K7 version of 2.6.16-24 or something close to that.

Any reason why I can't find any k7 variants in Synaptic anymore compared to literally tons before??  I used to have about 50 different (not all k7) images to pick from and now I have about 10.  

I did edit sources.list and added almost 20 different repositories.

I do see that 2.6.17-10.33-k7 was superseded by linux-image-generic and when I do uname -a it does show i686 GNU/Linux, but I'd like to have options.

Any ideas?

---

### Post by David Corrales on 2006-11-21
They unified the 686 and K7 kernel lines and their variants into generic. It's a lot easier to manage kernels now since there's 3 options: 386, generic and server.

---

### Post by terces on 2006-11-21
Gotcha, very nice!

That makes me happy.  So how does the auto detection work?  I'm using an x86 version of 6.10 on an AMD64 processor and it selected i686... kinda would have thought it would have picked k7.

Thanks for the fast response!

---

### Post by David Corrales on 2006-11-21
Well, generic is compiled for both architectures. If you're using generic, you're already using the best possible prebuilt kernel available for desktops.
Autodetection happens on the livecd I suppose while installing. The cool thing is that in Dapper, after install, you ended with a 386 by default. With Edgy you get generic right away.

---


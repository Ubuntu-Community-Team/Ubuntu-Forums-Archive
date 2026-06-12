---
title: "2.6.8 kernel source"
date: 2004-11-10
forum: General Help
---

### Post by ashley_v on 2004-11-10
I need the kernel source for 2.6.8 i386 kernel for vmware but I did not see it in synaptic.  I also looked for it with:

apt-cache search kernel-source

and it did not show up.  Is it missing from the apt repository or did I overlook something.

Thanks

---

### Post by HungSquirrel on 2004-11-10
I see the source for 2.6.7 but not 2.6.8.  Odd.

Are you sure you need the whole kernel source?  You might just need the headers.

---

### Post by fng on 2004-11-11
you can download the vanilla kernel source @ [www.kernel.org](www.kernel.org)
maybe try: apt-get source linux-386

---

### Post by ashley_v on 2004-11-11
I could not find headers for that kernel either.  Vmware is not that important now since I'm running qemu it's faster and I like it.

I'll probably just grab the 2.6.9 kernel from kernel.org, compile it and see how it runs.

Thanks anyway

---

### Post by anklator on 2004-11-11
what packages do i need to compile the kernel in ubuntu? same as in deb?

---


---
title: "Virtualbox Security"
date: 2008-05-13
forum: General Help
---

### Post by lakelovers on 2008-05-13
I installed Virtualbox, yesterday, for the purpose of validating a web site that I manage. I have been wondering if having the "real" Windows on my 100% Ubuntu box compromises Linux security? I was using "Ies 4 Linux" but for some reason it stopped working but today it is. Anyway, is either Virtualbox or Ies-4-Linux more secure than the other?

---

### Post by inportb on 2008-05-13
Virtualbox should be more secure than Wine. And both are more secure than Windows-on-hardware.

---

### Post by lakelovers on 2008-05-13
Thanks, inportb. . . that makes me feel better.

---

### Post by Monicker on 2008-05-13
> **lakelovers said:**
> I installed Virtualbox, yesterday, for the purpose of validating a web site that I manage. I have been wondering if having the "real" Windows on my 100% Ubuntu box compromises Linux security? I was using "Ies 4 Linux" but for some reason it stopped working but today it is. Anyway, is either Virtualbox or Ies-4-Linux more secure than the other?

A Windows virtual machine can still be get infected with Windows malware.  Files in shared folders could be affected but outside of that there would no consequences for your linux operating system.

On thing to keep in mind.  Many windows worms and bots are you used to participate in sending spam and taking part in DDoS attacks against other people.  So your vm could be used to attack others in that regard if it gets infected with those types of malware.

---


---
title: "Ubuntu minimal vs Debian minimal"
date: 2008-01-15
forum: General Help
---

### Post by Elvish Legion on 2008-01-15
Is there a difference between the barebones ubuntu and the barebones debian? It seems to me you'd basically do the same thing but use different repos

---

### Post by Nano Geek on 2008-01-15
There's some difference, but unless you needed a specific feature either one should work about the same way.

---

### Post by p_quarles on 2008-01-15
The essential difference is that Debian is a rolling release, where Ubuntu ties itself to the six month Gnome release cycle. The Stable (Etch) version of Debian is going to come with very thoroughly tested software. It will never be bleeding edge, but since things get upgraded after being thoroughly tested, it won't be very out of date at any point. In a year, Etch will have newer packages that the ones that ship with Gutsy Gibbon.

---

### Post by Elvish Legion on 2008-01-15
So with debian I won't have to always basically break my system with an upgrade every 6 months is the only major difference?

---

### Post by p_quarles on 2008-01-15
Well, you don't "have to" upgrade every six months with Ubuntu either. But yes, with Debian Stable you'll get applications that are older than the newest Ubuntu release, but newer than the Ubuntu LTS packages after about a year. As an example, the current version of Firefox (which Debian rebranded as Iceweasel) in Etch is 2.0.0.3.

---

### Post by Elvish Legion on 2008-01-15
> **p_quarles said:**
> Well, you don't "have to" upgrade every six months with Ubuntu either. But yes, with Debian Stable you'll get applications that are older than the newest Ubuntu release, but newer than the Ubuntu LTS packages after about a year. As an example, the current version of Firefox (which Debian rebranded as Iceweasel) in Etch is 2.0.0.3.

What about testing or unstable same deal?

---

### Post by p_quarles on 2008-01-15
Yep. Testing is relatively safe, too. Stable is basically targeted at mission critical situations. Unstable is more or less like an Alpha version of Ubuntu, so stay away from that. 

I should add, too, that Debian does dist-upgrade every now and again. There's no set schedule, but it's usually like a couple years. Basically, each distro would get a new status: Etch would become "Old Stable" (still supported), Lenny would become "Stable," and Sid would become "Testing." Some other character from Toy Story would then be made the new Unstable. So, it really is a good option if you value stability and low-maintenance work over bleeding edge software.

---

### Post by gsmithe on 2008-01-24
For the record: Debian unstable is always called "sid."

---

### Post by Tadpole on 2008-05-22
Hi guys, I have a question about this. I created the most minimal installs possible with debian netinst ISO and ubuntu minimal ISO, with no desktop environment of any kind (just a simple CLI). I then installed Xorg on both. Debian's install is now taking 692MB of disk space, while ubuntu's is 842MB. Why the difference? What packages does ubuntu have underneath that debian does not?

---

### Post by Tadpole on 2008-05-22
Nobody knows? I'm trying to use either debian or ubuntu as the base for a custom distro I'm designing, but I can't decide which to use. I'm leaning towards debian as it seems its minimal version is less bloated.

---


---
title: "Parental Controls for Ubuntu"
date: 2006-11-19
forum: General Help
---

### Post by pianoboy3333 on 2006-11-19
Someone asked me for a good parental control software, something that would be the equivalent of Norton's parental control software for linux. I tried taking a look at dansguardian, but it seemed hard to setup and configure, and it was all text based by the looks of it...

I recently landed upon CensorNet ([http://www.censornet.com/](http://www.censornet.com/)) and that appears to be what I'm looking for, but when I boot up into the install cd, it freezes at the first screen.

I was wondering if anyone has had a similar problem with CensorNet and knows of a workaround. Or if you know of another easy to use parental control software that I am looking for, or some gui to dansguardian. Help!

---

### Post by pianoboy3333 on 2006-11-19
Does anyone know how to properly setup dansguardian and squid...?

---

### Post by pianoboy3333 on 2006-11-19
Does UbuntuCE use a gui for dansguardian?

---

### Post by NetworkGuy on 2006-11-19
IMHO - You really don't need a GUI for DansGuardian.  Everything you need is in the same directory (usually /etc/dansguardian) and once it's setup right, rarely needs to be edited.

DansGuardian does require a proxy server (squid for example) however, you can not use it directly as a proxy server.

---

### Post by pianoboy3333 on 2006-11-20
Dansguardian doesn't seem like the best choice, because you can just edit those files with the root password, no?

---

### Post by iamhugeinjapan on 2006-11-20
^^^ Solution: Don't give the kids the root password! :)

Any parental controls are rendered pretty much useless if the people being controlled have root/sudo access.

---

### Post by pianoboy3333 on 2006-11-21
> **iamhugeinjapan said:**
> ^^^ Solution: Don't give the kids the root password! :)

Any parental controls are rendered pretty much useless if the people being controlled have root/sudo access.

But can't they just use their own "sudo" password that they use to login with?

OR can you un-hash the root password and use su, which sudo won't affect?

---

### Post by doobit on 2006-11-21
No, you can choose exactly what privileges to give a user when you create the user. They can even be "unprivileged" as a profile..There is a GUI (users and groups) to guide you in the system menu. The second tab allows you to choose exactly what things a user will have access too. 
You can also limit domain access directly with Firestarter, or a router's firewall with domain or IP filtering.

---


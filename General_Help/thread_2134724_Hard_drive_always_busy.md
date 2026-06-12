---
title: "Hard drive always busy"
date: 2013-04-12
forum: General Help
---

### Post by Sinopa on 2013-04-12
For some strange reason, my hard drive is almost always busy and I'm afraid that it's soon going to break down. It's even busy when it's idle. This problem started about a week ago. I tried fining out what it was by starting htop, but it shows no irregularities. No extra processes running that took large mount of cpu power, nor memory. 

Does anyone know why this is? Or does anyone know where I can find a simple to use file access monitoring software, so I can find what files are being accessed?

---

### Post by rnerwein on 2013-04-12
> **Sinopa said:**
> For some strange reason, my hard drive is almost always busy and I'm afraid that it's soon going to break down. It's even busy when it's idle. This problem started about a week ago. I tried fining out what it was by starting htop, but it shows no irregularities. No extra processes running that took large mount of cpu power, nor memory. 

Does anyone know why this is? Or does anyone know where I can find a simple to use file access monitoring software, so I can find what files are being accessed?
hi
sound like a little bit of work.
try: sudo lsof | grep your_mountpoint > file_bla
then you can search in file_bla to figure out what's going on.
ciao

---

### Post by Sinopa on 2013-04-12
Thanx rnerwein. I'll try that :)

---

### Post by |{urse on 2013-04-12
Well, you need to test your hard drive, sounds like, grab a bootcd with testing tools and make sure the drive isn't dying.

---

### Post by Sinopa on 2013-04-12
I discovered the problem. It was tumbler. I don't know why it kept going and going, but I've removed it now :)

---


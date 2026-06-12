---
title: "startup splash"
date: 2014-04-15
forum: General Help
---

### Post by norman_logan on 2014-04-15
I have resently upgraded to ubuntu 12.04, every thing works well but at startup Ii get a splash screen saying "the diskdrive/temp is not ready yet or present" help

---

### Post by Frogs Hair on 2014-04-15
Hello and Welcome 

I was looking into this problem a few days ago and found some results by searching.   

[http://askubuntu.com/questions/392720/the-disk-drive-for-tmp-is-not-ready-yet-s-to-skip-mount-or-m-for-manual-recove](http://askubuntu.com/questions/392720/the-disk-drive-for-tmp-is-not-ready-yet-s-to-skip-mount-or-m-for-manual-recove)

---

### Post by Double.J on 2014-04-15
Hi there! I too have experienced this from time to time.

Frog Hair's link looks familiar re fstab, but I think i also had to resolve dpkg after.

```
 sudo apt-get update -f
```

To tell you what's wrong. 

Mine started after i downloaded a .deb and realised too late that it asked me a question i didn't read about using /tmp](*,)

Jj

---

### Post by pfeiffep on 2014-04-15
> **norman_logan said:**
> I have resently upgraded to ubuntu 12.04, every thing works well but at startup Ii get a splash screen saying "the diskdrive/temp is not ready yet or present" help
I had a similar issue with my Dell laptop when running 12.04. I can't prove exactly what was wrong, but I think a relatively slow disk drive and being pretty full made the problem worse. 
I installed[ bleachbit]("http://bleachbit.sourceforge.net/") and ran it always immediately prior to shutting down and I never saw the symptoms again. Bleachbit is available in Software center.

---


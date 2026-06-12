---
title: "&quot;nautilus-columns&quot; package not working on ubuntu 13.04"
date: 2013-05-22
forum: General Help
---

### Post by hg088 on 2013-05-22
This package allowed nautilus to read file metadata and sort files based on it.

But this stopped working since i installed ubuntu 13.04.

Any way of making this package work.

---

### Post by woodyg on 2013-06-19
I would also like to use nautilus-columns, but installation of it does not change anything. Does anyone know what the problem is? Isn't it [supposed to work]("http://www.ubuntuupdates.org/package/webupd8/raring/main/base/nautilus-columns") for 13.04?

---

### Post by hg088 on 2013-06-19
It should work but theres a bug in ubuntu 13.04 that breakes all python extensions for nautilus. [http://ubuntuforums.org/showthread.php?t=878683&page=15](http://ubuntuforums.org/showthread.php?t=878683&page=15)

---

### Post by mc4man on 2013-06-19
> **woodyg said:**
> I would also like to use nautilus-columns, but installation of it does not change anything. Does anyone know what the problem is? Isn't it [supposed to work]("http://www.ubuntuupdates.org/package/webupd8/raring/main/base/nautilus-columns") for 13.04?
nautilus-python is broken in raring, though pushed a fix that is now in saucy, for raring users left the test ppa up that fixes - 
[https://launchpad.net/~mc3man/+archive/n-p-testfix](https://launchpad.net/~mc3man/+archive/n-p-testfix)

---

### Post by woodyg on 2013-06-20
> **mc4man said:**
> nautilus-python is broken in raring, though pushed a fix that is now in saucy, for raring users left the test ppa up that fixes - 
[https://launchpad.net/~mc3man/+archive/n-p-testfix](https://launchpad.net/~mc3man/+archive/n-p-testfix)


Has anyone managed to get this to work? I installed nautilus-python test builds, but nautilus-columns still does not seem to work... Do I need to do something, beyond installation, to get nautilus-columns to work?

---

### Post by mc4man on 2013-06-20
> **woodyg said:**
> Has anyone managed to get this to work? I installed nautilus-python test builds, but nautilus-columns still does not seem to work... Do I need to do something, beyond installation, to get nautilus-columns to work?

Went ahead & installed the n-colums package in 13.04 & tried on a music album, for the most part works ok, didn't get genre or bitrate from flacs. see screen
Not all that thrilled with, don't like how it truncates  folder name if a number of colums are added. (not in screen

Did you restart nautilus?
If starting nautilus from terminal are there any errors shown?

---

### Post by woodyg on 2013-06-20
> **woodyg said:**
> Has anyone managed to get this to work? I installed nautilus-python test builds, but nautilus-columns still does not seem to work... Do I need to do something, beyond installation, to get nautilus-columns to work?

It does work. I on the other hand am a bit dizzy... I confused Nautilus with Thunar (Thunar is my default file manager). It works fine with Nautilus.

---

### Post by hg088 on 2013-06-20
> **woodyg said:**
> It does work. I on the other hand am a bit dizzy... I confused Nautilus with Thunar (Thunar is my default file manager). It works fine with Nautilus.
Its broken in raring, in other versions of ubuntu works great

---

### Post by hg088 on 2013-06-20
> **mc4man said:**
> nautilus-python is broken in raring, though pushed a fix that is now in saucy, for raring users left the test ppa up that fixes - 
[https://launchpad.net/~mc3man/+archive/n-p-testfix](https://launchpad.net/~mc3man/+archive/n-p-testfix)
That successfully fixes nautilus python in raring, thanks for that

---

### Post by colingweaver on 2013-12-31
In case the above ppa doesn't work (it didn't for me), you could try the following (which did work on my computer -- x86_64, linux Mint 15):

sudo ln -sf /usr/lib/x86_64-linux-gnu/libpython2.7.so.1 /usr/lib/libpython2.7.so.1
sudo ldconfig

(From [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1157246](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1157246))

---


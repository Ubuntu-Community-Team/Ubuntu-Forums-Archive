---
title: "banshee libipodevice make error"
date: 2006-11-29
forum: General Help
---

### Post by a.d.gardiner on 2006-11-29
hey all,

i am trying to get banshee working with my ipod. I've been through following a few guides but keep getting stuck when they tell me to use the command 'make'.

I've been using this tutorial, have banshee installed and am as far as installing libipodevice.

[http://www.ubuntuforums.org/showthread.php?t=261253&highlight=libipoddevice](http://www.ubuntuforums.org/showthread.php?t=261253&highlight=libipoddevice)

I get an error when I do..
```

cd libipoddevice-0.5.0
./configure --prefix=/usr
make
sudo make install
cd ..

```

i get as far as the make bit and then terminal replys with make: "*** No targets specified and no makefile found. Stop."

Im still pretty new and the whole make thing is confusing me!

any ideas? ](*,)

---

### Post by a.d.gardiner on 2006-12-02
so, any ideas?

---

### Post by a.d.gardiner on 2006-12-03
It seems like if you try anything for long enough you can fix it. I don't know for sure but it appears that because I'm using Xubuntu rather than Ubuntu my install came standard with a load less stuff.

Simply I needed to install compilers and things and now everything is working just fine. Thats why make wasn't working. Im new so I didn't get it. lol

If I remember tomorrow i'll post a list of what I had to install extra incase anybody else gets stuck with this.

:)

---


---
title: "how to restore packages from AptOnCD"
date: 2007-09-02
forum: General Help
---

### Post by vadania on 2007-09-02
How do I install packages on a AptOnCD backup? Using the AptOnCD only copies them to apt cache, but does not install them properly.

Or how do I install all packages in a directory?
Or how do I install all packages in cache?

---

### Post by SOULRiDER on 2007-09-02
Im still wondering why it doesnt install them.. i had the same issue in my friends house to. What i did was go to /var/cache/apt/archives (i THINK thats where the packages are stored) and i did

```
sudo dpkg -i *.deb
```

That installed everything :P

---

### Post by vadania on 2007-09-03
Thanks! That's what I was looking for!

---

### Post by linuxtoindia on 2008-03-20
thanks got it.. but how to install all of them at a time?
and also along with the dependcies!?
if possible please help me remotely.. i will grant you access

---

### Post by ryanhaigh on 2008-03-20
I think you should use ```
sudo apt-cdrom
``` with the CD in to add the CD as a source. Then you should be able to go into Synaptic (System>Admin) and in the bottom left click the origin button, the CD should be one of the sources, click that then select all and mark for install.

---

### Post by linuxtoindia on 2008-03-20
after adding cd rom we just see all the packages!
how to know the packages only on cd from the list ,, or can we create a separate list for the all packages on cd!?

---

### Post by linuxtoindia on 2008-03-20
still not fixed!!


 and can we add the iso image itself instead of cd? 
or the user cache itself ?
to the synaptic?

---

### Post by ryanhaigh on 2008-03-20
Sorry I'm having a little trouble understanding what you mean.

Were you able to add the cdrom using apt-cdrom add?
Did the CD appear in the Synaptic when you click the origin button in the bottom left?

---


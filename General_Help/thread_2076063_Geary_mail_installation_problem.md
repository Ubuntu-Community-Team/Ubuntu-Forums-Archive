---
title: "Geary mail installation problem"
date: 2012-10-25
forum: General Help
---

### Post by sobakasu on 2012-10-25
So I wanted to install Geary mail program, but I was out of luck.

I added the repository via

```

sudo apt-add-repository ppa:yorba/ppa
sudo apt-get update && sudo apt-get install geary
```

but the installation command only gives out an error:

```
E: Couldn't find package geary
```

Any ideas? :(

---

### Post by 2F4U on 2012-10-25
I looked at the ppa and there are no packages for 12.10. So, if you use 12.10 you can't install from this ppa. Might be because the package is now in the universe repository for 12.10.

[http://packages.ubuntu.com/de/quantal/geary](http://packages.ubuntu.com/de/quantal/geary)

---

### Post by sobakasu on 2012-10-26
Actually I am still using Lucid, I completely forgot to mention that.

Thanks for the repository link! :)
Will the .deb work even on non-12.10 systems?


Edit:

I tried to add the Quantal repository via synaptic

```
deb http://archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://archive.ubuntu.com/ubuntu/ quantal main restricted
```

but not only do I get this error:
```
 W: There is no public key available for the following key IDs: > 3B4FE6ACC0B21F32
```

but also, geary is not found yet again... :(

(Never mind my crazy experimenting and non-existing knowledge, for me, my system is more or less a playground and sandbox for trying stuff out^^)

---

### Post by 2F4U on 2012-10-27
>  			 		   		 		 		Actually I am still using Lucid, I completely forgot to mention that.

There are no Geary packages for Lucid in that repository.

---


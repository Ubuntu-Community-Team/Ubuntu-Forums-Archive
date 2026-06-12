---
title: "bmpx in Edgy"
date: 2006-12-19
forum: General Help
---

### Post by JurB on 2006-12-19
I just installed Edgy on a seperate partition to try out bmpx.
Couldn't get it installed in Dapper , so after a few months of resisting the urge to try it, i gave in.
Now the damn thing won't install! Aaaaaagrh!

I added the bmpx repo as advised on the site, with apt-key and the works....
now it's complaining about not being able to install libmp4v2-0.

Please help [-o<

---

### Post by xopher on 2006-12-19
Make sure you have the multiverse repository enabled. Since that is where libmp4v2-0 is located:

[http://packages.ubuntu.com/edgy/libs/libmp4v2-0](http://packages.ubuntu.com/edgy/libs/libmp4v2-0)

If you do have multiverse enabled, try installing libmp4 manually or separately, then install bmpx.

The package worked / installed without any problems for me.

---

### Post by JurB on 2006-12-19
Yeah... just figures that out... i uncommented everything in sources.list, but it was not checked in synaptic:confused: 

thanks anyway

---

### Post by xopher on 2006-12-19
Great it worked out. Please post if you have any problems (package related), as Im the maintainer of that repository ;)

---


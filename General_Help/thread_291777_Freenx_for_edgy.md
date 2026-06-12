---
title: "Freenx for edgy?"
date: 2006-11-02
forum: General Help
---

### Post by zanophol on 2006-11-02
I have googled to no avail, so has anyone running edgy found a repository for freenx/nxserver?

---

### Post by Divan Santana on 2006-11-05
No unfortunately, please email me if you have any luck with this :)

---

### Post by garretwp on 2006-11-05
Add this to your sources.list file for apt:

# Freenx
deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx

Then do apt-get update and apt-get install freenx. After you are done with that configure freenx to your liking and things should be golden. I have it running right now under edgy.

- Garrett

---

### Post by pkarlos_76 on 2006-11-06
That link is for dapper sources not edgy! :-? But I'll try it...

---

### Post by pkarlos_76 on 2006-11-06
> **pkarlos_76 said:**
> That link is for dapper sources not edgy! :-? But I'll try it...

Looks like it worked like a charm...

---

### Post by jdong on 2006-11-06
In all theory those packages should work, but to be extra safe you should rebuild them for Edgy...

---

### Post by garretwp on 2006-11-06
I know they are for dapper and not edgy. But I have installed it and have it running as we speak with no issues. If you are concerned on running dapper packages on edgy, then I would advise not to proceed. But if you are feeling risky, then give it a shot. Again it works for me, but your mileage may very.

- Garrett

---

### Post by jdong on 2006-11-06
It would be a better idea to add the deb-src repository, then use prevu to "backport" those packages to Edgy

---

### Post by loren95404 on 2006-11-06
This looks interesting, I think I'll give it a go

---


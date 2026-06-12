---
title: "Install Open Office in Xubuntu"
date: 2007-07-10
forum: General Help
---

### Post by martin.erding on 2007-07-10
Hi,

I just tried to install Open Office in Xubuntu 7.04 over menue  "Add/Remove Applications" in "System"-menue.

But it tells me: "OpenOffice.org WordProcessor cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type".

This is strange, cause I installed OOo in a former Ubuntu on the same Thinkpad on the same way.

Many thanks for helping,
Martin

---

### Post by ronocdh on 2007-07-10
I don't use Xubuntu, but maybe is does not support OO for some reason? As I understand it, Xubuntu is designed for low-end hardware, and so maybe OO is deemed too bloated to run well on it? I would try alternatives like AbiWord, etc. first, and if you decide you definitely want OO, maybe post on their forums.

---

### Post by martin.erding on 2007-07-10
Hi,

I was trying, because it is told in xubuntu.org, that one can install in Xubuntu any application, which can be installed in Ubuntu or Kubuntu.

So it should work, anyhow. I just do not know how.

Many regards,
Martin

---

### Post by bapoumba on 2007-07-10
```
$ aptitude show openoffice.org
Package: openoffice.org
State: installed
Automatically installed: no
Version: 2.2.0-1ubuntu3
Priority: optional
Section: editors
```
Quite strange. I ran your error in google but did not find anything like it. Could you please paste the complete error output?

---


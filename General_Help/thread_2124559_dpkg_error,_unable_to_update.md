---
title: "dpkg error, unable to update"
date: 2013-03-11
forum: General Help
---

### Post by jakefish on 2013-03-11
Hello I am unable to update my pc

I keep getting this error

dpkg: error: parsing file '/var/lib/dpkg/available' near line 10037 package 'libavcodec-extra-53:amd64':
 field name ``This' must be followed by colon
Error in function: 


Hope someone can help

John

---

### Post by ibjsb4 on 2013-03-11
Looks like you can just do what it says and insert a colon.

```
gksudo gedit /var/lib/dpkg/available
```

 Or dpkg/available has a backup.  You can try using it.

```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.broken && sudo mv /var/lib/dpkg/available-old /var/lib/dpkg/available
```

---

### Post by schragge on 2013-03-11
The easiest way to cure this is
```
sudo dpkg --clear-avail
```
*/var/lib/dpkg/available* will be re-created on the next run of *apt-get update*

---

### Post by ibjsb4 on 2013-03-11
> **schragge said:**
> The easiest way to cure this is
```
sudo dpkg --clear-avail
```
*/var/lib/dpkg/available* will be re-created on the next run of *apt-get update*

Yep, that work perfect :)

---


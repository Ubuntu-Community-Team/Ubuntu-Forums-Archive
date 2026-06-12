---
title: "RPM to DEB with alien"
date: 2007-10-06
forum: General Help
---

### Post by t4ggs on 2007-10-06
Hi, im kind of new in linux, i downloaded an rpm and want to convert it to deb file, i installed alien from synaptic and now im using this command 
$sudo alien -k myfile.rpm
so i can convert the file that is in my desktop
but i get this message: Must run as root to convert to deb format (or you may use fakeroot).

 I also tried "cd Desktop" and then the whole "$sudo alien -k myfile.rpm" but i still get the same error message. I wonder if u can help me please.

---

### Post by por100pre1 on 2007-10-06
Try this:

```
sudo su -c 'alien -k myfile.rpm'
```

EDIT: Dont use the $ sign just do this:

```
sudo alien -k myfile.rpm
```

---

### Post by Lord Illidan on 2007-10-06
Also, do check if the software is available as a deb somewhere. Sometimes, rpm software can crap your system, especially if it is quite old.

---


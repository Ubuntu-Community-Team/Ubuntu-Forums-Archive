---
title: "GTKOrphan"
date: 2008-04-13
forum: General Help
---

### Post by harrykh on 2008-04-13
So is it possible to break things using this prograk coz I kept on deleting packages I know nothing about (:p) and it actually made more orphans (I think, I'm not sure). 

VLC, Skype, ubuntu desktop, AWN are orphans when check the "show orphans on other dirs" (or something like that), is this normal ? They all seem to work fine. What happen if I remove, say VLC, using gtkorphan, will the program itself be remove or is it just some kind of installation file(s).

---

### Post by ellgor on 2008-04-13
Hi,

Be very careful about what you delete, I found that what I thought (implied by GtkOrphan) was an unrelated part of a file caused a serious breakdown in a totally unrelated program, just be careful.

Regards, Ellgor.

---

### Post by kerry_s on 2008-04-13
gtkorphan is more for debian, not ubuntu, ubuntu rebuilds things tying everything together to the ubuntu-desktop meta package so if you remove any part it will all start to show as unneeded.

---


---
title: "howto change uuid of a harddisk"
date: 2007-09-27
forum: General Help
---

### Post by DLGandalf on 2007-09-27
I'm really amazed that I can't find an answer to my relatively simple question on google.. how do I change a UUID on a harddisk. 
a UUID is not given by the manufacturor right?

---

### Post by 5-HT on 2007-09-27
A combo of using uuidgen to generate the identifier and tune2fs to assign that uuid to a particular filesystem will do the trick.
cheers,

---

### Post by DLGandalf on 2007-09-27
thank you!

---


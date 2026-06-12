---
title: "Creating .deb's"
date: 2006-10-18
forum: General Help
---

### Post by Keshyden on 2006-10-18
I was interested in looking into the possibility of creating debs for certain software. I am not a programmer myself, but it is something I would like to learn.

Any info or links would be great.

Sorry if this is the wrong section.

---

### Post by PriceChild on 2006-10-18
follow the guidelines for packaging from source:
```
./configure
make
```for example, but instead of ```
sudo make install
```use ```
sudo checkinstall
```which will package it into a deb for you :)

---

### Post by Keshyden on 2006-10-19
Thanks for the response. Will this create a deb compatible with only my system or will it work on others too?

---

### Post by xianyun on 2006-11-10
thank you very much too.I've been looking for the info:)

---

### Post by Anonii on 2006-11-10
> **Keshyden said:**
> Thanks for the response. Will this create a deb compatible with only my system or will it work on others too?
It will probably work on others too, but its not the _correct_ way on creating .debs out of source. Unfortunately, I'm lame and I dont know _why_ its not the correct way. The correct way, tho, involves using pbuilder (afaik). _BUT_, most unofficial .debs that you can find in these forums are created using checkinstall like PriceChildu described, and most times they work on foreign machines. So I suggest you to try it out. Its easy, much faster (.debs creted the other way take much moar time) and they will most probably work.

---

### Post by 23meg on 2006-11-10
Packages created with checkinstall will not inherit dependencies. Only distribute checkinstall-created packages publicly if they have no dependencies and don't contain system-critical software.

---


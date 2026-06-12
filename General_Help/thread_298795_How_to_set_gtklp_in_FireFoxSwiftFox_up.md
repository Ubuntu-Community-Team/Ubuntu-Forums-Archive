---
title: "How to set gtklp in FireFox/SwiftFox up?"
date: 2006-11-13
forum: General Help
---

### Post by madmaxx on 2006-11-13
Hi!

From most apps I am able to print using gtklp -- a very comfortable and powerful printing GUI for GNOME -- but not from my current FF/SwiftFox.
In earlier versions, it was possible to change the printer command; this dialog seems to be gone ](*,) 

So, I located all printer commands in "about:config" and changed the commands from "lpr ${..blabla..}" (don't remember exactly) to "gtklp".
But still, the same (bad) printer dialog from FF remains, no starting of gtklp. :-k 

TIA for any helpful comments!
madmaxx

---

### Post by bmt on 2007-02-05
For Firefox v2:

From the File->Print dialog, in the Printer list select 'PostScript/default' then click on the 'Properties' button.

In the 'printer command' box:
```
/usr/bin/gtklp
```
and click 'OK' then 'Print'.

If you haven't already got this far (several months later), perhaps this will help someone else. ;-)

---

### Post by Wiebelhaus on 2007-05-03
> **bmt said:**
> For Firefox v2:

From the File->Print dialog, in the Printer list select 'PostScript/default' then click on the 'Properties' button.

In the 'printer command' box:
```
/usr/bin/gtklp
```
and click 'OK' then 'Print'.

If you haven't already got this far (several months later), perhaps this will help someone else. ;-)

Confirmed!

Thanks bud.

---


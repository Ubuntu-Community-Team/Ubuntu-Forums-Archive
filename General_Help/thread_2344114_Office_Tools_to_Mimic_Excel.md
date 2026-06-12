---
title: "Office Tools to Mimic Excel"
date: 2016-11-22
forum: General Help
---

### Post by Myst1234 on 2016-11-22
Hi All,

Which office software best mimics Excel? 

Specifically, I need to see deeper into Pivot Tables than LibreOffice or WPS Office appears to let me. (if this is user error I'm sorry, please let me know how to "see deeper")

The screen shots show the excel pivot table. In the Linux counterparts, I do not have those extra + signs that allow a further expansion of the pivot table. (sorry for any terrible explanations, I wasn't sure how to word this)

[ATTACH=CONFIG]272304[/ATTACH] [ATTACH=CONFIG]272305[/ATTACH]


Does anyone know a product or workaround that doesn't involve running MSOffice in some sort of dual-boot/VM scenario?

Thanks in advance!

---

### Post by QIII on 2016-11-22
There may be, so let's wait for other responses.

But I do want to say that as spreadsheet apps go, Excel is probably the best and most fully featured.  So some things may just work better in Excel.

Use what works.  It doesn't matter if it's a Microsoft product.  I don't remember anything in the Linux Use Agreement that said I could not use Microsoft products, although there is certainly a faction that would call me "unethical".

---

### Post by Myst1234 on 2016-11-22
> [COLOR=#000000]although there is certainly a faction that would call me "unethical".[/COLOR]
haha!

Main thing I'm trying to avoid is running a VM, dual-boot or buying an MSOffice license. If there are no other options, I'll bite those bullets, but I'd like to exhaust all other options first. Thanks!

---

### Post by QIII on 2016-11-22
I hear ya!

---

### Post by Mark Phelps on 2016-11-22
One of the downsides of running a VM that is often overlooked, is that if you have both a physical Windows installation and a VM installation on the same PC, the MS Activation Servers see those a two different "devices".  Something about the hardware "hash" that gets generated when you install Windows into a VM, even when that is on the same physical drive as the installed version, tells MS that it is not the same install.

The result of this is that, when you switch over to the VM, after having activated Windows (and MS Office) on the installed version, you get prompted to activate AGAIN ('cause MS thinks this is a new installation).  This DEACTIVATES the physical installation on that PC.

Then, when you relogin to the physical installation, you get prompted to reactivate IT!

And so on, and so on, and so on -- until you exceed the UNKNOWN activation limit that Microsoft has set. 

So, while lots of folks see VMs as a miracle cure, they are problematic, when you want to use them in a dual-boot installation.

---

### Post by oldfred on 2016-11-22
When I first started using spread sheets, the limit of rows & columns about matched the 9 pin printer output on two pages of greenbar (wider) paper. And it would not merge two sheets which I really needed.
So I learned dbase, wrote some programs and did my own merge. Printed output was just like spreadsheet but I could merge.

Found that may times larger spreadsheets were a disadvantage. Hard to audit and difficult to understand someone elses. 

You may want to think about database and how you really want data organized.

---


---
title: "openoffice bloating docs"
date: 2008-04-24
forum: General Help
---

### Post by seamuso on 2008-04-24
pretty much like the topic says. Original file (.xlt office xp) is 9.5 KB .. saving to new filename with no changes, new filesize is now 102 KB .. export to pdf gives a file that's now 158 KB .. 

Originally (I think it was still the 1.x version) my pdf's created from the .xlt were ~50KB in size. I've been trying to track this down ever since the newer versions of OO were released. Has anyone else encountered this?

Resolved by someone at the OO forums .. using print to pdf instead of exporting creates a pdf that's about 12KB in size.

---

### Post by calc on 2008-04-24
> **seamuso said:**
> pretty much like the topic says. Original file (.xlt office xp) is 9.5 KB .. saving to new filename with no changes, new filesize is now 102 KB .. export to pdf gives a file that's now 158 KB .. 

Originally (I think it was still the 1.x version) my pdf's created from the .xlt were ~50KB in size. I've been trying to track this down ever since the newer versions of OO were released. Has anyone else encountered this?

Resolved by someone at the OO forums .. using print to pdf instead of exporting creates a pdf that's about 12KB in size.

There are two issues here. I think the first issue is probably relating to the preview image of the file being included in the file. There is a bug about this in OpenOffice issue tracker but I don't have the number handy. Also the pdf export problem is a known bug that is in issue tracker as well, the problem with that is that it does not properly subset fonts, so it includes the entire font into the pdf, which causes it to grow much larger. Another way to reduce the size of the pdf would be to run pdf2ps then ps2pdf on the file which should make it much smaller.

---


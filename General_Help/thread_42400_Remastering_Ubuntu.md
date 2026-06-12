---
title: "Remastering Ubuntu"
date: 2005-06-17
forum: General Help
---

### Post by APerezL on 2005-06-17
Hi!

I'm trying to remaster a Ubuntu 5.04 LiveCD and despite i'm following the LiveCDCustomizationHowto and the md5sum.txt is ok, when I boot from this remastered CD I get an "Non-Ubuntu CD-ROM detected".

What's the role of the README.diskdefines ? where can I bypass this autocheck?

thanks!

---

### Post by APerezL on 2005-06-20
[Auto-Reply]

While the remastering process I've forgotten the /cdrom/.disk because I ran a "cp -Rp * /dest". There are 3 files inside this path, one called "info", that the installer checks for the existence of this file.

The next step is: how can I modify the /isolinux/*txt files? all of them have the txt extension, but the "file" command  returns "data" as file content. Inside this files are defined the screens showed by Ubuntu, and the ones that are showed when the user press F1, ...FX keys ... any clue?

thanks!

---


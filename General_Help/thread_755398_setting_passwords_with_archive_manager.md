---
title: "setting passwords with archive manager"
date: 2008-04-14
forum: General Help
---

### Post by Old Jimma on 2008-04-14
Ubunbuers:

I want to compress a file with archive manager and I want to set a password.

When I right click on the folder I want to archive, there isn't any place to set a password.

How do I do this?

Thanks,
Phil Smith
Duluth, GA

---

### Post by fguilhon on 2008-04-15
This is a known problem. There's a bug report in [https://bugs.launchpad.net/fileroller/+bug/97114]("https://bugs.launchpad.net/fileroller/+bug/97114").
You can do that from the command-line using, for example, zip:
```
zip -er dir.zip Dir/
```
The e option encrypts with pass and r option recurse on dirs..

---

### Post by ryanhaigh on 2008-04-15
You can do this but not with the right-click create archive method. To do it open archive manager (in applications>accessories) or press alt-f2 and enter file-roller.
Press new to create an archive and save it where you want as yourfilename.zip. Then go to edit>password and enter your password. You can then drag and drop or use the add button to add the files you want to the archive.

Keep in mind that zip passwords aren't very secure and there are even apps available in the ubuntu repos to help crack them (fcrackzip)

---

### Post by fguilhon on 2008-04-16
zip is just an example... anyway, zip isn't secure for a big company protecting sensitive data but for you personal use, using at least 8 chars passwords is pretty safe (including numbers and maybe uppercase and lowercase helps)

---


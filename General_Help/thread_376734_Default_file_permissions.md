---
title: "Default file permissions"
date: 2007-03-05
forum: General Help
---

### Post by malder on 2007-03-05
I would like to force any file created in a folder to default to certain permissions (770 to be exact). I also want the file to keep those permissions. Right now if I go in and chmod -R, then someone in the group modifies the file it defaults back to unwrittable for the group, which is what I don't want. Is there a way to make sure that even when someone in the group modifies the file it is still saved 770?

Thanks!

Matt

---

### Post by colo on 2007-03-05
Sane applications don't touch a file's octal permissions on write.
Which tools are you referring to when you talk about your group-members writing?

---

### Post by malder on 2007-03-05
this is with a program called [SFTPdrive]("http://www.sftpdrive.com"). So you're saying that maybe it's an issue with this program? Now that you mention it - when saving the file it (MS Excel) asks to 'overwrite' the file rather than just save. Wonder if that's the issue...

Thanks

Matt

---


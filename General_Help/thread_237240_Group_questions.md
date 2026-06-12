---
title: "Group questions"
date: 2006-08-15
forum: General Help
---

### Post by lastexyle on 2006-08-15
I'm still somewhat new to the world of Ubuntu and I've been curious about what exactly many of the groups in Ubuntu are. Some of the groups are obvious, but many others aren't. If anyone could explain to me what adm, admin, audio (play audio?), cdrom (access cdrom?), dialout, dip, floppy (use floppy disk I assume), lpadmin, plugdev, scanner, video (display anything? I can do that without being in the group though) all mean I'd be very grateful.

Also, what is the difference between a primary group and secondary groups?

---

### Post by aggyb on 2006-08-15
Most of these groups are left overs from old system defaults that are no longer used AFAIK.  One would be able to set the group of a device to say audio and all users in the audio group would have access to it.  This wikipedia article might help a bit:
[http://en.wikipedia.org/wiki/Group_identifier_%28Unix%29]("http://en.wikipedia.org/wiki/Group_identifier_%28Unix%29")

As for the meanings of you group names here's what I can gather:
adm & admin - Used for system admins
audio, cdrom, dialout, dip (fairly sure this is Dialin IP), floppy, scanner & video - Allow access to certain devices in /dev
lpadmin - This will be for users who have admin right for printers  (lp stands for line printer)
plugdev - I've no idea about this one.

Please correct me if I'm wrong on any of this.

AggyB

---


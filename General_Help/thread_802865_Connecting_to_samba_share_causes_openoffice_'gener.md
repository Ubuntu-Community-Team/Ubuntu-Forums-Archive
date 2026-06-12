---
title: "Connecting to samba share causes openoffice 'general internet error has occurred'"
date: 2008-05-21
forum: General Help
---

### Post by daehenoc on 2008-05-21
Hi all,

I have Ubuntu installed on a laptop and when connecting to a samba share off a Debian server (via Places -> Network -> Windows Network -> name_of_workgroup -> name_of_server -> name_of_share -> pick_any_oo_file) OpenOffice starts but then pops up an error window: "General Internet error has occurred" and the file does not open.

I suspected this is because the share is being mounted via smb (a similar problem is reported in Eye of Gnome when opening jpeg files "No images found in 'smb://fileserver/share/filename.JPG'."), so I mounted the share directly using CIFS and the problem went away, woot!

So two questions:
1) Is anyone else experiencing this problem and how did they work around it or fix it, if so I will log a bug in launchpad, and;
2) How do I get Ubuntu to use CIFS as the default mounting method for samba shares in Places->Network->Windows Network->blablabla.

The reason I need to have a further fix is that this is not my laptop, it belongs to a client and I don't want to have them manually mount this share (# mount /media/fileserver-files, I have made an entry in the fstab file) every time they want to go there.

Versions:
OpenOffice.org: 1:2.4.0-3ubuntu6

Thanks,
Greg

---

### Post by jdongmo on 2010-09-21
for solving your problem, you need to add option 'noblr' on your /etc/fstab
that work for me.

---


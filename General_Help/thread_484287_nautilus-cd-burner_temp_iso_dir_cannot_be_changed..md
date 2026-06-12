---
title: "nautilus-cd-burner: temp_iso_dir cannot be changed..."
date: 2007-06-25
forum: General Help
---

### Post by Franko30 on 2007-06-25
Hi,

I'm trying to burn files to a DVD with nautilus-cd-burner, which is no prblem when doing this from an ISO-file. But when adding files and directories, Nautilus always wants to write temp-files in /tmp . It's the same with Brasero which uses nautilus-cd-burner.

Unfortunately I don't have enough space in my /tmp directory.

In **gconf-editor** I tried to change the **temp_iso_dir** of **nautilus-cd-burner** as described here:

[http://live.gnome.org/Nautilus#head-f2a0b4f437160b8659a4c3d4fdc655f89edbacc0](http://live.gnome.org/Nautilus#head-f2a0b4f437160b8659a4c3d4fdc655f89edbacc0)

or here:

[http://kbase.redhat.com/faq/FAQ_35_5658.shtm](http://kbase.redhat.com/faq/FAQ_35_5658.shtm)

or here (German):

[http://www.linuxforen.de/forums/archive/index.php/t-210226.html](http://www.linuxforen.de/forums/archive/index.php/t-210226.html)

but to no avail!

No matter what I enter (and then restart nautilus with nautilus -q or via rebooting) the directory won't be used and the temp-files are always created in /tmp .

What am I doing wrong? Or is this a bug?

Thanks in advance

Franko30

---

### Post by Franko30 on 2007-06-26
Anyone?

---


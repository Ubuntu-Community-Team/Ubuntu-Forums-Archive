---
title: "Problem opening Firefox or Thunderbird"
date: 2014-04-24
forum: General Help
---

### Post by Edward_Diener on 2014-04-24
Suddenly when I try to start Firefox I am getting:

(process:3678): GLib-CRITICAL **: g_slice_set_config: assertion
'sys_page_size == 0' failed

(firefox:3678): GLib-GObject-WARNING **: Attempt to add property
GnomeProgram::sm-connect after class was initialised

(firefox:3678): GLib-GObject-WARNING **: Attempt to add property
GnomeProgram::show-crash-dialog after class was initialised

(firefox:3678): GLib-GObject-WARNING **: Attempt to add property
GnomeProgram::display after class was initialised

(firefox:3678): GLib-GObject-WARNING **: Attempt to add property
GnomeProgram::default-icon after class was initialised Could not
create gnome accelerators directory `/home/ubeldiener/.gnome2/accels':
Permission denied

The same type of thing is happening with Thunderbird.

I know both were previously working fine, but I do not know what I could have installed or updated that broke both applications. I am running the latest version of Ubuntu using Unity.

Does anyone know how to fix this ?

I did try re-installation of both Firefox and Thunderbird but the error persists.

---

### Post by Edward_Diener on 2014-04-25
I solved this by looking at my hidden .gnome2 directory. The owner and group for the directory is 'root'. I changed the group to my own group and then both Firefox and Thunderbird could start correctly.

---


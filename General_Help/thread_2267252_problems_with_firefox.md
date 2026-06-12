---
title: "problems with firefox"
date: 2015-02-28
forum: General Help
---

### Post by piscvau on 2015-02-28
Xubuntu version 14.04; firefox 36.0 

here is what I get when I launch firefox from the terminal window

(process:3869): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised.

after these error messages firefox is launched.

May be as a consequence of this problem I cannot save bookmarks on my distant profile. I use 2 different profiles : one which is local, that is on the same machine as firefox. This profile works OK.
When I use a distant profile which is on a Synology server, I cannot save any bookmarks. 

Any hep would be welcomed.
piscvau

---

### Post by sandyd on 2015-02-28
> **piscvau said:**
> Xubuntu version 14.04; firefox 36.0 

here is what I get when I launch firefox from the terminal window

(process:3869): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(firefox:3869): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised.

after these error messages firefox is launched.

May be as a consequence of this problem I cannot save bookmarks on my distant profile. I use 2 different profiles : one which is local, that is on the same machine as firefox. This profile works OK.
When I use a distant profile which is on a Synology server, I cannot save any bookmarks. 

Any hep would be welcomed.
piscvau
Hi, how are you using the 'distant profile'?

---

### Post by piscvau on 2015-03-01
> **sandyd said:**
> Hi, how are you using the 'distant profile'?

I am not sure I understand the question. here is what I did: I created a new profile and chose to use existing file on the NAS.  Given that I launch Gigolo at session start and that I created a bookmark on the NAS directory, it works. 

I just migrated from Windows and I had the same usage on Windows XP and it worked fine. 

does this answer your question?
piscvau

---


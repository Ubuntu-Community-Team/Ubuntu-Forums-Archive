---
title: "Problems with Thunderbird in Ubuntu 14.04"
date: 2014-08-22
forum: General Help
---

### Post by Adam_Jacobs on 2014-08-22
I have just done a mostly clean reinstall to upgrade to Ubuntu 14.04. I say mostly because my home drive was on a separate partition, which I left as is.

Mostly, everything worked fine, but I'm having some problems with Thunderbird.

The problem is that is can be very slow to open messages, and sometimes it doesn't open them properly. Only part of the message is visible, and the background Thunderbird window is still showing through. This is making it close to unusable. 

I tried running Thunderbird from a terminal and writing the error messages to a log. This is what it shows when I start it up:

```
(process:11926): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(thunderbird:11926): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(thunderbird:11926): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(thunderbird:11926): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(thunderbird:11926): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised

```

And this is what it shows when I try to open a message and it displays it badly:

```
(thunderbird:11926): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.40.0/./gobject/gsignal.c:3408: signal name 'selection_changed' is invalid for instance '0x7fa13a311850' of type 'MaiAtkType3'
```

Any idea what might be going on here and how I can fix it?

Thanks
Adam

---

### Post by zombienerd1 on 2014-08-22
This error can be caused by bad ownership of files in any mozilla folders.  You'd have the same problems with firefox if you kept that folder as well.

You need to chown every file in directories you kept, and do it recursively.

Open a terminal, go to the thunderbird directory, and run the following command:

> sudo chown -R username:group *
username:group needs to be your information.

Hope this helps!

It might be worth it to do this from your home directory as a whole, and re-own all files to the new account from the re-load.  *Warning* be sure that any files don't need other ownership before doing that.

---

### Post by Adam_Jacobs on 2014-08-22
Thanks for that, but I'm not convinced that was the problem. I had a look in both my ~/.thunderbird and ~/.mozilla directories, and I couldn't find any of them that had unexpected ownership. Just to check, I tried doing chown on them, but without the sudo, figuring it would tell me that it didn't have permissions if anything had bad ownership. It didn't give me any errors, so I'm pretty sure I had ownership of everything anyway.

But in any case, the problem persists.

---

### Post by Adam_Jacobs on 2014-08-28
Bump?

---


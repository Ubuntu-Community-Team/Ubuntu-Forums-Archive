---
title: "Can I *require* an option using the rrsync perl script?"
date: 2015-01-22
forum: General Help
---

### Post by Mark_Ungrin on 2015-01-22
I have a bunch of unsecured machines roaming around in the wild (user-owned laptops). I back their work-related subdirectory up to a server using the rrsync perl script (see [http://www.guyrutenberg.com/2014/01/14/restricting-ssh-access-to-rsync/](http://www.guyrutenberg.com/2014/01/14/restricting-ssh-access-to-rsync/)).

Most big files (primary collected data) don't change once generated - some text documents do, but they are not that big, and storage is cheap. So I use the -b option, with --suffix set to "date -Iseconds" - I waste some space on multiple versions of documents being worked on, but if the user gets hit with an an encryption virus, the backups won't be overwritten.

The rrsync script has provision for editing it to block certain options (e.g. it's easy for me to specify that the user can't call the -b option), but I would like to *mandate* the -b and --suffix options, and I'm not sure how to do that. Any ideas?

---

### Post by TheFu on 2015-01-22
Don't think you can without recompiling the tool.

However, a few options to consider.
* if they use sudo for the backups, you can force allowed options in the sudoers file.
* setup an alias for rrsync that includes the option you want. Most users won't notice this has been added - make it easier for them and they will do it.
* write a tiny script that does exactly what you want with the minimal user interaction.

---

### Post by Mark_Ungrin on 2015-01-22
I think I understand - if I just ignore what the user submits and declare @opts[1] to include b and whatever else I want will that work (not able to log in from here or I'd try it now)...?

---

### Post by TheFu on 2015-01-22
Or just
alias rrsync='rsync -b '

If you need to run the non-alias version, use \rrsync

Of course, this alias must be system-wide ... or at least for the userids you want to override.

---


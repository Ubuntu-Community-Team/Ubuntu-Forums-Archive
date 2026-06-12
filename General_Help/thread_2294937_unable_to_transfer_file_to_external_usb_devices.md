---
title: "unable to transfer file to external usb devices"
date: 2015-09-14
forum: General Help
---

### Post by Nosphky on 2015-09-14
Suddenly today after 18 months or so with no problems, (on 14.04 Trusty with all updates), I cannot transfer a file onto an external USB drive or any usb key.  I've tried dragging/dropping, copy / paste, and 'save as' from an application.

Every time, an error message comes up " '/media/myname/devicename/filename' is not a valid location".

I can mount the devices and read files from them.  I also have some backup scripts which use rsync to back up files to the external drive and they still work fine.

Drag and drop worked fine a couple of days' ago and I haven't made any changes to the set-up since.  I've tried rebooting.

Any ideas what might have gone wrong, how to debug would be appreciated.

---

### Post by Nosphky on 2015-09-14
Problem solved.  The filename was defective.  I needed that file on a different machine so I had to get it on a usb stick.  I passed it from desktop to a portable via dropbox and had the same problem stuffing it into a usb stick from the portable.

So the fault was in the filename.  Somehow the filename.txt had gained a space after the .txt.  Once that space was deleted, all was ok

---

### Post by Bashing-om on 2015-09-14
Nosphky; Good deal .

Good sleuthing ! Pleased you provided the solution; stops us all from wondering.

[INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]it is the simple things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


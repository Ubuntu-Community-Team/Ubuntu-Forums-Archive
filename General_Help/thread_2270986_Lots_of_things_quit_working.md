---
title: "Lots of things quit working"
date: 2015-03-26
forum: General Help
---

### Post by RogerDavis on 2015-03-26
Ubuntu 14.04

I started up this morning and the following aren't working :

- Dropbox - won't start, white page icon (Reinstalled from terminal, now working, with all original content)

- VirtualBox - won't start, white page icon  (Reinstalled from terminal, now working, with all original content)

- Can't see Ubuntu Software Center on the drop down - (Got this back by reinstalling from Terminal)

- System Settings only shows "Personal" and "System", (two icons), instead of the many more that are normal.  I tried installing "system-settings" from Terminal, but it didn't fix the regular display, just brings up a different one when started from Terminal, and want's me to log into Ubuntu One.  It looks like it's
for a phone

- Software Update quit for a while on the desktop, but I dragged a new icon out from the drop downs, and it "seems" to be working, but not sure

- Mozilla Seamonkey is now demanding I need Adobe Flash for videos, where it was working fine before

- Terminal is acting odd, can't copy or paste into it.  The right click turns it gray down to where the cursor is, but no other action is possible.  It will run typed in commands ok.  The terminal icon is much different, a red "X", with a blue "T" superimposed.  The Terminal window is smaller.

How can I repair these?  Is the failure likely connected?

---

### Post by Mark Phelps on 2015-03-26
When things "used to work" but now suddenly, do not -- there are generally two causes of this:
1) Updates that replace the older working versions with newer, nonworking ones
2) Filesystem corruption on the SSD/HDD.

You didn't say anything about recent updates, so I'm going with the second.

Suggest you read through the linked article and run fsck: [http://www.maketecheasier.com/check-repair-filesystem-fsck-linux/]("http://www.maketecheasier.com/check-repair-filesystem-fsck-linux/")

---

### Post by RogerDavis on 2015-03-26
There were updates

Apparently I can't use fsck without unmounting the disk, then I can't call fsck unless I remount the disk, then I can't...

Also, either way, how do I repair System Settings and Terminal?

Thanks!

---

### Post by RogerDavis on 2015-03-26
OK, latest is :

FIXED - Dropbox - won't start, white page icon (Reinstalled from terminal, now working, with all original content)

FIXED - VirtualBox - won't start, white page icon (Reinstalled from terminal, now working, with all original content)

FIXED - Can't see Ubuntu Software Center on the drop down - (Got this back by reinstalling from Terminal)

**- System Settings only shows "Personal" and "System", (two icons), instead of the many more that are normal. I tried installing "system-settings" from Terminal, but it didn't fix the regular display, just brings up a different one when started from Terminal, and want's me to log into Ubuntu One. It looks like it's for a phone !!! **

FIXED - Software Update quit for a while on the desktop, but I dragged a new icon out from the drop downs, and it "seems" to be working, but not sure

FIXED - Mozilla Seamonkey is now demanding I need Adobe Flash for videos, where it was working fine before

FIXED - Terminal is acting odd, can't copy or paste into it. The right click turns it gray down to where the cursor is, but no other action is possible. It will run typed in commands ok. The terminal icon is much different, a red "X", with a blue "T" superimposed. The Terminal window is smaller.[/B]

** How can I repair these remaining problems?   If I go to the next LTS release, will it fix all the bold lines? **

---

### Post by RogerDavis on 2015-03-26
OK, all fixed...

---


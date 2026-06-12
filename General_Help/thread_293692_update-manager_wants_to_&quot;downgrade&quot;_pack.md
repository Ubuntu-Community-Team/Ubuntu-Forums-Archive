---
title: "update-manager wants to &quot;downgrade&quot; package created with dpkg-buildpackage"
date: 2006-11-05
forum: General Help
---

### Post by psyeye on 2006-11-05
Hi!


Since IMAP4 was removed from evolution-data-server, I rebuild it with "--enable-imap4".

Steps taken:
[LIST]
[*]modify debian/rules
[*]run dpkg-buildpackage -rfakeroot
[*]install resulting deb-files with dpkg -i
[/LIST]

This all worked well and I can again use my university's IMAP4 servers!

Downside: update-manager wants to downgrade these packages! What can I do to tell it that it's actually a "new version"?


Thanks for any hints, guides, links!

regards,
psyeye

---

### Post by TLE on 2006-12-06
Yeah you need to add some info that lets the system regard this as a upgrade. I do this as part of this [HOWTO]("http://ubuntuforums.org/showthread.php?t=242502"). You need to run the command
```
debchange -i
```
while being inside the source directory. This will open up a editor, now you can add some info if you want to but it should not be necessary, since it has already created the one line you need, in the case of my howto
```
metacity (1:2.14.5-0ubuntu2) dapper-updates; urgency=low
``` 
the 2 after ubuntu in 0ubuntu2 indicates that it is the second update to this version. So if everything is correct there should be a entry just below the one you have made that is named 1:2.14.5-0ubuntu1. Then just save and repackage just as you did, now it wont want to downgrade because it regards your package as a update to version 2.14.5. The only thing that can happen now is if there comes an entire new version in the repos, say 2.14.6, then you'll need to do this whole trick again.

Have fun with it

---


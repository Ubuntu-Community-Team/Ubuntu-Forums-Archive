---
title: "Rsync problem. Windows source Linux target"
date: 2015-07-22
forum: General Help
---

### Post by stephen67 on 2015-07-22
I had no problems with 12.04, but after upgrading to 14.04 I have had a lot of issues.

I run rsync under cygwin on a windows machine. The linux machine is my backup.

When the file on linux was created using a copy on windows explorer, future rsync runs perform as expected.

If the file on linux was create by rsync, future rsync runs copy the file again as though it had been changed.

Here is the samba .conf section

[photography]
	comment = Photography
	path = /big0/photography
	writeable = yes
;	browseable = yes
	guest ok = yes
        force user = stephen
        force group = stephen

Here is my rsync command (run on windows)

rsync -vz --progress --chmod=ugo=rwX --delete -r /cygdrive/e/photography/ //AVALON/photography

Any help is appreciated.

---

### Post by btindie on 2015-07-23
I think you may need to use the "--modify-window=1" option to rsync on windows to relax the modify time comparison.

---

### Post by stephen67 on 2015-07-23
Thank you!

I actually went with the --size-only directive since these are photography files.

All is well!

---


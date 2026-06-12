---
title: "File corruption when editing file on SMB mount."
date: 2007-10-11
forum: General Help
---

### Post by rio_hot on 2007-10-11
Hi all,

I am having some real trouble with file locking.
I'm using Feisty at work, while everybody else is using XP machines. We all share files (.doc .xls) on shared drives [Win 2000 Server].
I can access these files OK (with read/write access) via either using the "Connect to server... Windows Share" options or using "mount -f smbfs....".
However I never get a file lock.
When using Open Office, I can open a file, that someone else has open (editing), and edit/save myself. This causes file corruption. Also, people can open files I'm working on, with the same results.
I have tried setting the following:
/etc/openoffice/soffice.sh
FILE_LOCKING=yes
also
SAL_ENABLE_FILE_LOCKING=1
export SAL_ENABLE_FILE_LOCKING
and even
export STAR_PROFILE_LOCKING_DISABLED=1
in various combination, all with no effect.

Can anyone point out what I'm doing wrong.
Many many thanks...

Wayne

---


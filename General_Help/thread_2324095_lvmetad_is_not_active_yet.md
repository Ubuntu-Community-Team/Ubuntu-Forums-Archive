---
title: "lvmetad is not active yet"
date: 2016-05-10
forum: General Help
---

### Post by doogiekd on 2016-05-10
hi all,

i upgraded to ubuntu 16.04 and am getting the following message during boot:

lvmetad is not active yet
using direct activation during sysinit
/dev/mapper/ubuntu-vg-root: clean
346675/9691136 files

what does this message mean?
what can i do to correct this, if indeed. this is an error?

thanks!

---

### Post by rexdemon on 2016-05-25
I had the exact same problem
Found the solution here[[https://unix.stackexchange.com/questions/199164/error-run-lvm-lvmetad-socket-connect-failed-no-such-file-or-directory-but]](https://unix.stackexchange.com/questions/199164/error-run-lvm-lvmetad-socket-connect-failed-no-such-file-or-directory-but])

systemctl enable lvm2-lvmetad.service
systemctl enable lvm2-lvmetad.socket
systemctl start lvm2-lvmetad.service
systemctl start lvm2-lvmetad.socket

This worked for my LVM Ubuntu 16.04

---

### Post by joaodelsolar on 2016-05-26
I tested this procedure, but without any perceptive changes.

---

### Post by Sky_Dog on 2016-10-22
Hi guys,

did you resolved this issue? I am experiencing the same problem and the suggestion above didn't have any effect on my Ubuntu 16.04 :-(

Regards
S.

---


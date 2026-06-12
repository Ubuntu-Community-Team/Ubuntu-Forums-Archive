---
title: "Problem on booting"
date: 2006-08-14
forum: General Help
---

### Post by satimis on 2006-08-14
Hi folks,

Ubuntu-6.06-amd64

Freqently Firefox crashed and exited Gnome desktop to login page OR hung on screen forcing me to force-reset PC.

Now problem encounted on booting, popup warning to run "fsck".  

I did;
# fsck /dev/hda
twice after login as root.

Each time I aswsered many questions and ended up with;

"fsck.ext2: e2fsck_read_bitmap: illegal bitmap block (15) for Root"


On reboot with "shutdown -r now" it was impossble booting straight to login screen.  Each time requesting to run "fsck".  After running it the same problem remained.  However if ignoring the warning and pressing [Ctrl]+D, booting contiued to login page.

Please advise how to fix this problem.  TIA

B.R.
satimis

---


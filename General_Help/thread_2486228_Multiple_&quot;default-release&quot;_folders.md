---
title: "Multiple &quot;default-release&quot; folders"
date: 2023-04-23
forum: General Help
---

### Post by lou6 on 2023-04-23
I noticed today that I have 2 default release folders in my .mozilla folder.  How to know which is the active one for restoring Firerfox data (if I need to do that).  Thanks for all answers...

---

### Post by #&amp;thj^% on 2023-04-23
Will this help? Change "me to your user name"
```
ls -la '/home/me/.mozilla/firefox' 
```
```
otal 136
drwx------ 14 me me  16 Apr 17 17:44  .
drwx------  4 me me   4 Apr 13 19:06  ..
drwxrwxr-x  2 me me   3 Apr 13 19:10  20wt7wl9.default
drwxrwxr-x  2 me me   3 Apr 13 19:10  49s5ux6q.default
drwx------  2 me me   3 Apr 13 19:06  9hcszszr.default
drwxrwxr-x 14 me me  52 Apr 13 19:10  a3c4mhkk.default-release
drwx------  3 me me  10 Apr 16 10:59 'Crash Reports'
-rw-r--r--  1 me me  64 Feb 12 11:37  installs.ini
drwxrwxr-x 15 me me  57 Apr 23 13:27  kxwpdjsn.default-release-1
drwxrwxr-x  2 me me   3 Apr 13 19:10  lfacv4tn.default
drwx------ 10 me me  41 Apr 13 19:08  lfiwx9g8.default-release
drwxrwxr-x 13 me me  49 Apr 13 19:10  o9snwflo.default-release-1
drwx------  2 me me   2 Apr 13 19:06 'Pending Pings'
-rw-r--r--  1 me me 341 Feb 12 11:37  profiles.ini
drwxrwxr-x 11 me me  47 Apr 13 19:10  ue6ty3yz.default-release
drwxrwxr-x 12 me me  44 Apr 13 19:10  zzp8i098.default-release


```
Dates show true for me
EDIT: Also you can run "stat" against them to possibly help IE:
```
stat '/home/me/.mozilla/firefox/a3c4mhkk.default-release' 
  File: /home/me/.mozilla/firefox/a3c4mhkk.default-release
  Size: 52        	Blocks: 18         IO Block: 3584   directory
Device: 0,40	Inode: 70556       Links: 14
Access: (0775/drwxrwxr-x)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2023-04-23 09:00:16.075207919 -0600
Modify: 2023-04-13 19:10:32.919654297 -0600
Change: 2023-04-13 19:10:32.919654297 -0600
 Birth: 2023-04-13 19:10:30.463659290 -0600

```
I just happened to know that was the one I needed

---

### Post by lou6 on 2023-04-23
Thank you! that does it.

---

### Post by mIk3_08 on 2023-04-23
> **lou6 said:**
> Thank you! that does it.
If your issue was already been answered you can mark this thread as Solve.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---


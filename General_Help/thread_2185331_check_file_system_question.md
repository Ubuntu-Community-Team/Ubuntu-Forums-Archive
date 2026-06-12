---
title: "check file system question"
date: 2013-11-02
forum: General Help
---

### Post by aaronmarsh632 on 2013-11-02
Hi,

I think this should be a simple answer I just cant find it, I'm running an older ubuntu install on 1 of my PC's and in the disk utility I have the 'Check File System' option but on the new ubuntu I cant find that button, the disk utility is completely different and I just cant find it, please can any one help me out?

Thanks

---

### Post by aaronmarsh632 on 2013-11-09
Bump,

Please does anyone know the answer to this? I dont think this option would have been removed from the disk utility.

---

### Post by ian-weisser on 2013-11-09
The command is **fsck**. See the manpage.
Do *NOT* run fsck on a mounted filesystem!

Several ways to check how many reboots until the next check, and how to force a check at the next boot are detailed at [http://askubuntu.com/questions/26141/how-do-i-find-out-if-there-will-be-a-fsck-during-the-next-boot](http://askubuntu.com/questions/26141/how-do-i-find-out-if-there-will-be-a-fsck-during-the-next-boot)

---


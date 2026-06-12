---
title: "Problem with LVM and ext3"
date: 2007-10-18
forum: General Help
---

### Post by pepertje on 2007-10-18
Hi,

I had this problem yesterday with installing LVM on my home server.

It's an Ubuntu 6.06 LTS server on wich I run samba for file sharing.
I added a new HD yesterday and wanted to setup an LVM with two 320Gb disks.

I first tried using Webmin to set it up, making the group and then formatting it as ext3. It all worked fine untill I had copied a certain amount of files on the disk. Then it gave an error and remounted as read only.
My first tought was that I did something wrong with setting it up, so I tried it manually in console, with the same result as before: remounting as read-only after giving an error.
So I tried formatting it as reiserfs since the howto I was using used reiserfs. Again, the same result.
At this point I read that there was a bug in 6.10 and 7.04 so I did the fix they gave in the howto and tried it again using ext3. And again the same result.

In a last attempt I did it all over again using ext2 and that worked just fine.

Does anybody know why this didn't work with ext3 or reiserfs, but did with ext2? It's working now so I won't change it, but I just like to know what went wrong.

---


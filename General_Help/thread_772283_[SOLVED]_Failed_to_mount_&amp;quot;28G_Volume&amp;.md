---
title: "[SOLVED] Failed to mount &amp;quot;28G Volume&amp;quot;."
date: 2008-04-28
forum: General Help
---

### Post by Zeotronic on 2008-04-28
What a time to have problems... after the release of 8.04... that *is* why I'm having problems though.

In gparted, I have been getting the following error:
> org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result).
At first I had thought I had encountered this before, that I had to install the tools to handle NTFS, but as anyone that understands that line can tell, I was wrong. I don't understand that line, so if someone could help me? Also, it may or may not be related, but Xubuntu (as in my Xubuntu) isn't mounting my other partitions... before, in another install of 8.04, it would always mounth the other partitions... and in 7.10 I dont recall ever having problems related to it. Presently, Xubuntu only seems to be mounting external memory devices, not the other partitions on my twin hard-drives.

---

### Post by p3tris on 2008-05-06
I have excactly the same problem. Only i had the partition backed up so i used Gparted and format it and made it ex3, guess what, it won't mount. Then i made it fat32, ex2, tried everything. I just wont mount!

I use Xubuntu 8.04 (although in ubuntu 8.04 i tried for a while it mounted perfect and it was ntfs, so i don't know if it's a XUBUNTU problem)

Thanks for any help coming...

*found the problem i think:

sudo mousepad /etc/PolicyKit/PolicyKit.conf 
and insert into section <config> permission for all users to mount all disks
```
<match action="org.freedesktop.hal.storage.*">
    <return result="yes"/>
</match>
```

i found it here ---> [http://www.linuxquestions.org/questions/linux-newbie-8/acces-to-partiton-612726/](http://www.linuxquestions.org/questions/linux-newbie-8/acces-to-partiton-612726/) thanks to rev918

---


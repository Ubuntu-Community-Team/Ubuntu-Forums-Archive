---
title: "VMWare access a partition"
date: 2007-02-22
forum: General Help
---

### Post by nzflew on 2007-02-22
I have Windows XP set up under a VMWare Server on Ubuntu Edgy. I am trying to access a partition from the Windows XP under VMWare, every time I try to add it as a partition (or disk) I get a permissions error. I can add a removeable hard drive fine though. Can anyone shed some light on this for me. Do I need to add permissions for VMWare to the partition that the WinXP INstallation is trying to access. Any help would be appreciated.

---

### Post by groova on 2007-03-05
I don't think that will ever work, because it would make the whole idea of using virtualisation sort of pointless.

What you can do is install a samba-server on your Ubuntu (check this topic for instructions [http://www.ubuntuforums.org/showthread.php?t=296668&highlight=vmware+samba]("http://www.ubuntuforums.org/showthread.php?t=296668&highlight=vmware+samba")) . Worked great for me. :)

---

### Post by nzflew on 2007-03-08
Thanks for that, the solution you provided worked exactly the way I wanted it to.

Mark

---


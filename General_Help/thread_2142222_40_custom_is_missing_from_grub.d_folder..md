---
title: "40_custom is missing from grub.d folder."
date: 2013-05-05
forum: General Help
---

### Post by DragonFart on 2013-05-05
hi im a noob and in need of some help pls.

earlier i tried to install clonezilla to a new ext2 partition that i made alongside ElementaryOS partition. i followed the tutorials here ([http://clonezilla.org/livehd.php](http://clonezilla.org/livehd.php)) updated the grub, rebooted and the clonezilla wasnt in the list. so i logged into elemnetary OS and went to grub.d folder and the 40_custom file that was there earlier gone AWOL! how do i get back the file? im using grub customizer btw.

grub version: 1.99-21ubuntu3.9

thanks :)
p/s: i did use the "search" to look for similar questions before posting this but there was none.


here's a screenshot of the grub.d folder.
[IMG]http://i.imgur.com/BI7a41Q.png?1[/IMG]

---

### Post by dino99 on 2013-05-05
well, in case you want something "stable", avoid using "exotic" package(s)/howto(s), follow the genuine ubuntu way.
so purge the third parties and grub* too, then reinstall grub-pc & grub-common

more info with the link below

---


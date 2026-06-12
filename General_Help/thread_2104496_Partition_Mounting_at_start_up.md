---
title: "Partition Mounting at start up"
date: 2013-01-13
forum: General Help
---

### Post by sadanandan on 2013-01-13
Hello, I need help to mount my three partitions at start up.
I added"/usr/bin/udisks --mount /dev/disk/by-uuid/0AD475D7D475C58B" this command in the start up applications list. It did work for one partition. But when I added a second partition"/usr/bin/udisks --mount /dev/disk/by-uuid/BA6CF9D66CF98D7F" and restarted, the first one disappeared from the start up list and only the second one mounted. 

Then I modified the command to include all three partitions in one command"/usr/bin/udisks --mount /dev/disk/by-uuid/0AD475D7D475C58B;/usr/bin/udisks --mount /dev/disk/by-uuid/BA6CF9D66CF98D7F;/usr/bin/udisks --mount /dev/disk/by-uuid/374CC66754A0C28B" 
With this command in the start up list, only the last partition mount.

Any help??

---

### Post by ibjsb4 on 2013-01-13
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+auto+mount+partition+at+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+auto+mount+partition+at+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by Morbius1 on 2013-01-13
I have been able to reproduce this error. It's quite odd really. It's not a question of it not running it literally removes the previous udisk startup application.

I tried your idea of having them all in one startup script but used " && " instead of a ";" and it worked. Try the same with yours:

/usr/bin/udisks --mount  /dev/disk/by-uuid/0AD475D7D475C58B [COLOR=Blue]**&&**[/COLOR] /usr/bin/udisks --mount  /dev/disk/by-uuid/BA6CF9D66CF98D7F [COLOR=Blue]**&&**[/COLOR] /usr/bin/udisks --mount  /dev/disk/by-uuid/374CC66754A0C28B

---

### Post by sadanandan on 2013-01-13
**ibjsb4**
I am not very confident about editing fstab file. That is why I chose the 'start up applications'way. I followed the first link you mentioned.
 
I modified the command as **Morbius1** suggested with '&&' instead of ';' But it is not working for me. I tried with and without 'space' before and after '&&'. In both cases only the last mentioned partition mounted.

---


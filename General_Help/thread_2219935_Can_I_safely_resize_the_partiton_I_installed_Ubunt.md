---
title: "Can I safely resize the partiton I installed Ubuntu onto?"
date: 2014-04-26
forum: General Help
---

### Post by randypfau on 2014-04-26
When I formated my drive during ubuntu installation I made an ext4 primary which I installed the ubuntu filesystem onto and a swap partion... my ext4 partion is approx 300gb in size... id like to cut it into 2 partitions... a 40gb and a 260gb... is this possible to do safely? if so how would I go about doing such via command line?

---

### Post by david98 on 2014-04-26
As far as am aware you can't resize a partition through the command line because the partition would be mounted. The best way to resize the partition would be to use a live disk/usb and use gparted to resize the partition. I have done this many time's safely but would recommend backing up all data before you start messing around with partitions in case you make a mistake.

---

### Post by LastDino on 2014-04-26
I'm not sure but if your / partition is the one you want to re-size (which seems to be the case), it will cause problems. Best way to do this is take a backup and do the procedure David suggested, if it doesn't work then go for fresh install.

---

### Post by ibjsb4 on 2014-04-26
You need to use gparted, which is on the ubuntu live dvd.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

[http://gparted.org/display-doc.php?name=help-manual#gparted-resize-partition](http://gparted.org/display-doc.php?name=help-manual#gparted-resize-partition)

---


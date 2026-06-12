---
title: "Renumbering partitions"
date: 2007-12-10
forum: General Help
---

### Post by achidlow on 2007-12-10
I have a secondary hard disk, 200GB, which has two partitions on it, /dev/sdb1 which is NTFS and /dev/sdb2 which is ext3, im moving my files off sdb1 and onto sdb2 so i can delete sdb1 and make it take up the whole disk. but sdb2 is actually before sdb1, but i want it to be called sdb1 cause well i like things to be nice and in order :D. so, to do this, can i just (once ive deleted partition sdb1 and resized sdb2 to the whole disk) use fdisk to delete the partition, and recreate the same partition but name it sdb1?

---

### Post by geirha on 2007-12-10
I think the result of that is undefined (though I don't know for sure). Why not just make a new partition at the start of the drive (which I believe will be called sdb1). Then move the files "back" to sdb1 ... cumbersome and time consuming, I know.

---

### Post by achidlow on 2007-12-10
sigh i was hoping it didnt have to come to that... hmmm well its not like ill be damaging any data right? ill give it a shot and if worst comes to worst use one of the many file recovery programs out there to retrieve the files and/or the partition. itll be an adventure lol. itd be nice if it works, yes?

---


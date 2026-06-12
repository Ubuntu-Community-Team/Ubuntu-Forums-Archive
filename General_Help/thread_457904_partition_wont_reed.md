---
title: "partition wont reed"
date: 2007-05-29
forum: General Help
---

### Post by hessiess on 2007-05-29
when i boot ubuntu it ses that the partition is full, but in windows it ses that the linux partition is 0 bytes? healp plz;)
carnt even get to a comand line

---

### Post by hessiess on 2007-05-29
bump

---

### Post by hessiess on 2007-05-29
bump

---

### Post by blacksadness on 2007-05-29
can you give more info? it it's the ubuntu partition windows will always see it as 0 bytes, you could install an ext3 read write software for windows if you need to.. but please give out more info about the drive specs.. it could be just really full and you need to empty some stuff..

---

### Post by hessiess on 2007-05-29
i have ext3 driver on windows, outherwise i wouldent have been able to reed the partition its 10gb partition windows ses its a 0 gb partition. it was nilly full so that may be the problem. is there a scandisk program that can be run from recovery mode?

the gui loads so far then it givs an error mesage about the partition may be full, then puts me on a comand line that dosant do anything. i can type stuff, but it dosent do anything.

i hibonated windows then booted ubuntu. only thing i can thinc of is if hibonating windows crupted the file system, althow i have dun this befor without problems. i only have internet in windows

---

### Post by blacksadness on 2007-05-29
oh, i remember that happening to me once back when i had windows, go in ubuntu recovery mode from the boot loader and do fsck.ext3 /dev/hdx or sdx whatever your drive is and then do an rm -rf /var/cache/apt/archives to free up some space if its' full.. not that you will have to unmount the drive before scanning (umount /)..
good luck

---

### Post by hessiess on 2007-05-31
thx:) its working again

---


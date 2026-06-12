---
title: "disk assignment /dev/sd*"
date: 2013-07-09
forum: General Help
---

### Post by Ceiber Boy on 2013-07-09
Ive writttern a small sctipt automating a truecrypt process, however it relies on /dev/sda, /dev/sdb and /dev/sdc maintaining these assignments.

(what happens is a & b are small by todays standards and both are backed up to c.  a is the system disk, b & c are truecrypt voluems)

Question: is their anything that would cause these asignments to change, and rhus cause my script to stop working?

---

### Post by Ceiber Boy on 2013-07-09
Ive writttern a small sctipt automating a truecrypt process, however it relies on /dev/sda, /dev/sdb and /dev/sdc maintaining these assignments.

(what happens is a & b are small by todays standards and both are backed up to c.  a is the system disk, b & c are truecrypt voluems)

Question: is their anything that would cause these asignments to change, and rhus cause my script to stop working?

---

### Post by dannyboy79 on 2013-07-09
yes, they could change if you install a new hard drive or change connections to ide/sata ports on your motherboard. I would suggest you use the hard drive UUID, those never change, EVER.

---

### Post by Ceiber Boy on 2013-07-09
Thank you, that is an excelant idea. I'll have a google lots to see hhow to implement this approach in to script.

---

### Post by oldfred on 2013-07-09
Threads merged.
Please do not create duplicate threads on same topic.

---


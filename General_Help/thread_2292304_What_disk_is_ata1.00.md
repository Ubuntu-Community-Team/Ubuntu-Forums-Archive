---
title: "What disk is ata1.00 ?"
date: 2015-08-26
forum: General Help
---

### Post by georgesgiralt on 2015-08-26
Hello !
My logs are full of lines like this one : 
**ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded**
And I can't find which physical device it relates to ? 
How could I find it ?
(I tried all my knowledge but to no avail, this is why I ask for help)
Many thanks in advance for your help !

---

### Post by georgesgiralt on 2015-08-26
Hello !
My logs are full of lines like this one : 
**ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded**
And I can't find which physical device it relates to ? 
How could I find it ?
(I tried all my knowledge but to no avail, this is why I ask for help)
Many thanks in advance for your help !

---

### Post by oldfred on 2015-08-27
Duplicate threads merged. Please do not create duplicate threads on same topic. 
We all are volunteers and do not need to spend time answering a question that may then be already solved in another thread.

Is this what you want?
       sudo lshw -C Disk -short 
    
Lots of detail:
 sudo lshw -class disk

sudo apt-get install udisks
udisks --dump

---

### Post by georgesgiralt on 2015-08-27
Hello OldFred,
I'm sorry for the duplicate. First time I posted I got an SQL related error embedded in a WEB server page error and my post did not show. So I hit back button on my browser and tried posting again. This time, the post showed as it should.
As per the informations you gave me, I tried all of them already. Alas nowhere is really found the "ata1.00" correspondence with one of the disks.

---

### Post by grahammechanical on 2015-08-27
ATA1 might not be referring to any physical device but to an interface. Do you have an IDE hard drive attached? ATA1 = version 1 of the interface standard. There is also an ATA2 as well as ATA5 & ATA6. 

[https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

Regards.

---

### Post by georgesgiralt on 2015-08-27
No I don't. 
3 SATA drives on one and the same chip which has 4 ports.

---


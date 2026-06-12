---
title: "installing"
date: 2008-04-27
forum: General Help
---

### Post by regdabs on 2008-04-27
I started installing 8.04 a little while ago, and was going fine for the first 3 steps.  While in the partition manager I was using manual setup because I already have a partition to install Ubuntu onto.  I got a list of the partitions that I have and selected the one that I wanted to use.  Got a message stating "no root file system has been defined".  Select edit and get a list of options to select from and not sure which I should be using.  Where do I go from here?

---

### Post by smoker on 2008-04-27
you need a 'root' partition, this is where ubuntu will be installed. root is designated by the  / so in the 'edit partition' process of the install, make sure you enter the  /  relevant to the partition where you want ubuntu installed, you will also have to designate a 'swap' partition as well (usually double your ram in size),

best of luck

---

### Post by regdabs on 2008-04-27
the only options that I have under edit partition are:

Ext 3 journaling file system
Ext 2 file system
reiserFS journaling file system
XFS journaling file system
FAT 16 file system
FAT 32 file system
Swap Area
do not use the partition

Thanks again

---

### Post by smoker on 2008-04-27
> **regdabs said:**
> the only options that I have under edit partition are:

Ext 3 journaling file system
Ext 2 file system
reiserFS journaling file system
XFS journaling file system
FAT 16 file system
FAT 32 file system
Swap Area
do not use the partition

Thanks again

not there, that is for the formatting options. if i remember (off-hand), there is a dropdown box below that section on the partitioner, and if you click, you'll have options like, eg, / , Home , Boot , Usr , etc. you are looking to opt for  /  here.

---

### Post by regdabs on 2008-04-27
Nothing there that I can see, the only active boxes below the list of partitions are 
edit partition
delete paratition
and undo changes to paratition

nothing else there unless I am totally in the wrong place.

---

### Post by smoker on 2008-04-27
highlight the partition you want, then click 'edit partition' and you should have the choices,

---

### Post by regdabs on 2008-04-27
that what I did and the choices I listed in the earlier reply are the ones that show up.

---

### Post by smoker on 2008-04-27
hmm, i'm assuming you are using the live-cd disk to install?

anyway, there is a good guide here that may help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

there are other info topics on the left page of the above link, so hopefully this will explain better than i can!

best of luck

---

### Post by smoker on 2008-04-27
hmm, i'm assuming you are using the live-cd disk to install?

anyway, there is a good guide here that may help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

there are other info topics on the left page of the above link, so hopefully this will explain better than i can!

best of luck

SORRY! about double post, don't know how that happened!

---

### Post by regdabs on 2008-04-27
Smoker thanks for your help.  I finally find the option you were talking about and as soon as I selected root /, the rest of the installation went real smooth.  I am up and running and it seem to be working great, even found my graphic card GeForce 8800 which I had been having trouble with in Freespire.  Thanks again.

---

### Post by smoker on 2008-04-27
glad you got it sorted, have fun, lol

---


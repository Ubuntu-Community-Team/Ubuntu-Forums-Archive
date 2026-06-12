---
title: "Wubi/ Vista Problem"
date: 2008-03-01
forum: General Help
---

### Post by savageman on 2008-03-01
I am new here but I have been trying to install Ubuntu on my external hard drive for a few days now. I have a 80gb internal drive and a WD 160gb external that I partitioned into two drives. I did this just to have Ubuntu on a separate partition.

Now I have gone through regular installation through live cd numerous times at it always fails. So I tried numerous versions of Wubi and all failed with the same message.

I have my drives set up as so:
C(internal): 80gb
E(external):130gb
F(external):30gb

Both E and F are on the same external. Now I want Ubuntu installed on the 30gb external (F). I have tried so 4-5 times installing wubi from version 7.04-8.04Rev 444.

It installs fine but when i reboot and my computer wants to know which OS I want I choose Ubuntu. The next screen pops up and says Windows boot error. 

Cannot find \ubuntu\winboot\wubildr.mbr  
Status: 0xc000000e

Once I log back into vista i check and that file is there on my F drive where it should be.

Now I have no clue why ubuntu hates my laptop and why I can't install it. Anyone have any answers or can push me in the right direction.

System specs:
Vista home premium 
1.83ghz T2400
1gb mem
32-bit
Dell lat d620

thanks

---

### Post by ago on 2008-03-01
prova a copiare i files wubildr* su tutti i drives.

---

### Post by savageman on 2008-03-01
I am sorry I don't understand what you want. 

> prova a copiare i files wubildr* su tutti i drives.

Can you repeat it again?

---

### Post by ago on 2008-03-01
ops sorry posted while chatting in italian and got mixed up...

"try copying wubildr* files on all drives"

---

### Post by savageman on 2008-03-01
That did not work I tried putting the whole directory tree in all drives
     Ex. ubuntu\winboot\ then all wubildr files

that didn't work so I just put the wubildr files in all the drives without the folders and that didn't work.

any more ideas?

Oh and I did try to install it on other drive (E) and same problem occured

---

### Post by savageman on 2008-03-01
Just a side note this post has the screen image that I get [http://ubuntuforums.org/showthread.php?t=658612]("http://ubuntuforums.org/showthread.php?t=658612")

The suggestion to fix this was to run a windows iso repair?

---

### Post by ago on 2008-03-02
Try to debug/fix using EasyBCD

---


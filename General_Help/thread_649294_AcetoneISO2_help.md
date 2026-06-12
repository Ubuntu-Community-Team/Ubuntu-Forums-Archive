---
title: "AcetoneISO2 help"
date: 2007-12-24
forum: General Help
---

### Post by UK-Wobbie on 2007-12-24
I am using the backup CD tool on AcetoneISO2 and when i click on the tool it says you can burn the .bin file with "Burn TOC utility" But i can not see any Burn TOC utility in AcetoneISO2.

Do any one know where it is? 

Thanks :)

---

### Post by disturbedite on 2007-12-24
why don't you just use a burning program to burn it?  like k3b...

but yeah, i don't see one either.

---

### Post by rabid9797 on 2007-12-24
im not sure what to tell you, there doesn't seem to be a TOC utility or anything related to it in the repo's, maybe its just a feature you are missing in acetone?

anyways, if you can't figure that out, you could always try using k3b (located in the repos), its another cd/dvd burning app, it can burn image files as well, and its very easy to use

---

### Post by bulletxt on 2007-12-24
I'm sorry that qdialog  is outdated I actually forgot to update it. We removed all burning functions for a simple reason: we will completely write from scratch burning tools so AcetoneISO2 will be able to make data cd , copy cd ecc making it the independent DE burning tool! I have allready corrected the message in SVN.

however if you have allready created the backup *.bin and *toc of the cd-audio, I'll tell you how to burn it from a shell with one fast command:

 cdrdao write namefile.toc

you can possibly add other options like speed write but this method should just work out of the box!

---

### Post by UK-Wobbie on 2007-12-29
> **bulletxt said:**
> I'm sorry that qdialog  is outdated I actually forgot to update it. We removed all burning functions for a simple reason: we will completely write from scratch burning tools so AcetoneISO2 will be able to make data cd , copy cd ecc making it the independent DE burning tool! I have allready corrected the message in SVN.

however if you have allready created the backup *.bin and *toc of the cd-audio, I'll tell you how to burn it from a shell with one fast command:

 cdrdao write namefile.toc

you can possibly add other options like speed write but this method should just work out of the box!

Thanks :)
I was going to give it a go and see what it's like.

---


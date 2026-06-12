---
title: "Encrypting HD how?"
date: 2007-10-20
forum: General Help
---

### Post by pluisr on 2007-10-20
Hi!

Can anyone tell about a tutorial or a how-to that shows step by step how to encript the HD with Ubuntu?

Which is the best option to encript with Ubuntu?

Thanks!!

---

### Post by Page on 2007-10-20
IIRC you have to configure that during a new Gutsy install.

I'm not sure it can be done for a system that was upgraded from Feisty.

---

### Post by bodhi.zazen on 2007-10-20
See if these links help :

[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)
	[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

			[http://www.debian-administration.org/articles/469](http://www.debian-administration.org/articles/469)

Note: Encrypting a partition is destructive, ie it formats (over writes) the data.

FYI: You can encrypt / at installation with the Alternate CD

---

### Post by meastp on 2007-10-20
Is there an easy way to put the passphrase on an usb-stick? If this usb-stick is not present at boot, one would have to type in the passphrase manually, but if it is present, the computer will get the passphrase from the usb-stick.

---

### Post by pluisr on 2007-10-25
> **bodhi.zazen said:**
> See if these links help :

[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)
	[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

			[http://www.debian-administration.org/articles/469](http://www.debian-administration.org/articles/469)

Note: Encrypting a partition is destructive, ie it formats (over writes) the data.

FYI: You can encrypt / at installation with the Alternate CD

Many Thanks Bodhi

would this work in gutsy?  :confused:

How do I do it with the alternate CD?

consider  i am a Beginner please!! :(

---

### Post by honeydew on 2007-10-25
boot up with the alternate CD.. select the text based installation.. follow instructions/defaults are usually fine(except for locale settings of course).  Then when you get to the partition creator.. select the guided disk encryption.   after that continue installation as normal.

---

### Post by pluisr on 2007-10-27
Many Thanks! got it,

But....Is it possible to keep the Windows XP on another partition with the alternate CD?  (Just in case) 8-[

---

### Post by bodhi.zazen on 2007-10-27
> **pluisr said:**
> Many Thanks! got it,

But....Is it possible to keep the Windows XP on another partition with the alternate CD?  (Just in case) 8-[

Yes it should be, just be sure to review the partitioning (manually)

---


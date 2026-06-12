---
title: "Writing ext3 in Windows vs. writing ntfs in Linux"
date: 2007-06-22
forum: General Help
---

### Post by vexorian on 2007-06-22
The other week when my windows got infested with a virus that kept itself in "Documents and settings" and me figuring out that windows' recovery console  can't access that folder for whatever lame reason you can think of, I noticed that I could really use some way to write to windows' partition from Linux.

So I got to ask which of these alternatives is the most stable?

---

### Post by tgoose on 2007-06-22
I don't think using ext3 as the system partition is possible under Windows (although it is possible to read and write ext3.) NTFS read-write support has been fine in Ubuntu for me since the last update, so out of the two options that's probably the better.

Have you considered FAT32, though? That's perfectly supported by both, although perhaps doesn't perform so well.

---

### Post by arsenic23 on 2007-06-22
For manually fixing windows error and viruses you might find [Bart PE]("http://www.nu2.nu/pebuilder/") more usefull then your windows disk.

---

### Post by vexorian on 2007-06-22
Yeah well NTFS write support should be fine, afterall my only bad experience with NTFS on Linux was when I hybernated windows and then I loaded the windows partition from vmware(or was it the free alternative? I don't remember the name) and then I could solve the issue by just moving the files to another partition and formatting the damaged one.

I guess I could just keep ntfs write disabled until it is needed it is just a checkbox in ntfs-conf anyways...

And Fat32 is very bad for a system partition in my opinion.

Thanks.

Arsenic: Although that is sure interesting, is it legal?

---

### Post by arsenic23 on 2007-06-22
> **vexorian said:**
> Arsenic: Although that is sure interesting, is it legal?

You know, I've never once asked myself that question.  This seems like an answer: 
> It is important to remember that BartPE is not a free replacement for any of the Windows editions listed above. Since its creation and use implies leveraging fully licensed version of the operating system, you must still be a rightful owner of corresponding Microsoft product.

Also look [here]("http://aplawrence.com/Words2005/2005_07_11.html").

---


---
title: "Undo RM -r"
date: 2008-07-04
forum: General Help
---

### Post by rykel on 2008-07-04
Hi,

I deleted some files on a NTFS partition in the following manner:

**[INDENT]sudo rm -r /FOLDER[/INDENT]**

Is there a way I could undo or recover what was removed?

Thanks for advising.

---

### Post by ibutho on 2008-07-04
As far as I know, you cannot reverse "rm -r" and thats why its advised to use it very carefully. If the data was very important, you could send your disk to experts who can try to recover it for you.

---

### Post by bryncoles on 2008-07-04
you could try installing testdisk - its in the repo's and here [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk). ive used it to recover photos before and it works quite well at that. im no expert though, so i cant give much advice and you might be better going to a professional, as ibutho suggests. 

good luck though

---

### Post by hyper_ch on 2008-07-04
and for the future: Make regular backups of your data ;)

---

### Post by justleen on 2008-07-04
testdisk or spinrite.. spinrite is closed source, so you'd have to buy it...

---

### Post by sonicb00m on 2008-07-04
getdataback for ntfs for Windows will help you.

---

### Post by rykel on 2008-07-05
Thanks for all the help, mates... I must say, RM -r is POWERFUL.   :)

---

### Post by kevdog on 2008-07-05
There was a tutorial a ways back that when you did the rm command, it moved the data to the user trashcan.  That way you could recover the data if needed.  I think the tutorial may be in the Tutorials and Tips section.  If not, let me know.

---

### Post by tysont on 2012-06-12
Just ran into this myself, give this [method of undoing rm -R a shot]("http://www.etherealbits.com/2012/06/the-perl-script-that-may-save-your-life/").  Worked for me.  Good luck!

---

### Post by oldos2er on 2012-06-12
Please don't bump old threads.

---


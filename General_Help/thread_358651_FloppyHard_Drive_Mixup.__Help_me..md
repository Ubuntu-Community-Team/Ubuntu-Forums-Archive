---
title: "Floppy/Hard Drive Mixup.  Help me."
date: 2007-02-11
forum: General Help
---

### Post by caecusum on 2007-02-11
This is my very first experience with Ubuntu, and one of my first with Linux.  I've managed to get a great little system set up save for one problem:

When I browse my computer using the file browser I see Filesystem, CD-RW/DVD+R Drive, and Floppy 1.  The catch here being that I don't have a floppy drive.  Easy, just remove it you say?  Well I'm a little afraid to do that, you see, when I right click the Floppy Drive icon and go to properties it shows as having 211GB of free space - my entire hard drive!  What does this mean?  This can't be right.  Somebody help me out here, please!  Why does Ubuntu think my hard disk is a removable floppy?

---

### Post by kerry_s on 2007-02-11
No, your miss understanding the properties. What it's showing is the properties for the floppy folder icon which is on your HD, the properties for a floppy will only show if the floppy is mounted, other wise it's just a icon.

---

### Post by caecusum on 2007-02-11
Thanks for the quick response.  So just because I'm obsessive compulsive, is there a way to remove the floppy icon so it stops bother me? :)  I tried just deleting it and received an error message "operation not permitted"

---

### Post by kerry_s on 2007-02-11
You got to do it as root. gksu nautilus /media or in terminal> sudo rm /media/floppy

becareful using root, you'll have the power to mess up your system. :)

---


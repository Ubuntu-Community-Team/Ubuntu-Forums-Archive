---
title: "Couple of questions about partitioing."
date: 2007-05-09
forum: General Help
---

### Post by Crafty Kisses on 2007-05-09
First off I don't have my Windows Installer Disc, so should Partition Magic 8.0 do the job? And secondly when I partition should I still be able to access my C drive files. (Im a Noob I know)

---

### Post by Turellius on 2007-05-09
I am a bit confused as to your exact intentions, so I will first answer your questions.  Yes, Partition Magic 8.0 can do all sorts of partitioning tricks including resizing partions.  Yes, you should still be able to see and access files on your Windows partition(C:).  Now I am going to assume that you plan to install a version of Ubuntu and re-answer your questions.  You don't need to use Partition Magic as Ubuntu is a Live CD that you can boot from and then install Ubuntu from there.  One of the steps is creating/assigning/resizing a partition on which to install Ubuntu.  Also, while almost certainly by default you will be able to access your Windows partition and read from it, writing to it requires some additional libraries.  I don't know the exact libraries, but a quick google search gave me the answer and if you get stuck you can always come back here.  Hope this helps.

---

### Post by merlinus on 2007-05-09
Just make sure when using the live cd partitioning to not let it use your entire hard drive!  You can select the manual option at that screen.

The ntfs-configuration tool wil allow you to read and write to ntfs-formatted partitions.  You will be able to get it from Applications/Add-Remove after installation.

-merlin

---


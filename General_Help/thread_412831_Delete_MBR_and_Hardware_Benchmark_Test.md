---
title: "Delete MBR and Hardware Benchmark Test"
date: 2007-04-18
forum: General Help
---

### Post by cyberia81 on 2007-04-18
Hi. I am taking donated systems at our school, refurbishing them if necessary, and giving them to students without computers at home. I am installing Edubuntu on them. As I am relatively new to Linux, I have two questions:

1) People that are donating computers want to know if I am going to delete the information on their hard drives (yes) and how. In the past when I was using Windows, I knew exactly what to do. What is the best way to ensure that everything has been removed, and how do I go about doing this? Or, is it sufficient enough to just delete the partition and install Edubuntu?

2) I searched for a program to test the computers before giving them to the students, but I was unable to find anything. Are there any benchmark programs out there to test the hardware? I want my student volunteers to be able to perform these tests on their own, which means they will need a program to run. They don't know enough about hardware to recognize a problem on their own yet.

Any help would be greatly appreciated. Thanks for reading!

---

### Post by moore.bryan on 2007-04-18
[I]for your #1, [http://www.linux-kurser.dk/secure_harddisk_eraser.html](http://www.linux-kurser.dk/secure_harddisk_eraser.html) doesn't look too difficult.

for #2, [http://www.tux.org/~mayer/linux/bmark.html](http://www.tux.org/~mayer/linux/bmark.html) looks like it might do the trick.

[/I]

---

### Post by milton1 on 2007-04-18
Reformatting and installing a new system is generally enough to clear the old data. Some may still be recoverable, but that will be the case no matter what you do. The only sure-fire way to prevent sensitive data recovery is to take a hammer to your hard drive. I would tell your donators that their data is being erased, but if they have any higher than normal concerns about data security, that they should remove or clean their hard drives before donating the system.

---

### Post by ajgreeny on 2007-04-18
If you and your donaters are really paranoid, have a look at *Darik's boot and nuke *which can be found at:-
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

It takes a long time to completely clear a disk, depending on the size, but will wipe it as clean as it is possible to do, short of the hammer job mentioned by milton1

---


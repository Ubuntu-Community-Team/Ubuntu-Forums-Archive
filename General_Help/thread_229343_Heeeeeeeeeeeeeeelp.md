---
title: "Heeeeeeeeeeeeeeelp"
date: 2006-08-04
forum: General Help
---

### Post by ubuntuubuntu on 2006-08-04
I wanted to install Ubuntu in my laptop which had only Windows XP. When using GParted, there was an error. I had only one partition (Windows). I asked GParted to resize this partition and create two other partitions. The other partitions were not created.
Now, my Windows partition filesystem is " unknown", and I can't use Windows.

CAN I RECOVER THIS PARTITION? PLEASE, HELP ME, I HAD LOTS OF IMPORTANT FILES ON THAT PARTITION!

---

### Post by wombat20 on 2006-08-04
Don't panic. (btw, heeeeeelp is not a very descriptive title)

It may be that the master boot record has been damaged as the install didn't complete.  Try booting from your windows CD and using the recovery console to do a "fixmbr" command.  Before you try installing ubuntu again make sure you back up everything you can't replace.

---

### Post by ubuntuubuntu on 2006-08-04
It didn't work. I still get the message "error loading operating system" when I turn the computer on. 
What can I do? Pleeease, help me!

---

### Post by Tomosaur on 2006-08-04
Unfortunately for you, I had this exact same problem. Even more unfortunately for you, my Windows installation was brand new, so when I realised I had to reinstall it, it wasn't a problem.

However, before you do anything rash, try out the Windows recovery CD again. I think there's a command called 'fixboot' or something, which should replace the files needed to boot windows.

---

### Post by Irony on 2006-08-04
Thats because GParted won't resize the Windows partition. Try this and then reinstall grub;

[http://ubuntuforums.org/showthread.php?p=1314739#post1314739](http://ubuntuforums.org/showthread.php?p=1314739#post1314739)

---


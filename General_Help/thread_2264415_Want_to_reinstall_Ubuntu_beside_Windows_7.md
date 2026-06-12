---
title: "Want to reinstall Ubuntu beside Windows 7"
date: 2015-02-07
forum: General Help
---

### Post by albaqui on 2015-02-07
Hi

i had 2 OS. Windows 7 and Ubuntu 13.10 side by side. On the start I used to choose windows7 or Ubuntu.
yesterday I accidentally uninstalled Ubuntu OS.
i did system restore but could not get back Ubuntu OS.
now I have Windows 7
i checked from computer management that it has 
C drive which has Windows7
F drive which has Ubuntu

Now, how can I renstall/recover Ubuntu OS like before from the Hard drive?
please reply to my email also: [email]albaqui@gmail.com[/email]

---

### Post by Mark Phelps on 2015-02-07
IF the "F" drive had Linux, the only way you could have installed was using WUBI -- as that installs INSIDE an existing Windows filesystem.

There is no way to "recover" a former WUBI installation once you have removed it.  Windows System Restore really only restores the Operating System and its support files; it does not restore user data or files.

You will have to install Ubuntu again using WUBI.

---

### Post by Bucky Ball on 2015-02-07
Just another note: neither 13.10 or WUBI are supported anymore. 13.10 reached end of life last April. I advise reinstalling using 14.04 LTS on a separate partition. See [here]("http://ubuntuforums.org/showthread.php?t=2229730") for some clues and let us know if you have any questions. ;)

---

### Post by albaqui on 2015-02-07
Thank you for giving helpful tips.
Now, what should I do since WUBI no more exist?
please tell me step by step since I am new in computer.
thanks.

---

### Post by albaqui on 2015-02-07
another post informed no more WUBI to install from hard drive. So what can I do? Can you tell me step by step. I am new in computer. Thanks.

---

### Post by albaqui on 2015-02-07
Hi
I noticed F drive empty (partition F has free space) 120 GB. So it is empty. 
So I have only C drive with Windows 7.
please advise me. Thanks.

---

### Post by yancek on 2015-02-07
There are numerous tutorials including some at the Ubuntu site.  The tutorial below is pretty detailed and if scroll down the page it explains dual-booting.  My understanding of the wubi program is that it was a method to test Ubuntu on a windows machine.  You could install Virtualbox on windows and then install Ubuntu there.  Reading a few tutorials is probably a better idea.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Bucky Ball on 2015-02-07
Here is a tutorial using 'Something Else' option when you get to the partitioning section of the install, so you don't wipe Windows:

[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352)

Main thing is that you have unallocated space on your disk to install Ubuntu to.

---

### Post by albaqui on 2015-02-07
Thank you all for help. Yes, finally I did it. Now I have 2 OS.

---

### Post by Bucky Ball on 2015-02-07
Good news. Please share what worked for you and mark the thread as 'solved' to help others. See the second link in my signature for how. ;)

---


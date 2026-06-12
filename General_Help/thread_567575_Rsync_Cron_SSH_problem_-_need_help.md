---
title: "Rsync Cron SSH problem - need help"
date: 2007-10-04
forum: General Help
---

### Post by firewalker22 on 2007-10-04
Hey folks,
I could use a helping hand if any of you ubuntu prodigies could lend me your expertise.
I have a windows Vista 64 bit machine that is running **cgywin**, a feat within itself!
I am trying to use **openssh** to move files via **rsync** which I plan to then schedule as a cron job.

Hope you are all with me so far.

The problem is this, while I have established a connection to the remote machine and
can copy folders, the files withing are not being copied. I can copy the files if I do it manually without **rsync**... but I want** rsync** to do it as it is a task that needs to be done every day.
I do not believe that there is an **ssh** or **cgywin** problem. I think my code might be missing something for **rsync**. Please observer code below.

[I]$ sudo rsync -IavzuPOW --cvs-exclude --exclude '17EI0010.JPG' --exclude 'System*/' --exclude '*RECYCLE*/' reserve@192.168.1.112:/cygdrive/e/ /Milky_Way/Data/devBACKUP/
[/I]

The drive that I am attempting to backup ' Drive e'  is not a drive with  a windows os on it. It just contains some data files.

Man i sure would appreciate some advice, but please try not to use to many big words or assume I know much of anything. Simple things like 'Open your terminal and type this'
are things I can handle.

one more thing,
 /Milky_Way/Data/devBACKUP/  is a samba share if that makes an difference.:guitar:

---

### Post by altonbr on 2007-10-05
Not sure if this will help: [http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082), but give it a shot. I'm having some problems with this as well, so I'll report if I can get it working.

---


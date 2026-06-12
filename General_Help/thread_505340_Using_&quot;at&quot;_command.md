---
title: "Using &quot;at&quot; command"
date: 2007-07-20
forum: General Help
---

### Post by tyusoff on 2007-07-20
Hi guys, 

I have been using Xubuntu 6.10 for my other workstation and now just installed Ubuntu 7.04 for my home workstation. I used a lot of "at" command to help me running my codes on my Xubuntu machine. However, when I tried to use "at" on my Ubuntu machine, it does not work. no matter what I tried. usually i will prepare a txt file which list the command i would like to make and then assign for a time for it to run, ie

> >at 20:12 < run.txt 

but on Ubuntu it will give message as below

> warning: commands will be executed using /bin/sh
job 20 at Sat Jul 21 20:12:00 2007


but still nothing happened. could anyone point me to the right direction?? what i should do to make "at" work on ubuntu machine.

Thanks

---

### Post by dreadlord_chris on 2007-07-20
hmmmm... **at** should work the same no matter what version of Ubuntu you use.
Could you check and see if either of these files exist on your system:
**/etc/at.allow**  <-- if this file exists only names listed in it are allowed to use **at**
**/etc/at.deny**  <-- if this file exists then names listed in it are denied access to **at**

---

### Post by davidjmayo on 2007-07-20
>  warning: commands will be executed using /bin/sh
job 20 at Sat Jul 21 20:12:00 2007


You posted today (friday) at 6.37PM with a time of 20.12 so your post was before the time for the at command to run. Why is the job scheduled for saturday? It does say it will be executed not that there is an error

---

### Post by stylishpants on 2007-07-20
Remember to use the 'atq' command to see what jobs are scheduled for the future.  You should always use that command to check what's going on if you think your 'at' command wasn't quite right.

---

### Post by sulekha on 2007-07-24
> **dreadlord_chris said:**
> hmmmm... **at** should work the same no matter what version of Ubuntu you use.
Could you check and see if either of these files exist on your system:
**/etc/at.allow**  <-- if this file exists only names listed in it are allowed to use **at**
**/etc/at.deny**  <-- if this file exists then names listed in it are denied access to **at**

In my machine (dapper) there is no /etc/at.allow file so what to do???

---

### Post by dreadlord_chris on 2007-07-24
> **sulekha said:**
> In my machine (dapper) there is no /etc/at.allow file so what to do???

the files are not required - and are only used **if** they exist

---

### Post by tyusoff on 2007-11-20
finally I solved the issue. I stop using "at" for quite some time, but the need come again so I have to take a look again. It seems the problem lies in /etc/at.deny file. As the command is executed using /bin/sh, there is a "bin" line in at.deny file. Removing "bin" from the file, finally allow my program to be executed .. wow ..wat a relieve ..

---


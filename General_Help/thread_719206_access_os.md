---
title: "access os"
date: 2008-03-08
forum: General Help
---

### Post by junaid.kollam on 2008-03-08
Is it possible to access an os  in Ubuntu that is installed on another partition.(i do not mean virtual box,vmware ......) of a system?if yes.how?

---

### Post by pointone on 2008-03-09
What do you mean by access? You cannot fully run two instances at the same time without some kind of virtualization.

---

### Post by 1467 on 2008-03-09
you can get data from other partitions if that is what you wont to know 
is ti?

---

### Post by junaid.kollam on 2008-03-09
For example i have a windows installed and Ubuntu installed partition.now i want to access softwares from windows in Ubuntu.is it possible?how?.

---

### Post by pointone on 2008-03-09
Not directly; the software must be installed in the running OS if you want to run it. You can install most Windows applications in Ubuntu with [Wine]("http://www.winehq.org/").

---

### Post by paxmark1 on 2008-03-12
exactly

I am using ntfs-3g for the /windows mount I used to use only ntfs for the hard drive mount and ntfs-3g for the external hdd.

I have to keep a /windows on.  I have to run Windows about once a week. That is just the nature of my reality.

I find it very difficult wading through websites using wine with winblowz on the computer, there is a [Uvery[/U] strong bias in the web sites about just using wine with no windoze on the computer.  

What are the pros and what are the cons of using winefile to acess installed programs in the ntfs sections and using wine to run.  This would be as opposed to installing programs in /home/.wine... and acessing from there?  

If I have installed something once, why install again?  

Which performs better a windoze install on ntfs run via wine or the install on /home/~/.wine/win32 ...

Just for the sake of asking, if we keep programs seperate from date - why doesn't wine go into a /usr/wine/win32/installs?

Peace,  Mark

---


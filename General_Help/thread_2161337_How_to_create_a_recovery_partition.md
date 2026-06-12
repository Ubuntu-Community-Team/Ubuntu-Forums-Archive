---
title: "How to create a recovery partition?"
date: 2013-07-10
forum: General Help
---

### Post by Tassadar on 2013-07-10
Hi all,


I have been using linux (Kubuntu x64 to be exact) for a  few months and I use an bootable Clonezilla USB drive to make and  recover images of the system, and works great.


Now I want to make  in the hard drive a recovery partition that will allow me to press a key  or something similar when booting the computer and then go to a  recovery option with what I can restore the computer to the default  state.


I need all to be in the internal hard drive, not on a USB  drive, and I need the recovery process to be easy to use (I don't wan't  to have to select partitions or other options).


Mainly, I  understand that making this can be a bit difficult, but I don't mind,  the question is that the result, i mean, the recovery option must be  simple and easy to use.


Anyone knows how could I do this?


Many thanks in advance

---

### Post by dino99 on 2013-07-10
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)
[http://askubuntu.com/questions/56095/how-i-do-a-system-restore](http://askubuntu.com/questions/56095/how-i-do-a-system-restore)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.kingletas.com/2012/07/restore-ubuntu-to-the-default-settings-without-re-installing-it.html](http://www.kingletas.com/2012/07/restore-ubuntu-to-the-default-settings-without-re-installing-it.html)

Thats all :P

---

### Post by Mark Phelps on 2013-07-10
> Now I want to make in the hard drive a recovery partition that will allow me to press a key or something similar when booting the computer and then go to a recovery option with what I can restore the computer to the default state.


THIS ... is going to be your problem ...

Lots of folks will provide you links to tools that you can use to make a backup, either files & folders, or complete image backup .. but all of them require launching from a command line, shorcut, or menu entry.  None of them work from a key pressed during booting the PC.

There is also "remastersys" -- which can be used to make a backup that can then be restored.  I don't use this, but you can read the details from the link: [http://www.maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22]("http://www.maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22")

---


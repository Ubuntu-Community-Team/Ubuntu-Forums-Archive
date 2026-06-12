---
title: "Synaptics doesnt open"
date: 2008-05-10
forum: General Help
---

### Post by ZachDowd on 2008-05-10
I installed Ubuntu two days ago and have been trying to install SiS graphics since, Ive finally managed to get it working (I think), but now synaptics doesnt open, when I click it it appears in the window list for a moment and then disappears. I am completely new to Linux, so I have no idea how to go about fixing this, any help would be appreciated..

---

### Post by ZachDowd on 2008-05-10
Just found out that hardware drivers, hardware testing and software sources all do the same thing.

---

### Post by ryanhaigh on 2008-05-10
Try openning a terminal (apps>accessories>terminal) and entering the command sudo synaptic. This is not the recommended method but should give you error messages if the command fails which may help.

Just a guess at this stage but it may be the first issues in this thread [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by GB2732 on 2008-05-10
Try this:

[http://firmit.wordpress.com/2008/05/05/making-gksu-and-gksudo-work/]("http://firmit.wordpress.com/2008/05/05/making-gksu-and-gksudo-work/")

You may have to set the Authentication mode to 'su' the first time,

then do it again, this 2nd time choosing 'sudo'. It worked for me.

---


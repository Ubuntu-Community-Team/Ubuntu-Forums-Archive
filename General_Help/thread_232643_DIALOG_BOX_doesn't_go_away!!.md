---
title: "DIALOG BOX doesn't go away!!"
date: 2006-08-09
forum: General Help
---

### Post by boom2k1 on 2006-08-09
This kind of dialog box doesn't go away!!!
How come??

Even if I press Hid All Hide, it doesn't go away!!

It is a java dialog box.


It won't go away unless I go to the System Monitor and shut off java!

It is problematic because in Azureus this kind of dialog box shows up whenever I have an error. I wouldn't be able to close it unless I shut down Java (and also closes Azureus)

Help!

---

### Post by hopstah on 2006-08-09
go here [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php) and download the newest shapshot of the Azureus2.jar file

backup your current Azureus2.jar file ```
sudo mv /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.bak
```
then move the downloaded one to the proper folder ```
sudo mv [path to downloaded file] /usr/share/java/Azureus2.jar
```
that will take care of it!

---

### Post by Jonathan Métillon on 2006-09-18
Hi,

I'm experiencing the same problem with Azureus 2.4.0.2 under Ubuntu 6.06.

Is there an easier fix since August? No update of Azureus fix it?

---


---
title: "After pidgin install (via getdeb) synaptic doesnt work anymore"
date: 2007-05-29
forum: General Help
---

### Post by amonsul on 2007-05-29
Hi all!

Yesterday I`ve installed pidgin through getdeb package. Pidgin works fine. But today when i launch synaptic an error-message appears. The same when i try to start the update-manager. 

The error message tells me that he must reinstall pidgin but he cannot find the .deb package (that  I´ve donwloadad and then cancelled). What can i do???

When i try to reinstall pidgin .deb packages from getdeb i get the same error-message. And i cannot remove the package (even in console).

p.s.:
Sorry, my system language is german so the screenshot are german  too.

---

### Post by deadlikeoscar on 2007-05-29
Did you try: sudo apt-get remove package_name? I had this problem when a package wanted to overwrite some files of another and so it didn't install all of the way but it would still run.  I had to remove it to get synaptic to work again.

---

### Post by loathsome on 2007-05-29
Try something like this: ```
sudo apt-get remove -f -m -y <package name>
```

---

### Post by amonsul on 2007-05-29
When i do this i get the following error:

> amonsul@amonsul:~$ sudo apt-get remove -f -m -y pidgin
Password:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
E: Das Paket pidgin muss reinstalliert werden, ich kann aber kein Archiv dafür finden.
amonsul@amonsul:~$ 
translated: Pidgin must be reinstalled but i cannot found an archiv for it....


What can i do now?

---

### Post by Dougie187 on 2007-05-29
Try this.

[http://ubuntuforums.org/showthread.php?t=437239](http://ubuntuforums.org/showthread.php?t=437239)

I might suggest, that next time you install it instead of using getdeb build it from source. Its not very hard and I know it works.

---

### Post by dreadlord_chris on 2007-05-29
Ya... I had this same problem yesterday with a different package (nvidia-glx) - [http://ubuntuforums.org/showthread.php?t=457256](http://ubuntuforums.org/showthread.php?t=457256)

try installing the .deb manually with dpkg:
```

dpkg -i packagename.deb

```

---


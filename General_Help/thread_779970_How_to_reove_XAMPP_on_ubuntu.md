---
title: "How to reove XAMPP on ubuntu ?"
date: 2008-05-03
forum: General Help
---

### Post by reyhan on 2008-05-03
How do i Remove Xampp on ubuntu?

---

### Post by Monicker on 2008-05-03
Do you mean xampp?  How did you install it?

Check to see if it is listed in the package manager.
```

sudo dpkg --get-selections | grep xampp
```

If it is:
```

sudo apt-get remove xampp
```


If not, then you need to follow the instruction from wherever you received the package.  Source tarball packages can often be remove by doing

```
make uninstall
```

...from the dir where you extracted the files to.

---

### Post by Cebonet on 2009-09-04
try this:

rm -rf /opt/lampp

---

### Post by bvanaerde on 2009-09-04
> **Cebonet said:**
> rm -rf /opt/lampp
Yup... just delete the files, it's that [easy]("http://www.apachefriends.org/en/xampp-linux.html#388") :D

---

### Post by erlend_sh on 2010-02-06
the rm command deleted it for me, however I still have a problem: The XAMPP control panel is still accessible through my applications tab :( It won't open of course, but how do I remove it completely? Is it just a cosmetic glitch or are there still some XAMPP files left on my system somewhere?..

---

### Post by grizzler on 2010-02-06
Just cosmetic. Everything belonging to XAMPP was in /opt/lampp.

If you want to get rid of menu entries, just delete them using the menu editor.

---

### Post by avram063 on 2010-05-25
I don't have permission. how to fix that.

---

### Post by ubunterer on 2011-02-05
> **avram063 said:**
> I don't have permission. how to fix that.

U probably must use "sudo" command before autoscrable ur root pass of ur ubuntu as ubuntu doesnt provide root password for your system by default. 

Try:

sudo rm -rf /opt/lampp

..this will do the delete job of your xampp for linux ;)

---


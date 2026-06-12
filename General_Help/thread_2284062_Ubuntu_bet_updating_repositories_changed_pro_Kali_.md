---
title: "Ubuntu bet updating repositories changed pro Kali name: c"
date: 2015-06-26
forum: General Help
---

### Post by Arthur_Aires on 2015-06-26
I wanted to download the repositories of Kali more just spoiling my Ubuntu, and now most of the applications that I run my system recognizes as Kali: c.
 Examples:

[IMG]http://img.gforum.tv/img/05f5cac5b028876282b4d79b861f0a55cc26083f.png[/IMG]

and 

[IMG]http://img.gforum.tv/img/a0385e2bd969b7db3ad7bd86a6d9b73b994a464f.png[/IMG]

 How do I return it to normal?
Already I turned off the sources.list lines of repositories kali, and gave an update and upgrade more to no avail: c.

---

### Post by wildmanne39 on 2015-06-26
*Thread moved to **General Help**.*

---

### Post by Arthur_Aires on 2015-06-27
Someone has the answer to my question?

---

### Post by Arthur_Aires on 2015-06-27
Someone has the answer to my question?32

---

### Post by QIII on 2015-06-27
When you log in, are you presented with a choice to start the Unity interface or Kali's interface?

Would you also run the following in the terminal and post back the results?  This will not make changes.  The -s flag stands for "simulate"

```
sudo apt-get -s purge kali-*
```

Unfortunately, since we don't know exactly what you did, you may have overwritten much of your Ubuntu installation with Kali system directories/files.

---


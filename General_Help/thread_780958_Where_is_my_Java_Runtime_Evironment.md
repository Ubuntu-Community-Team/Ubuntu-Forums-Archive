---
title: "Where is my Java Runtime Evironment?"
date: 2008-05-03
forum: General Help
---

### Post by DandyDon on 2008-05-03
I'm trying to use Open Office but when I open the Project Wizards , it tells me I need a Java JRE in order to use that Open Office function.

I check Add/Remove Programs and it shows Java Runtime Environment installed. 

What am missing?.

---

### Post by jimv on 2008-05-03
Try this in a terminal

sudo apt-get install --reinstall sun-java6-jre

---

### Post by rbmorse on 2008-05-04
If that doesn't work, try installing 

openoffice.org-java-common

from repository.  I used synaptic.

---

### Post by DandyDon on 2008-05-04
> **rbmorse said:**
> If that doesn't work, try installing 

openoffice.org-java-common

from repository.  I used synaptic.

That what did. I unstalled what had, and installed all modules via Add / Remove.

---

### Post by spudtheimpaler on 2008-05-04
'which' is a useful command as well for things like this:

```
me@mybox:~$ which java
/usr/bin/java
```

which will probably give you a link to your java install...
```
me@mybox:~$ ls -la `which java`
lrwxrwxrwx 1 root root 22 2008-05-03 23:42 /usr/bin/java -> /etc/alternatives/java
```

or not - thats another link...

```
me@mybox:~$ ls -la /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2008-05-03 23:42 /etc/alternatives/java -> /usr/lib/jvm/java-6-sun/jre/bin/java

```

There we go.

HTH

Mitch.

---

### Post by Annoying Moose on 2008-05-04
You may also need to select your JRE in OpenOffice itself.

[LIST=1]
[*]Select "Tools" from the menu bar.
[*]Select "Options".
[*]Under the "OpenOffice.org" subtree, select "Java".
[*]Check the "Use a Java runtime environment" checkbox, if it isn't already.
[*]You may need to wait a few seconds, but OOo will automatically detect all (or, at least, most) JREs currently installed on your system.  In your case, there should be a single option in the "Java runtime environments already installed" box.  Select it and click the OK button.
[/LIST]

If the option for your JRE didn't appear in the list, then your JRE is most likely not installed properly.  I would follow the advice of jimv and rbmorse.

---

### Post by LindaLou on 2008-09-03
I followed the info from jbmorse and came upon this - see attached screen shots - as my Oo shows no Java installed and there are none found in the Add/Remove.  
I am completely in the dark as to what additions I would need to select, if any.  I am running Oo V 2.4.1 on Ubuntu latest version, 64bit.

You advice is greatly appreciated.

---

### Post by jespdj on 2008-09-03
Synaptic is telling you that those packages need to be installed, because something else you're trying to install needs all those packages.

Just click Mark to let it install all that stuff.

---

### Post by LindaLou on 2008-09-04
Thank you very much jespdj, for your advice.  I haven't had the need to use any of the templates in Oo until now and I kinda freaked out when I saw the list for Java!!

Again, your reply is much appreciated.:)

---


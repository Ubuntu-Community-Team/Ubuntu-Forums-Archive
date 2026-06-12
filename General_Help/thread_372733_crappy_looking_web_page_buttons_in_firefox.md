---
title: "crappy looking web page buttons in firefox"
date: 2007-02-28
forum: General Help
---

### Post by krystiana on 2007-02-28
Hi

I would like to get some advice on firefox under Ubuntu. I recently switched from Windows Xp and noticed that in Firefox on web pages some controls look crappy (blocky) and not even close to the gnome theme ones.

By controls i mean:
buttons
check fields
switch fields and other 

Is there a way to force firefox to use the buttons look and ... from gnome? or just change the default one?

---

### Post by mcduck on 2007-02-28
You can replace them with better ones. I've made a installer for nice firefox widgets, I'll attach it here.

Extract the package and run './install.sh' that's included. Restart Firefox and that's it :)

edit: You need to run the script from the same directory where the script is!

---

### Post by Pikestaff on 2007-02-28
> **mcduck said:**
> You can replace them with better ones. I've made a installer for nice firefox widgets, I'll attach it here.

Extract the package and run './install.sh' that's included. Restart Firefox and that's it :)

I'm interested in this too so I downloaded it as well :)  But it's telling me "no such file or directory".  Does it work with Firefox 2?

This is exactly what it gets me:

```
cat: res/forms-extra.css: No such file or directory
cp: cannot stat `res/form-widgets': No such file or directory

```

---

### Post by llamakc on 2007-02-28
It worked for me on:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20060601 Firefox/2.0.0.1 (Ubuntu-edgy)

---

### Post by mcduck on 2007-02-28
> **Pikestaff said:**
> I'm interested in this too so I downloaded it as well :)  But it's telling me "no such file or directory".  Does it work with Firefox 2?

This is exactly what it gets me:

```
cat: res/forms-extra.css: No such file or directory
cp: cannot stat `res/form-widgets': No such file or directory

```
Yes, it does, but only if it's installed in the default place. Ubuntu 6.06 only has Firefox 1.5, so if you have Firefox 2 you must have installed it yourself in some other than the default place..

The INSTALL file has instructions for manual install.

(also, you need to run the script from the same directory where the script is)

---

### Post by Pikestaff on 2007-02-28
Awesome, that worked... Firefox looks a lot better now... thank you! :-D

---

### Post by krystiana on 2007-03-01
Hi

Thank you :-)
Well this should be included in default firefox package for ubuntu. otherwise it looks so bad... just doesnt fit rest of the ubuntu gnome environment.

---


---
title: "java path name in .bashrc"
date: 2005-09-07
forum: General Help
---

### Post by legit on 2005-09-07
hey all,
so i installed the java rpm but i don't know how to add it to the .bashrc file, i know i need to add a path name but im not sure what the syntax is and such can anyone help me out?
thanks,
- legit

---

### Post by numberexhaust on 2005-09-07
Well you have to figure out where the path of the "bin" directory is... I write java programs myself and installed java by hand.

What you need to do is add the following line:

```
export PATH=/where/you/want:$PATH
``` 

to the following file:

```
sudo gedit ~/.bashrc
``` 

Hope that helps

---

### Post by legit on 2005-09-07
okay so i did that but now i get the following error when i type java:
"Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object"

any ideas?

*edit* nevermind i think i found a solution *edit*

---

### Post by numberexhaust on 2005-09-07
[QUOTE=legit]okay so i did that but now i get the following error when i type java:
"Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object"

any ideas?

*edit* nevermind i think i found a solution *edit*[/QUOTE]
 what exactly are you trying to do?

---


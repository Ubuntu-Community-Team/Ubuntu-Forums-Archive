---
title: "I can't uninstall this program."
date: 2006-12-22
forum: General Help
---

### Post by jincast90 on 2006-12-22
Hello. I recently downloaded a program because I needed an alarm clock. I opened synaptic, and found a program called SandUhr. The thing is I don't like the program, but each time I try and uninstall the program it gives me the error on the picture. What is wrong? Why can't I remove the program?

---

### Post by taurus on 2006-12-22
See if you can remove it from a terminal!

Applications -> Accessories -> Terminal
```
sudo aptitude remove sanduhr
```

---

### Post by jincast90 on 2006-12-22
> **taurus said:**
> See if you can remove it from a terminal!

Applications -> Accessories -> Terminal
```
sudo aptitude remove sanduhr
```

I already had tried this, but I tried again anyways. It will not work. The program is still there.

---

### Post by pickarooney on 2006-12-22
try reinstalling it, see if that repairs the uninstall script?

---

### Post by jincast90 on 2006-12-22
> **pickarooney said:**
> try reinstalling it, see if that repairs the uninstall script?

Okay.. I reinstalled, and that went just fine. But afterwards when I tried to uninstall it, I got the same error.

---

### Post by pandu.rs on 2006-12-22
just remove the menu entry using alcarte menu editor and forget abt that program :)

---

### Post by raul_ on 2006-12-22
What error do you get in the terminal? Maybe the program is running while you're trying to uninstall it. Try 
```

ps aux | grep sanduhr

```

of course, substitude sanduhr with the correct name, if that's not it...if something pops up just kill it and then try uninstalling again

---

### Post by neotasic1 on 2007-05-19
> **jincast90 said:**
> Hello. I recently downloaded a program because I needed an alarm clock. I opened synaptic, and found a program called SandUhr. The thing is I don't like the program, but each time I try and uninstall the program it gives me the error on the picture. What is wrong? Why can't I remove the program?


I too have had troubles removing this program but have found the solution. The reason the un-installation fails is because the removal program is scripted to remove a file named sanduhr-C.omf which is located in the directory usr/share/omf/sanduhr. A reference to this file is part of the error message I get when I run "sudo aptitude remove sanduhr" from the terminal window. If your installation is the same as mine, if you check the contents of this directory you will have a file in there called sanduhr-de.omf. (presumably because the author was German.) For the uninstall to work correctly you need to rename this file to sanduhr-C.omf. Unfortunately you will not have permissions to do this unless you do it from the teminal window with superuser permissions. 

Type this code in the Terminal

cd /usr/share/omf/sanduhr
sudo chmod 777  sanduhr-de.omf
mv sanduhr-de.omf sanduhr-C.omf
sudo aptitude remove sanduhr

Hey presto - this did the trick. Let me know how you go. I have posted this as a reply to your thread even if you have already found a solution  as others may have the same problem - inevitable if the uninstall script is not amended. (I don't know how to fix that unfortunately)

---

### Post by Banter on 2007-05-25
if ```
mv sanduhr-de.omf sanduhr-C.omf
``` raises a permission error, try
```
sudo mv sanduhr-de.omf sanduhr-C.omf
```

---

### Post by neotasic1 on 2007-05-31
> **Banter said:**
> if ```
mv sanduhr-de.omf sanduhr-C.omf
``` raises a permission error, try
```
sudo mv sanduhr-de.omf sanduhr-C.omf
```

Well picked up. :D

---


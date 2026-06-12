---
title: "[SOLVED] how nautilus-scripts for all users"
date: 2008-04-26
forum: General Help
---

### Post by zvacet on 2008-04-26
How can I install nautilus scripts for all users.I tried put them in /usr/share/nautilus-scripts but it doesn´t help.Now only user who installed them is able to use them.I want to install them once and all users to be able to work with them.

---

### Post by fragos on 2008-04-26
I can only think of one way to do this. Place the scripts in a centralized location and make a link in each home directory so that their .gnome2/nautilus-scripts folder points there. You have to touch each install once but can make all changes to the scripts themselves in the centralized folder.

---

### Post by zvacet on 2008-04-27
Thanks for replay,but I don´t think that is the way,because I used to install them for all users,but forget how to do it.When I installed one nautilus-script from synaptic in /usr/share is made folder named nautilus-scripts.That is the reason I think that all of them should be there,so I tried to do that with no joy.Still open for suggestions and advices.

---

### Post by fragos on 2008-04-27
What I suggest should work. There may well be a system wide folder that can do what you want for all users. It might be teadious but you can look in the nautilus source code. Try grep in the source code for "nautilus-scripts" to zero in on the area where the code is. Even if you can't code in C or whatever language is used you will be able to pick out folder and file names.

---

### Post by zvacet on 2008-04-27
After ages in dark I make it happened.Followed your first advice and done with 

```
ln -sf /usr/share/nautilus-scripts/ ~/.gnome2/nautilus-scripts
```

Thank you!

---

### Post by bowwave on 2008-04-27
>> strings /usr/bin/nautilus|grep nautilus-scripts
/.gnome/nautilus-scripts
~/.gnome2/nautilus-scripts

---

### Post by zvacet on 2008-04-27
I don´t see under thread tools option **mark as solved**.

---


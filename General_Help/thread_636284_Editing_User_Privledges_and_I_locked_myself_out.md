---
title: "Editing User Privledges and I locked myself out"
date: 2007-12-09
forum: General Help
---

### Post by smorris08 on 2007-12-09
I have three user accounts on my computer. One being root, another being the one i automatically log-in to, a third that my friend made when helping me set up some things on my computer so I don't know the password of. 

The problem I'm having is that while in groups and users to delete my friend as a user i accidently clicked administrator privileges on mine and so now my main account can't go back in and change users and groups. 

I know i can do this in the terminal or through the root account (which i know the password) I just can't figure out how...


Any help is appreciated

---

### Post by Total_Biscuit on 2007-12-09
Folks seem to do this all the time, so there're loads of answers to the question in the forums here.  Try the first part of this one: [http://ubuntuforums.org/showpost.php?p=2598193&postcount=2](http://ubuntuforums.org/showpost.php?p=2598193&postcount=2)

---

### Post by mali2297 on 2007-12-09
Boot in recovery mode to get to a root terminal. Then type
```

usermod -a -G admin smorris08

```
..assuming your user name is smorris08.

---


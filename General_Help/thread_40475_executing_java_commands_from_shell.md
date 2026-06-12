---
title: "executing java commands from shell"
date: 2005-06-09
forum: General Help
---

### Post by btumpps on 2005-06-09
hi. i have installed java 2 sdk 5.0 to my /home/jdk1.5.0_O3 directory. i think the java commands are in the directory /home/jdk1.5.0_O3/bin. how can i use those commands from shell window?

---

### Post by wylfing on 2005-06-09
The easy way to fix this is to add the java path to the PATH variable. Try:
```
export PATH=$PATH:/usr/local/jdk1.5.0_02/bin
``` 
Alter the java path to match what's on your system. The old-school way to fix this permanently would have been to edit ~/.bash_profile (or equivalent for the shell you use), but I don't believe a login bash shell is ever launched unless you are, for example, ssh-ing into your box. Try creating a file called ~/.gnomerc and putting the line above in that file. The next time you reboot, it should be there for you.

---

### Post by btumpps on 2005-06-09
[QUOTE=wylfing]The easy way to fix this is to add the java path to the PATH variable. Try:
```
export PATH=$PATH:/usr/local/jdk1.5.0_02/bin
``` 
Alter the java path to match what's on your system. The old-school way to fix this permanently would have been to edit ~/.bash_profile (or equivalent for the shell you use), but I don't believe a login bash shell is ever launched unless you are, for example, ssh-ing into your box. Try creating a file called ~/.gnomerc and putting the line above in that file. The next time you reboot, it should be there for you.[/QUOTE]

thanks that was helpful.

---

### Post by Joeb on 2005-06-09
Just an additional recommendation.  You might want to make a symlink to the actual java installation under /usr/local (or whereever you have java installed) and then use the name of the symlink (ie java) in the path statement.  That way, you can change the version of java you have installed without having to redo all the path stuff.  You could even have multiple versions of java installed and have the java symlink point to the one you want to use (say for testing different releases).

---


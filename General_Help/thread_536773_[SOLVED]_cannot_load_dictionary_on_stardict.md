---
title: "[SOLVED] cannot load dictionary on stardict"
date: 2007-08-28
forum: General Help
---

### Post by al.adab on 2007-08-28
hi, 

I've downloaded + unpacked the Oxford Advanced Learner's Dictionary found at 
[http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php](http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php). 
 
I tried the following (not knowing exactly what I'm doing...): 

**sudo mv stardict-oald-2.4.2 /usr/share/stardict/dic**

and got this error: **mv: cannot stat `stardict-oald-2.4.2': No such file or directory**

I then looked into the unpacked folder and thought I should maybe try this: 

**sudo mv oald.dict.dz /usr/share/stardict/dic**

but got this error: **mv: cannot stat `oald.dict.dz': No such file or directory**

I also found somewhere I should maybe try **sudo mkdir /usr/share/stardict/dic**
but found out that **mkdir: cannot create directory `/usr/share/stardict/dic': File exists**

Can anyone help me? I'm probably doing something stupid but know so little about Linux I cannot figure out what it is. Thanks tons.

---

### Post by wormser on 2007-08-28
> sudo mv stardict-oald-2.4.2 /usr/share/stardict/dic

and got this error: mv: cannot stat `stardict-oald-2.4.2': No such file or directory

I think the problem is you are not in the folder that stardict-oald-2.4.2 is in.  Change into that directory then run the command.  Another option is to specify the complete path to stardict-oald-2.4.2.  Like /home/username/stardict-oald-2.4.2.

> I also found somewhere I should maybe try sudo mkdir /usr/share/stardict/dic
but found out that mkdir: cannot create directory `/usr/share/stardict/dic': File exists

It looks like the directory already exists.

---

### Post by al.adab on 2007-08-28
[QUOTE=wormser;3266746]I think the problem is you are not in the folder that stardict-oald-2.4.2 is in.  Change into that directory then run the command.  Another option is to specify the complete path to stardict-oald-2.4.2.  Like /home/username/stardict-oald-2.4.2.

sorry...I do not understand what you mean. Can you please give me an example? Thanx!!!

---

### Post by wormser on 2007-08-28
> **al.adab said:**
> 
sorry...I do not understand what you mean. Can you please give me an example? Thanx!!!

The shell looks in the current directory.  You have to specify the path to the file.  When you run that command the first part (stardict-oald-2.4.2) does not specify the exact path to the file.  So, the shell looks in the current directory for the file.  If that file is not in that directory then it will return the error you got.  

You need to cd into the directory where the file stardict-oald-2.4.2 is then run the command.  This way the shell will be able to find the file and execute the rest of the command.

If this is a bit too much for you right now, you can do this with the gui.

```
gksudo nautilus
```

Nautilus is the file browser and gksudo give you root privileges for graphical applications.

---

### Post by al.adab on 2007-08-28
[QUOTE=wormser;3266847]The shell looks in the current directory.  You have to specify the path to the file.  When you run that command the first part (stardict-oald-2.4.2) does not specify the exact path to the file.  So, the shell looks in the current directory for the file.  If that file is not in that directory then it will return the error you got.  

Right: if I type **sudo mv /home/daniele/stardict-oald-2.4.2 /usr/share/stardict/dic** and I get **mv: cannot stat `/home/daniele/stardict-oald-2.4.2': No such file or directory**. If I type either **cd stardict-oald-2.4.2 ** or **cd /home/daniele/stardict-oald-2.4.2** I get bash: **cd: stardict-oald-2.4.2: No such file or directory**. Or I've possibly completely misunderstood what you say???

The dictionary I downloaded + unpacked is at /home/daniele (that's what I get if I right-click on it and choose "properties"). If I open it, I find that the main file is called 'oald.dict.dz'. Is there any chance you can tell me step by step what I should do to be able to use it on StarDict? That is, can you please give me a list of commands I should type into terminal? Thank you again for your patience.

---


---
title: "Change default path of program for newer verison??"
date: 2013-02-02
forum: General Help
---

### Post by einstein**-7 on 2013-02-02
okay, noob question.  
When you manually install a newer version of a program thats on your system how do you tell the system to go there when executing  shell ''' program_name '''' instead of the older version?
Also change the icon path as well-- not simply create a new generic shortcut??
Thanks,

---

### Post by Frogs Hair on 2013-02-02
Some details about the program might help. You may have both programs installed with a different version number. An example is python on 12.10 having two versions installed. Does the new version replace the old?

---

### Post by einstein**-7 on 2013-02-02
> **Frogs Hair said:**
> Some details about the program might help. You may have both programs installed with a different version number. An example is python on 12.10 having two versions installed. Does the new version replace the old?

In my case yes but the programs vary.
one is rawtherapee new replaces old but don't want to remove old.

---

### Post by Frogs Hair on 2013-02-03
What you are describing might only work if the new and old version can be installed at the same time. If that is possible changing the icon would not be difficult.

If the new version is an upgrade of the old and does not install separately then you may be out of luck.I don't know that you could change the installation locations of a separate package . keep in mind that files for a program in Ubuntu are often placed in many different folders.

---

### Post by rnerwein on 2013-02-03
> **einstein**-7 said:**
> okay, noob question.  
When you manually install a newer version of a program thats on your system how do you tell the system to go there when executing  shell ''' program_name '''' instead of the older version?
Also change the icon path as well-- not simply create a new generic shortcut??
Thanks,
hi
if you start your program via terminal then (i think the version are in different places) the use the full path name: /path/to/version_old, /path/to/version_new.
or just rename one version.
for the icon, if they use the same icon - i don't know. sorry
cheers

---

### Post by einstein**-7 on 2013-02-03
Okay, newer version wasn't technically installed,  just downloaded  and unziped into folder.. wasn't available from source site. 
So i guess a better question would be how to add the path to that executable to the system.
I don't want to rename since that would probably cause dependency  issues just re-rout the command rawtherapee to the other location without specifying the path to it in the shell.

---

### Post by Impavidus on 2013-02-03
With more or less default settings your shell will first look in ~/bin, then in /usr/local/bin and then in /usr/bin, where the old version has been installed if that came from the repos. If you put your new version in one of the directories earlier in your $PATH the shell will run the new version by default and the old version if you specify the entire path.

You could put your downloaded executable in ~/bin or place a symlink to it in ~/bin (create the directory if necessary).

---

### Post by rnerwein on 2013-02-04
> **einstein**-7 said:**
> Okay, newer version wasn't technically installed,  just downloaded  and unziped into folder.. wasn't available from source site. 
So i guess a better question would be how to add the path to that executable to the system.
I don't want to rename since that would probably cause dependency  issues just re-rout the command rawtherapee to the other location without specifying the path to it in the shell.
hi
this will don't solve your question when you will run both versions without a full pathname.
in your .bashrc you can set the PATH (don't forget to export it !). the PATH is search from left to right. e.g.: PATH=$PATH:/path_to_old_version:/path_to_new_version
the system will always get your old version (that's even a story about fine-tuning).
i have no idea of another way to solve your question (i would rename it).
cheers

---

### Post by einstein**-7 on 2013-02-04
> **Impavidus said:**
> With more or less default settings your shell will first look in ~/bin, then in /usr/local/bin and then in /usr/bin, where the old version has been installed if that came from the repos. If you put your new version in one of the directories earlier in your $PATH the shell will run the new version by default and the old version if you specify the entire path.

You could put your downloaded executable in ~/bin or place a symlink to it in ~/bin (create the directory if necessary).

> **rnerwein said:**
> hi
this will don't solve your question when you will run both versions without a full pathname.
in your .bashrc you can set the PATH (don't forget to export it !). the PATH is search from left to right. e.g.: PATH=$PATH:/path_to_old_version:/path_to_new_version
the system will always get your old version (that's even a story about fine-tuning).
i have no idea of another way to solve your question (i would rename it).
cheers
Ok, not sure what a symlink is but found the .bashrc file but where is the file that has the "PATHS" specified?  how would i add or edit a PATH for any program?
Sorry,  I'm a noob when it comes to manually managing system stuff.

---

### Post by Impavidus on 2013-02-04
Your PATH is a colon separated list of all directories where the shell searches for the commands you give. You can add new directories to your PATH by prepending them to the PATH, for example, to add the directory ~/myownprogs, add the following lines to the file .bashrc:```

PATH=~/myownprogs:"${PATH}"
export PATH
```When you do so, the shell will first try to find commands in ~/myownprogs before it tries the default directories.

---


---
title: "Getting Java to work in Firefox"
date: 2005-10-18
forum: General Help
---

### Post by allroz on 2005-10-18
I know this should be in the 64 section, and in hoary, but there are much more people that come through here and i figured i would get a better answer. I have a 64 bit and am running hoary. I'm having a great difficulty in getting java to display in firefox. I've tried using synaptic package manager to install and doing it through terminal but i still can't see it. I really need this up and running by thursday for my employee login. Can someone please give me a cut and dry method of installing blackport (i think that's what its called) or whatever its is that allows me to view java on firefox. Im still a newb at this, and need something easy but something that'll work. Thanks.

---

### Post by adwait on 2005-10-18
1)Its called BACKPORT
2)Its not what you need. That's when you want to install a newer version of software, which is not available in the repositories of your current OS.
3)After having installed it. did you add it to your path? What does
```
which java
``` 
say?
Did you add the following lines to the file /home/$USER/bash.bashrc
> JAVA_HOME=/usr/java/jre1.5.0_04
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH


---

### Post by allroz on 2005-10-18
It just says usr/bin/java when i type which java in. When i type thta other stuff in it does nothing.

---

### Post by adwait on 2005-10-18
The other stuff? Those lines are supposed to be added to a file.....read carefully :)

---

### Post by allroz on 2005-10-18
It just says there's no such file to open. :confused:

---

### Post by adwait on 2005-10-18
It should be there in your home directory......
/home/<yourusername>/bash.bashrc

---

### Post by rwilliams on 2005-10-18
[QUOTE=allroz]I know this should be in the 64 section, and in hoary, but there are much more people that come through here and i figured i would get a better answer. I have a 64 bit and am running hoary. I'm having a great difficulty in getting java to display in firefox. I've tried using synaptic package manager to install and doing it through terminal but i still can't see it. I really need this up and running by thursday for my employee login. Can someone please give me a cut and dry method of installing blackport (i think that's what its called) or whatever its is that allows me to view java on firefox. Im still a newb at this, and need something easy but something that'll work. Thanks.[/QUOTE]

The java you're referring to is called "Blackdown".  The instructions for installing the AMD64 version can be found here: [https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)

Hope this helps

---

### Post by majed on 2005-10-19
Check this out: [http://ubuntuforums.org/showthread.php?t=76754&highlight=java+plugin]("http://ubuntuforums.org/showthread.php?t=76754&highlight=java+plugin") .. it is a great how-to that worked with me perfectly!

just follow the procedure with the obvious change of downloading the 64 version and changing the file name accordingly as you go through the instructions.. good luck!

---

### Post by allroz on 2005-10-19
I still can't get it to work. It keeps saying error.

---


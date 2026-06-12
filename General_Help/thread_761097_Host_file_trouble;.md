---
title: "Host file trouble;"
date: 2008-04-20
forum: General Help
---

### Post by Chris.Jr on 2008-04-20
I am trying to follow bodhi.zazen's guide for the host file :

[http://ubuntuforums.org/showthread.php?t=241460#2](http://ubuntuforums.org/showthread.php?t=241460#2)

The trouble I am having is that when I try to do the following commands :

    * Download the script
    * Make the script executable (chmod a+x updatehosts.sh)
    * Install tofrodos (sudo apt-get install tofrodos)
    * sudo ./updatehosts.sh

I tried doing the chmod step, but it does not work. It returns to me as : "chmod: cannot access `updatehosts.sh': No such file or directory". When the script it downloaded, it's named "updatehosts.sh.txt" I deleted the .txt extentsion and it still returned the same error. I tried adding the .txt to the command but it still didn't work. The script is exactly on my desktop and it stills returns this! I tried to sudo, and it does the same error! Why will this not work? :confused:

---

### Post by Rocket2DMn on 2008-04-20
You need the .sh extension, you were right to delete the .txt extension.  That command is run from terminal, and when you open a terminal, it defaults you to your home directory, not the desktop.  To do that you need to use to cd command to change directories.
So you have
```
cd ~/Desktop
```
the ~ denotes your home folder (the default when you open a terminal, so it's not really necessary).  Also, linux is case sensitive, so Desktop needs to be capitalized (one of the few files/folders with a capital letter by default).
More help with terminal can be found here - [http://linuxcommand.org/](http://linuxcommand.org/)

---


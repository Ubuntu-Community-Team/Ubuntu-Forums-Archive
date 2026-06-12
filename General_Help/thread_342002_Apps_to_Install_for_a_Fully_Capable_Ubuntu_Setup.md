---
title: "Apps to Install for a Fully Capable Ubuntu Setup?"
date: 2007-01-19
forum: General Help
---

### Post by presbp on 2007-01-19
I want to revert to the default set of programs and configurations that comes with a clean install of Ubuntu Edgy because right now I have programs that have been installed that won't go away or their icons in the apps menu won't disappear.  I don't want to have to reinstall Ubuntu again is there any command or series of commands to revert to the default setup when Ubuntu is just installed?  If not I will just do a clean reinstall and start over.
       I want to know.. if I revert Edgy back to default and want to install programs and utilities to make Ubuntu have the most capable setup (can do the most things easily) which programs should I install that have the best functionality, stability and overall usability??
   I have been really frustrated with Ubuntu but maybe this can help.  Thanks.

---

### Post by scrooge_74 on 2007-01-19
Why can you remove apps? Does from sypnaptic are the easiest to remove, others you installed you just remove the directories and files using sudo rm -rf /the name of the directoriy

---

### Post by kd7swh on 2007-01-19
That just depends on what you want to do. Everyone has there favorite programs. 
I use firefox, vlc, putty, pan, gaim, ffmpeg, and open office everyday.  

There are over 20,000 programs in the full repository. 

If you tell me what do you want to do then i can give you the name of a program. :)


___

for removing apps you can also try:
```
sudo apt-get remove "name of app" 
```

---

### Post by igknighted on 2007-01-19
try:
```
sudo aptitude install ubuntu-desktop
```
This is a metapackage that should install any packages you are missing that came with the default install.

---


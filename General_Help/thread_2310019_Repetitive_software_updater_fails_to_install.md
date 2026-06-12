---
title: "Repetitive software updater fails to install"
date: 2016-01-15
forum: General Help
---

### Post by WaltL on 2016-01-15
I'm running Xubuntu 14.04 LTS.  For sometime now I have gotten an update from Software Updater that is about 350 MB that includes security updates for Chrome, Firefox, Thunderbird as well as updates for R, GCC, GNU and xubuntu base.  When I try to install I get a msg saying that the update "requires installing packages from unauthenticated sources."  I hit OK and, presumably, nothing happens, since the next day I will get the same updater request.  I assume that maybe one or more of the packages fails to install and thus nothing gets installed; although, I have no evidence that this is what is happening and I get no msg. that the updates have failed.

Has anyone else experienced this and or is there any package that should be excluded that may allow the others to install successfully?

---

### Post by Shaun_Dixon on 2016-01-15
I am new to Linux myself, but maybe we can see what is causing the issue by checking for any updates in the terminal. 

Is it possible to open up a terminal window and then type the following command

```
sudo apt-get update
```

and then

```
sudo apt-get upgrade
```

That should identify any updates and it should you give a prompt to install them.  If it fails then it should give some output in the terminal we can see.  

That could be a start and I am sure someone who is more knowledgeable than me will come along with other possible solutions if that does not work.

---


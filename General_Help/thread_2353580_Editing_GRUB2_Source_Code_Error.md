---
title: "Editing GRUB2 Source Code Error"
date: 2017-02-23
forum: General Help
---

### Post by shawn.c on 2017-02-23
Hey guys, 

I'm new to this whole Ubuntu and Linux in general and have encountered some problems when trying to fiddle around with the GRUB2 source code. 

My aim was to try to edit the GRUB2 header which is currently GNU GRUB version2.02..... 

Searching online i found that one way to go about changing it was through editing the source code and recompiling it. 

Following the instructions from these website :

[http://askubuntu.com/questions/357186/how-to-change-the-header-title-and-help-message-in-grub-menu?noredirect=1&lq=1](http://askubuntu.com/questions/357186/how-to-change-the-header-title-and-help-message-in-grub-menu?noredirect=1&lq=1)
[http://askubuntu.com/questions/28372/how-do-i-get-and-modify-the-source-code-of-packages-installed-through-apt-get?noredirect=1&lq=1](http://askubuntu.com/questions/28372/how-do-i-get-and-modify-the-source-code-of-packages-installed-through-apt-get?noredirect=1&lq=1)

and editing the line from
```
msg_formatted = grub_xasprintf (_("GNU GRUB  version %s"), PACKAGE_VERSION);
```
to
```
msg_formatted = grub_xasprintf (_("Test Test  version %s"), PACKAGE_VERSION);
```

I have manage to compile and install the new source code with the command
```
dpkg-buildpackage -rfakeroot -uc -b
``` 

```
sudo dpkg -i --force-all grub-pc*.deb grub2-common*.deb
```

However after restarting and re-entering the GRUB2 menu, the title still shows GNU GRUB version2.02 ..... 

Is there anything I missed out? 
Currently running Ubuntu 16.04 LTS in case it is an important information. 
Thanks !

---


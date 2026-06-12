---
title: "Maya 2016 will launch from command line but not from applications menu"
date: 2016-10-09
forum: General Help
---

### Post by dusanyu on 2016-10-09
Has anyone seen something like this before? adter the long process of installing maya on my UbuntuMATE 16.04 machine following the instructions found  at this page [https://fredrikaverpil.github.io/2015/09/10/installing-maya-2016-on-ubuntu-14-04-trusty/](https://fredrikaverpil.github.io/2015/09/10/installing-maya-2016-on-ubuntu-14-04-trusty/)   Just updating the steps to use the libraries found in 16.04

maya launches fine using /usr/autodesk/maya2016/bin/maya in the terminal however if I use  the .deskop file that is in the mate applications menu it crashes. 

i checked to verify that the commands were the same which they are (i pulled the command line call for maya from the .destop file) 

thanks for the help

---

### Post by kc1di on 2016-10-09
Looking at that install page.  He says > For some reason, not sure why, I can&#8217;t start Maya without root privileges. Let me know if you know why &#8211; or any other way I can improve this guide by commenting below!

Happy rendering!  That could be the problem. if you need root priviledges in the .desktop file go to the launch command in the file and place ```
gsku
```
in front of the command -- so it would look something like the following ```
gsku /usr/autodesk/maya2016/bin/maya
```  then it will ask for your password when you click on the menu item. 
Good Luck.

---

### Post by dusanyu on 2016-10-09
great idea but I fixed the necessity of Maya to run in root perms as running is an ugly solution.

I tried your suggestion anyway and it still crashes

---

### Post by kc1di on 2016-10-09
Does it spit out any error messages at all or just crash?
Seems like there must be some differences in the command used in the terminal and the command executed in the .desktop file.

---

### Post by dusanyu on 2016-10-09
no error at all the splash screen vanishes and the application does not load further.

at the moment i am loading 14.04 in a virtual machine and see if it has the  same wibble i can  live with loading from terminal :)

---

### Post by kc1di on 2016-10-09
could you post the command listed in the .desktop file here - Thanks

---

### Post by dusanyu on 2016-10-09
command is /usr/autodesk/maya2016/bin/maya

here is the destop files as shown by the Mate menu  editor 
[IMG]https://s9.postimg.org/gyg46eebz/Screenshot_at_2016_10_09_09_54_51.png[/IMG]

---


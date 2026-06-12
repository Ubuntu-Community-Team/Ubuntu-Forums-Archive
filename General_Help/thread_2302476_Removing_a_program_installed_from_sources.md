---
title: "Removing a program installed from sources"
date: 2015-11-10
forum: General Help
---

### Post by muhammadalidildar on 2015-11-10
I am using Ubuntu for development purpose and so I installed a development tool "YARP" from sources. For some reason I've to remove it completely and then reinstall. I tried 'apt' command and Synaptic Package Manager but surely it is not a solution to remove a program that was installed from sources. So please help me little.

Thanking you in advance.

---

### Post by oldos2er on 2015-11-10
Go back into the source code folder and run *sudo make uninstall*. I'm assuming you ran *sudo make install* to install the program (you didn't say).

---

### Post by TheFu on 2015-11-10
How ever the program was install is how it should be removed. A good INSTALL or README file would provide the steps to uninstall.  Sometimes it is just  **rm -rf /path/to/the/project/**  No need to over-think this.

Of course, if it is some sort of daemon, there are probably config files under /etc/, but maybe not.

---

### Post by muhammadalidildar on 2015-11-11
> INSTALL or README file would provide the steps to uninstall Courtesy: TheFu
> run *sudo make uninstall* Courtesy: oldos2er

Trying the above hints, I finally solved my problem. Thank you very much.[URL="http://ubuntuforums.org/member.php?u=338320"][COLOR=#C61919][B]
[/B][/COLOR][/URL]

---

### Post by oldos2er on 2015-11-11
Welcome.

---


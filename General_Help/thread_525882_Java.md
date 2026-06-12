---
title: "Java"
date: 2007-08-14
forum: General Help
---

### Post by oldtraveler on 2007-08-14
Why is it so difficult to install Sun Java?  I need it for Pogo games and have spent 2 hours trying to install the silly thing.  Other threads on this subject don't get the job done for me.

---

### Post by AlexThomson_NZ on 2007-08-14
Yep, it is probably harder than it needs to be.  At least as it moves to a  GPL complient license, it should be installed by default with future versions of Ubuntu (8+?)

Basicially, I download the .tar.gz, extract it to /usr/local, add it to my system path, and update the symbolic link in the /usr/bin directory.  I am not sure of the synaptic way (I do it my way for work reasons)

---

### Post by bettlebrox on 2007-08-14
sudo apt-get install sun-java6-plugin

works for me.

See here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by AlexThomson_NZ on 2007-08-14
Ahh you were just after the Firefox plugin, sorry, I thought you were after the whole JRE

---

### Post by oldtraveler on 2007-08-14
> **bettlebrox said:**
> sudo apt-get install sun-java6-plugin

works for me.

See here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Java_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)
I thought that was going to do it.  After the command it ran for a few minutes and then left me with an agreement form that wouldn't scroll to the bottom so that I could OK it.  Thus nothing happened.  No java.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem".   What does that mean?

---

### Post by bettlebrox on 2007-08-15
It means from a command line type:

sudo dpkg --configure -a

When the license aggreement comes up use the spacebar to scroll down. Then tab to select the OK and press Enter (if my memory is correct).

Luck

---

### Post by zvacet on 2007-08-15
> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

This will install Java and other things you will need.

---


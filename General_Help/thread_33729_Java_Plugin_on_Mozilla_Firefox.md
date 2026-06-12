---
title: "Java Plugin on Mozilla Firefox"
date: 2005-05-11
forum: General Help
---

### Post by Hambone_Linux on 2005-05-11
I have downloaded the jre1.5.0_02 and tried to install it on my Unbuntu and tried to get the plugin to work for the Mozilla Firefox.  When I try to connect to another pc's VNC program it does not come up saying that the plugin is missing but nothing show's up on the machine. Did i do something wrong or do I need to change the way I  installed it.  I am not really new to Linux i have been using it for about 6 to 7 months.  However I am new to Unbuntu and would appreciate any help that can be given.

Thank You

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=Hambone_Linux]I have downloaded the jre1.5.0_02 and tried to install it on my Unbuntu and tried to get the plugin to work for the Mozilla Firefox.  When I try to connect to another pc's VNC program it does not come up saying that the plugin is missing but nothing show's up on the machine. Did i do something wrong or do I need to change the way I  installed it.  I am not really new to Linux i have been using it for about 6 to 7 months.  However I am new to Unbuntu and would appreciate any help that can be given.

Thank You[/QUOTE]

Did you folow the Ubuntuguide instructions? I follow them to a tee and it ALWAYS works for me.

[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by Hambone_Linux on 2005-05-12
Okay thank you I got it to work just by following everything to the tee just like you said.  I have one more question for you if you could provide some help.  I have downloaded some things to my desktop and I am unable to delete them because it says that I do not have permission to change them.  there has to be a way to delete them but I am unable to find them.  If you know how to do it I would appreciate it.

---

### Post by tread on 2005-05-12
Well, one sure way to delete them: start a terminal, change to the directory you want to go to:
"cd path_name"
then
"sudo rm annoying_file_name"

Did you download the file as root or something?

---

### Post by fluideye on 2005-05-12
I too followed the instructions on ubuntuguide.org 

wget -c [http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin](http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin)
sh jre-1_5_0_03-linux-i586.bin
sudo mkdir /usr/java
sudo mv jre1.5.0_03/ /usr/java/

Then when I put in the next line

sudo chown -R root:root /usr/java/jre1.5.0_03/
**no such file or directory** 

Evidently it allowed me to move jre1.5.0_03 to /usr/java/ but where?  Not to that directory.  I've done a file search and can't find it anywhere.  

What should I do?  Start from the beginning and if I do that will it install all packages twice?

---


---
title: "How to install 3'rd party software?"
date: 2014-05-09
forum: General Help
---

### Post by Geir_Wathne on 2014-05-09
Hi. Im not experienced with linux and i dont figure out this:
I want to install Medusa 3d CAD software and has downloaded it as a 294Mb .sh file. If i try to install it using:
sudo install medusa.sh /opt
it only copies the .sh file to /opt
I dont know if /opt is the right folder, but if i dobbelclick the .sh file in a browser it openes a terminal window preparing installation and then the installation widow comes up as it should be. It suggests /opt as installation folder (thats why i have tried sudo to /opt) but the next screen tells me installation can not be performed without being super user. It doesnt help me to log in as admin.
I have to start the shell script somehow from the command line, starting with sudo, but what else should i write?
Anybody have a suggestion?

---

### Post by deadflowr on 2014-05-09
Thread moved to General Help

---

### Post by slickymaster on 2014-05-09
Hi Geir_Wathne, welcome to the forums.

According to [http://www.download.cad-schroer.info/m4_personal_512_install_en.pdf](http://www.download.cad-schroer.info/m4_personal_512_install_en.pdf) you need to have have the **csh** or **tsh** shell installed. If you don't, run the following at a terminal window:```
sudo apt-get install csh
``` and then try running again```
sudo ./medusa4_v4_0_0_linux_personal.sh
```

EDIT: You have to adapt the name of this file _medusa4_v4_0_0_linux_personal.sh_ to whatever one you've download

---

### Post by LastDino on 2014-05-09
It is generally like this

> CD Directory where/your/medusa.shfile/is


Then type in terminal while being in that directory
> sudo ./medusaxyz.sh

Not sure but I wanted to give it a try as I'm new to this scripting world as well. You can however wait for someone else to confirm this or suggest better way.

Oh, I got ninja'd. Glad to know I wasn't horribly off, though I didn't knew about the ''csh'' package >.>

---

### Post by kc1di on 2014-05-09
Go to the folder where you downloaded medusa.sh /  open a terminal and type:
```
sudo sh ./mdeusa.sh
``` 
 if there are no dependency errors it should install program.  if you hit errors post them here will try to help.
you should also read their installation guide found[ here.]("http://www.cad-schroer.com/fileadmin/Download/datasheet/MEDUSA4Personal-Installation-Guide.pdf")

---

### Post by LastDino on 2014-05-09
Ah, also, please post how it is fairing compared to Auto-CAD. I am also in need of CAD alternative which can deal with both 2D and 3D. Given you successfully install it ^^

---

### Post by Geir_Wathne on 2014-05-09
but i only get
sudo: ./medusa4_v5_2_1_linux_personal.sh: command not found
and when installing csh i get a message:
csh is already the newest version.
and trying to install tsh results in this:
sudo apt-get install tsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tsh

---

### Post by Geir_Wathne on 2014-05-09
I'm acing to try it out because autodesk inventor is to expensive

---

### Post by slickymaster on 2014-05-09
Did you mark _medusa4_v5_2_1_linux_personal.sh_ as executable before running it?
```
chmod +x medusa4_v5_2_1_linux_personal.sh
```and then afterward```
sudo ./medusa4_v5_2_1_linux_personal.sh
```

---

### Post by kc1di on 2014-05-09
> **Geir_Wathne said:**
> but i only get
sudo: ./medusa4_v5_2_1_linux_personal.sh: command not found
and when installing csh i get a message:
csh is already the newest version.
and trying to install tsh results in this:
sudo apt-get install tsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tsh
csh is installed, did you CD to the correct directory where you downloaded the file?  
make sure there are no miss types in the command. 
type ```
csh
``` then run the command I mentioned above.
also if your on a 64 bit machine and installed 64 bit Ubuntu you'll need the ia32-libs to run the programs.  If that is the case follow the instructions in[ this thread.]("http://ubuntuforums.org/showthread.php?t=2182653")

---

### Post by Geir_Wathne on 2014-05-09
Now it worked, thanks a lot for your help.
I wrote sudo sh medusa.sh
and the installation started. It needs 850Mb free space. Now it remaines to see if it is worth what it costs. I'll come back with details:-)

---

### Post by LastDino on 2014-05-09
> **Geir_Wathne said:**
> Now it worked, thanks a lot for your help.
I wrote sudo sh medusa.sh
and the installation started. It needs 850Mb free space. Now it remaines to see if it is worth what it costs. I'll come back with details:-)

Good! Now be sure to post here or directly on my profile so I can decide whether to check it out or not. And I read that it is free for personal use? 

Also, please mention if it supports Auto-CAD files or not (i.e .DWG).;)

---

### Post by kc1di on 2014-05-09
scratch that you need to do it this way. 
CD to the directory the file is fond in > 
open a terminal and enter ```
sudo csh
```
You should see a # at the beginning of the line enter the following ```
 sh ./medusa4_v5_2_1_linux_personal.sh
``` 
that will bring up the installer , follow the instructions.

---

### Post by Geir_Wathne on 2014-05-09
> **LastDino said:**
> Ah, also, please post how it is fairing compared to Auto-CAD. I am also in need of CAD alternative which can deal with both 2D and 3D. Given you successfully install it ^^

Hi, i was looking around in the program, and i think its easier for an autocad user to find your way around then for me. I haven't used autocad for some years. I've been using inventor that is purely parametric 3d drawing where you make drawings in model room and presents then in sheets. Here you obviously draw in the sheet you are going to print. Seems very good for 2d, but how good it is for parametric 3d i dont know yet.
Best of all, havent found any BUG's yet:-)

---

### Post by LastDino on 2014-05-09
> **Geir_Wathne said:**
> Hi, i was looking around in the program, and i think its easier for an autocad user to find your way around then for me. I haven't used autocad for some years. I've been using inventor that is purely parametric 3d drawing where you make drawings in model room and presents then in sheets. Here you obviously draw in the sheet you are going to print. Seems very good for 2d, but how good it is for parametric 3d i dont know yet.
Best of all, havent found any BUG's yet:-)

What format is it saving files in? Can it handle .dwg? That has been the real problem for me tbh :/

---

### Post by kc1di on 2014-05-09
Also if you using 64 bit you'll need to install lib32gcc.
also if your on a 64 bit machine and installed 64 bit Ubuntu you'll need the ia32-libs to run the programs. If that is the case follow the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=2182653").

---


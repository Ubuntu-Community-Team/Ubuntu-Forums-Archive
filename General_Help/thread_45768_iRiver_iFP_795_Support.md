---
title: "iRiver iFP 795 Support"
date: 2005-07-01
forum: General Help
---

### Post by pdev1961 on 2005-07-01
Hello all,
i just acquired the above MP3 player and much to my chagrin nothing happened when I connected it to my Dell Inspiron 1150 running Hoary.
What do I need to do to make it work?  I tried searching the forums but found nothing on the subject :(
Thanks
Pierre

---

### Post by StacyWebb on 2005-07-01
[go here](http://tuxmobil.org/player_linux_survey_iriver.html) 

This should take care of any issues make sure you get the deb file.

---

### Post by pdev1961 on 2005-07-01
Tracy
Thanks for your help, but I am a newb at Linux and not sure what to do when I get to there...

---

### Post by StacyWebb on 2005-07-01
ok, then go [here](http://sourceforge.net/projects/ihptool/) 

and download the tool, 
extract the folder and then
 cd into the directory
then run
./configure
make
sudo make install

I just added that because I don't know if you know how to install from a source file.

Instructions are located on the site on installing and running the app

Hope this works for you.

btw: it's Stacy not Tracy

---

### Post by pdev1961 on 2005-07-01
Oopps,
Sorry Stacy..

---

### Post by pdev1961 on 2005-07-01
[QUOTE=StacyWebb]ok, then go [here](http://sourceforge.net/projects/ihptool/) 

and download the tool, 
extract the folder and then
 cd into the directory
then run
./configure


Stacy,
I extracted the folder and cd to the directory but whe I continued I got this:

pierre@ubuntu:~/Downloads/ihptool-0.3.0$ ./configure
bash: ./configure: No such file or directory

---

### Post by Xjulle on 2005-07-01
[QUOTE=pdev1961][QUOTE=StacyWebb]ok, then go [here](http://sourceforge.net/projects/ihptool/) 

and download the tool, 
extract the folder and then
 cd into the directory
then run
./configure


Stacy,
I extracted the folder and cd to the directory but whe I continued I got this:

pierre@ubuntu:~/Downloads/ihptool-0.3.0$ ./configure
bash: ./configure: No such file or directory[/QUOTE]
Hello!
Probably the player works out of the box if you upgrade the firmware to ums (I have firmware 1.29 on my IFP799)

---

### Post by pdev1961 on 2005-07-03
[QUOTE=Xjulle][QUOTE=pdev1961]
Hello!
Probably the player works out of the box if you upgrade the firmware to ums (I have firmware 1.29 on my IFP799)[/QUOTE]

Right you are!

Working great now, thank you very much

Pierre

---


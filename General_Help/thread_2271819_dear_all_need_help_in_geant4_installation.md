---
title: "dear all need help in geant4 installation"
date: 2015-04-01
forum: General Help
---

### Post by medoo2 on 2015-04-01
dear all 
I am new using ubuntu
my version is ubuntu 14.04

I need your help in geant4 installation since I need to use this code in my study issue as medical physics 

please help me installing Geant4 , I have tried using informations from the internet , but I did not succeed .

thanks

---

### Post by anaconda on 2015-04-01
Isn't geant in the repositories..

I am currently in Debian 7, and geant321 is in debian reposotproes (so I assume a newer version will be in ubuntu repositories too..)

How about running this in terminal:
sudo apt-cache search geant

and then installing the version, that apt-cache search finds with:
sudo apt-get install geantXXX
(change the XXX with whatever apt-cache search found...

PS. Sorry that I am not currently on ubuntu -machine... then I could give better instructions..

---


---
title: "How to install Wine problem"
date: 2007-09-27
forum: General Help
---

### Post by bobmac on 2007-09-27
Folks,
I think I made a mistake by initially posting this to the ubuntuguide.org forum - my apologies.


I checked out the guide on how to install Wine. I note that its for the version before 7.4 which I have installed.

The instructions are:
sudo gedit /etc/apt/sources.list

* Add the following lines at the end of this file

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

* Save the edited file

Up to here appears to work OK

* Acquire public key

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -

but when I enter the above I get the following error
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

* Update and install Wine package

sudo aptitude update
sudo aptitude install wine


Does anyone know what I'm doing wrong?

Bob

---

### Post by zvacet on 2007-09-27
You mixed repositories,that´s what is wrong.Delete lines with wine repositories and save the file.After that 

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")



Or without wine repository go to synaptic> search box>type wine and that is it.You decide wich way you want it to do.

---


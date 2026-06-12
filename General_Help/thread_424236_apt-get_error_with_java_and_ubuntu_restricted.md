---
title: "apt-get error with java and ubuntu restricted"
date: 2007-04-26
forum: General Help
---

### Post by fletcherthunder on 2007-04-26
i used add/remove programs to install ubuntu restritected formats, macromedia flash, and java.  it downloaded and installed, i agreed to the java eula, but now every time i run apt-get anything, it pops up with this - 

Setting up sun-java6-bin (6-00-2ubuntu2) ...
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on sun-java6-plugin; however:
  Package sun-java6-plugin is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-plugin
 ubuntu-restricted-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)


i've looked everywhere for a fix, and tried 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo apt-get clean
sudo apt-get install --fix-missing
sudo apt-get install --fix-broken

i installed from the fiesty alternative cd, i haven't edited the sources.list, i just turned off the cd via "software sources.   any ideas on what i can do?

thanks!

---

### Post by zvacet on 2007-04-26
Do you have all repositories open?

---

### Post by fletcherthunder on 2007-04-26
i left the at the default, except i went in and uncommented the "backports" repositories.  i believe all of them are open be default, so that's the way i left them....

---

### Post by fletcherthunder on 2007-04-26
hmm, i removed the sun-java6-bin with apt-get remove, then seached for ubuntu-restricted, it showed it as "p", not "i", so i apt-get installed ubuntu-restricted , and it reinstalled java6-bin and plugin, and now it seems resolved....

---

### Post by zvacet on 2007-04-27
No,they are not open by default.Go to the system>administration>software properties and chek all boxes you find there.Reload.

---

### Post by Lucius Demon on 2007-05-01
:confused:  im thinking....like installing flash 9, you need a a 32-bit emulator program (if you are on 64-bit)  like nspluginwrapper. that is how i installed flash and its working. hopefully, this helps and id be willing to supply a link.

---

### Post by Lucius Demon on 2007-05-01
actually...use a program called automatix; it actually has a 64 bit version. @  getautomatix.com

---

### Post by zvacet on 2007-05-02
If you use Feisty

> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.



[https://help.ubuntu.com/community/Java?highlight=%28java%29]("https://help.ubuntu.com/community/Java?highlight=%28java%29")

---


---
title: "Stuck at 0% [Waiting for headers] - How to fix?"
date: 2013-09-19
forum: General Help
---

### Post by lanser2 on 2013-09-19
My system was working fine before I installed Pantheon, now after the installation, I can't install any package. I ran these commands: 
  
sudo apt-add-repository -y ppa:elementary-os/daily
  sudo apt-add-repository -y ppa:midori/midori-dev
  sudo apt-add-repository -y ppa:ricotz/docky
   sudo apt-add-repository -y ppa:marlin-devs/marlin-daily
  sudo apt-get update
  sudo apt-get install elementary-desktop

   and after that, I did:

  sudo apt-get remove elementary-desktop
  sudo apt-get remove pantheon
  now, whenever I try to install any package, I get stuck at stuck at 0% [Waiting for headers] - and when I do sudo apt-get update, I get stuck at 100% [Waiting for headers] - How can I fix this? please help.

---

### Post by lanser2 on 2013-09-19
Can anybody please help me? I am stuck!!!!!

---

### Post by oldos2er on 2013-09-19
Please wait 24 hours before bumping your post. We have forum members from all over the world, and it takes time for your post to be seen by everyone.

---

### Post by ibjsb4 on 2013-09-20
Apt-get remove is not how you remove PPAs.  Check out PPA Purge, a terminal program for removing ppa.  You can also add a GUI to it by install yppamanager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+uninstall+ppa&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+uninstall+ppa&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

---


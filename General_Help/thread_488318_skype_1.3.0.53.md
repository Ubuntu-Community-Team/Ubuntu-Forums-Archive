---
title: "skype 1.3.0.53"
date: 2007-06-30
forum: General Help
---

### Post by jrev on 2007-06-30
Hi all,
Do you know where I can find the package  
skype_1.3.0.53-1medibuntu1_i386.deb
which cannot be found any more on the Skype home page

this is to work with the Dapper version of ubuntu 

Il you have it in your archives i will give you the address of the man in need of it  

Thanks in advance for your help :D

---

### Post by JDMT on 2007-06-30
You could install Wine from [www.winehq.com](www.winehq.com) and just use the windows version.

---

### Post by McNils on 2007-06-30
[http://ftp.leg.uct.ac.za/pub/linux/medibuntu/pool/non-free/s/skype/](http://ftp.leg.uct.ac.za/pub/linux/medibuntu/pool/non-free/s/skype/)

---

### Post by badboy_24u on 2007-07-03
Type:

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then type: "sudo apt-get install skype".

Enjoy...

---


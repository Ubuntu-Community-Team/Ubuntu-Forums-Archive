---
title: "white screen"
date: 2008-03-02
forum: General Help
---

### Post by jwxie on 2008-03-02
hey folks, i am done with my dual OS, and trying to test with the xp and unbuntu

yet, the unbuntu seems not able to reconginze my video card i guess
cuz it appears to be "blank, white screen", which is strange to me

sorry i could not search at this site cuz i just reformted my own disk, so even with this xp i am using IE6...

My vdieo card is :
C.T. Tech. Radeon 9200SE

waiting for any reply is great!!!!!

(i did a bit research though)

i am going to use <control><alt><f1> so i can have some commands to run...

---

### Post by overdrank on 2008-03-02
> **jwxie said:**
> hey folks, i am done with my dual OS, and trying to test with the xp and unbuntu

yet, the unbuntu seems not able to reconginze my video card i guess
cuz it appears to be "blank, white screen", which is strange to me

sorry i could not search at this site cuz i just reformted my own disk, so even with this xp i am using IE6...

My vdieo card is :
C.T. Tech. Radeon 9200SE

waiting for any reply is great!!!!!

(i did a bit research though)

i am going to use <control><alt><f1> so i can have some commands to run...
You may try and reconfigure you xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jwxie on 2008-03-02
okay thank you very much 
here is my solution about the white screen

first
sudo dpkg-reconfigure -xserver-xorg
configure them, you can read from here
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)


then
you have to upgrade your video driver and system as well
sudo apt-get update
sudo apt-get upgrade

third
during the last 3 mins of the "get upgrade", the screen may appears to become black, totally black, don't freak out, wait for another 5- 10 mintues, it should turns into the "LOGIN Screen"

and then login

---


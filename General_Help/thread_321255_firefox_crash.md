---
title: "firefox crash"
date: 2006-12-18
forum: General Help
---

### Post by kadkad19 on 2006-12-18
i have installed now ubuntu 6.10 (edgy)
all is working fine . sound video etc ....
1 thing ,,
firefox crash when i go into flash i installed flash :

"..........To install Macromedia Flash Player 7 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Macromedia Flash Player requires two font packages
      to be installed, gsfonts and gsfonts-x11.

Press ENTER to continue..........."

well after install it when i go into youtube or website with flash firefox CRASH
"
NOTE: Macromedia Flash Player requires two font packages
      to be installed, gsfonts and gsfonts-x11."
used apt-get install
to install those package 
"gsfonts-x11 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."
gsfonts same ....

i also tried to installed by click on the flash when its uninstalled ...
same probalm
also tried ubunto "add/remove" in application .
** now i delete the /home/user/.mozilla/All_Files_Were_Here**

well what should i do ? 
to make firefox support flash ?
*first time i use ubuntu but not first time for linux .

tnx

---

### Post by raul_ on 2006-12-18
[http://www.ubuntuforums.com/showthread.php?t=320227&highlight=firefox+flash]("http://www.ubuntuforums.com/showthread.php?t=320227&highlight=firefox+flash")

If this doesn't work try searching the forums. I'm pretty sure i saw that question a couple of times

---

### Post by kadkad19 on 2006-12-18
raul ...
tnx but thats didnt work ...
any other suggestion ? and i did not found any help in the search :S

---

### Post by raul_ on 2006-12-18
[http://www.ubuntuforums.com/search.php?searchid=11410951]("http://www.ubuntuforums.com/search.php?searchid=11410951")

one of these oughta work :D

---

### Post by kadkad19 on 2006-12-18
well i solve it .
with some help from the forum ... but they just make it more complicated O_o"
go in adobe labs site ...
download
FP9_plugin_beta_112006.tar.gz
flash player 9 ...
put into
/home/~userName~/.mozilla/plugins/
extrat the libflash ...
and like a magic ...

---


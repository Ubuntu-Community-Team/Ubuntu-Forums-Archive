---
title: "rcconf missing"
date: 2005-11-01
forum: General Help
---

### Post by danron on 2005-11-01
Hello.

I can't find the rcconf program anywhere on my HD after a clean 5.10 install. Not even apt-cache search rcconf gives any hits, so of course apt-get install rcconf doesn't work either. All other programs I tried to install has been working just dandy :) with apt-get. Could it be that I'm using the wrong repository for apt? 

Please, any help would be greatly appreaciated.

---

### Post by trash-can on 2005-11-01
Try update-rc.d! This is the debian-way of managing services!

---

### Post by Schmots on 2005-11-01
I actually just installed rcconf last night.

you need to edit your apt sources (/etc/apt/sources.list)

Comment out your cdrom and then uncomment out all the others except the last set of backports (they failed on my system) then

sudo apt-get clean
sudo apt-get update
sudo apt-get install rcconf

Smile, have a nice day

---

### Post by danron on 2005-11-01
Schmots, your directives worked perfectly - thank you!

update-rc.d I will learn later, now I just want my machine up and running.

---


---
title: "Permission error &quot;d?????????&quot; on USB"
date: 2015-02-23
forum: General Help
---

### Post by Julian_Gonzalez on 2015-02-23
Hello recently my USB stop showing a folder from my USB, I have only used this USB on my linux OS "Ubuntu 14.04 LTS". The USB is a 32GB Sandisk and this folder "Donwloads" have most of my important files.

I check the USB on the terminal but "ls" doest shows the folder neither, I checked it with "ls -al" and the folder is present but shows some strange folder permissions. (Check screenshot)

[ATTACH=CONFIG]260183[/ATTACH]

It says permissions d?????????? and owners date size blocks clock as ?.

Any help I dont want to lose those files.

Thank you

EDIT: found this on Github "https://gist.github.com/ipedrazas/5bd43acaf03ae9541ca5" but it doesnt work at all.

---

### Post by coldraven on 2015-02-24
You could try using PhotoRec, it can find many file types. To get it you must install testdisk
```
sudo apt-get install testdisk
```
Then run PhotoRec
```
sudo photorec
```

See here for more info: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Ruben_van_Smirren on 2015-02-24
try to chmod the directory "sudo chmod 0777 Downloads"

---


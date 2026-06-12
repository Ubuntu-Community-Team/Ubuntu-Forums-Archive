---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-05-18
forum: General Help
---

### Post by fastian12 on 2013-05-18
Hello all i am very bad in linux OS knowledge so if i miss basics or make some too basics mistakes Kindly forgive me! I am recently switched to Ubuntu and all what is that i wanted to try Ubuntu 12.10 desktop environment **"AWESOME" . **Website told me to run this Command in Terminal **" sudo apt-get install awesome "** so i did but this happened **E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.** So i again ran this command which successfully proceeded. Then again i tried to install Awesome environment but now such error came and is not removing. I don't know how to fix it! Help!

Error is : [B]E: Sub-process /usr/bin/dpkg returned an error code (1)

And [/B]i am using **lenovo B570e** machine

Intel Core i3-2330 2nd Generation
Hard Drive 500GB
RAM 4GB
Graphic Card 1.7GB
Processor 2.2 and 2.2 64bit

I hops this will help!:(

---

### Post by fastian12 on 2013-05-18
**and please be general in language too complicated or LINUX language causes much trouble! Thanks again!**

---

### Post by ibjsb4 on 2013-05-18
In terminal try:

```
sudo apt-get -f install
```

Get any errors?

---


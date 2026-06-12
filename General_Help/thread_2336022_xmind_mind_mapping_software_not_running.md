---
title: "xmind mind mapping software not running"
date: 2016-09-03
forum: General Help
---

### Post by wajdlee2 on 2016-09-03
hi guys I have downloaded xmind on my ubuntu 16.04.1 after installation I tried to run the software and have given me the following error 

An error has occurred. See the log file
/home/wajdlee/.xmind/configuration-cathy_linux_64/1472930368981.log.

---

### Post by howefield on 2016-09-03
Perhaps you could share the relevant part of the log file as our resident clairvoyant has the weekend off ?

Just joking but it would probably be helpful for others to know what the error is.

---

### Post by wajdlee2 on 2016-09-03
I have shared the log file on my google drive 

[https://drive.google.com/open?id=0B9gcpP3Q36jBQkVGRkowQnVMRDQ](https://drive.google.com/open?id=0B9gcpP3Q36jBQkVGRkowQnVMRDQ)

sorry for bothering seems complicated issue

---

### Post by dragonfly41 on 2016-09-04
I don't use Eclipse or xmind but reading your log it seems that you have a bunch of "Unresolved requirements".

e.g.
Unresolved requirement: Require-Capability: osgi.ee; filter:="(&(osgi.ee=JavaSE)(version=1.7))"

Read one suggested answer in this thread ...

[http://stackoverflow.com/questions/24669940/java-8-missing-required-capability-require-capability-osgi-ee-filter-osg](http://stackoverflow.com/questions/24669940/java-8-missing-required-capability-require-capability-osgi-ee-filter-osg)

It may be a matter of setting your xmind.ini file in ~/.xmind to point to your Java path.  But I'm guessing.

---

### Post by wajdlee2 on 2016-09-04
thanks I will see what I can do

---


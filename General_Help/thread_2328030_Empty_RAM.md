---
title: "Empty RAM"
date: 2016-06-16
forum: General Help
---

### Post by Seth-666 on 2016-06-16
[COLOR=#111111][FONT=Helvetica]How can i clean up my RAM memory, empty ram , just the standard OS system without affecting the applications. Not Reset app . just eampty ram . just like that a click and cache is 0 , standard ... ?[/FONT][/COLOR]

---

### Post by Seth-666 on 2016-06-18
serious? nobody knows? top 1 linux desktop and no answer?  cool :| 
bad support

---

### Post by RobGoss on 2016-06-18
Hello and welcome, What version of Ubuntu are you using?

This app will work on just about any version of Ubuntu [Bleachbit ]("https://www.bleachbit.org/") it cleans the system and removes unwanted files also will also free up space on your machines it works well for me and I have been using it for some time. It also frees up memory as well

---

### Post by Seth-666 on 2016-06-18
on my pc, ubuntu 14

---

### Post by RobGoss on 2016-06-18
> **Seth-666 said:**
> serious? nobody knows? top 1 linux desktop and no answer?  cool :| 
bad support


Please keep in mind the members here at Ubuntu forums are** volunteers** and do not get paid to provide support so keep this in mind when asking your questions and it may takes a few hours before your questions are answered.

---

### Post by banceu_sergiu_ione on 2016-06-18
I believe that there is just 1 way to free you ram completely >>> * Shut Down * the machine. Otherwise, the OS will always use a small amount of ram in order to can run : )

But if you look to clean your system you can run the fallowing commands:

> sudo apt-get autoclean

> sudo apt-get autoremove

if you run the 16.04 version, it can be used only * apt *

---

### Post by deadflowr on 2016-06-18
I doubt you'll ever be able to set the cache to zero, as anything running will need some memory cached.
The simplest method to clear out as much used cache though is to run as root:
```
sync; echo 3 > /proc/sys/vm/drop_caches
```
alternatively you can run something like this as a regular user with sudo:
```
sync;echo 3 | sudo tee /proc/sys/vm/drop_caches
```
or really any variation of sync and changing the value to 3 in the drop_caches file will do.
You then run the command whenever you want to clear up some cache.

Some user even put the command in cron and set it run every so often automatically.

A rather quick and brief overview on what the command does here:
[http://www.linuxinsight.com/proc_sys_vm_drop_caches.html]("http://www.linuxinsight.com/proc_sys_vm_drop_caches.html")

---


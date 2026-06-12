---
title: "wont let me make folder in / or  Filesystem?"
date: 2008-03-26
forum: General Help
---

### Post by iFost on 2008-03-26
HI im a complete noob and i need to make a folder for an online game i play (Runescape) in / or filesystem in order to use signed java, isntead of unsigned (takes a lot longer to load etc) i was jsut wondering if n e one could help me step by step.. thankyou.

---

### Post by danwood76 on 2008-03-26
What are you exactly trying to do?
this thread:
[http://ubuntuforums.org/showthread.php?t=585350](http://ubuntuforums.org/showthread.php?t=585350)

has relevance.
the last post says to make 2 directorys to make firefox cache the java, .file_store_32 and another called .jagex_cache_32.

so in terminal do:
```

mkdir ~/.file_store_32
mkdir ~/.jagex_cache_32

```

restart firefox and see if it works.

-- edit --

I just did this and went to runescape and loaded the signed java applet up so it should work.
Hope it helps!

---

### Post by iFost on 2008-03-26
Alright thankyou... i made those... but i still get that error... heres a pic of it.... i also tried 
mkdir ~/.rscache   but i still get that error =[

---

### Post by bobthebob1234 on 2008-03-26
Check the permissions on the folder. It will be only read and writable by you by default!

---

### Post by jken146 on 2008-03-26
It asks you to create a directory, /rscache

Open a terminal (Applications -> Accessories -> Terminal) and use this command: ```
sudo mkdir /rscache
```
Then it asks you to set the permissions so that all users can read and write to it.  ```
sudo chmod -R a+rw /rscache
```

---

### Post by iFost on 2008-03-26
im still getting that error... i tried all of the above ^^ maybe its the java im using?

---

### Post by bobthebob1234 on 2008-03-26
Have you looked at the runescape FAQ section, like it says to?

try a different or more upto date java.

---

### Post by danwood76 on 2008-03-26
When I wrote my last post I created those 2 directories and went to runescape and it worked.
Loading the signed java session up and asking me to log in. I dont play runescape so I couldnt login.

I just tested on my laptop I run purely for work and it created the directories automatically when I started playing.
I think there must be some issue with your java install.

---


---
title: "[SOLVED] I cant install programs on Gutsy.. Help!!!!"
date: 2008-02-26
forum: General Help
---

### Post by pogztimz on 2008-02-26
hello to all.. i installed gutsy gibbon on my acer aspire 4715z laptop just a while ago, my problem is i cant install packages like DevHelp, Anjuta, Lazaruz, Gambas and many others.. everytime i tried to install something a msg window appears.. i pasted a link of wat i see if i add a program.

[http://farm4.static.flickr.com/3274/2293479152_fe93c5ea2c.jpg](http://farm4.static.flickr.com/3274/2293479152_fe93c5ea2c.jpg)


pls help me on this.. ty..

---

### Post by Yellow Pasque on 2008-02-26
Can you run this command for me?:
```
uname -a
```

---

### Post by pogztimz on 2008-02-26
sure.. here it is..

[http://www.pastebin.ca/918643](http://www.pastebin.ca/918643)

---

### Post by Yellow Pasque on 2008-02-26
There seems to be some sort of conflict where it's looking for the 386-compatible kernel and you're running the i686-generic SMP version.

---

### Post by pogztimz on 2008-02-26
so do u have any idea on how to resolve this? i really help.. i need those packages.. plsssss.....

---

### Post by Yellow Pasque on 2008-02-26
Go to System -> Administration -> Software Sources and enable all of the software sources on the first tab.
Now look in System -> Administration -> Synaptic Package Manager
Are they listed in there?

---

### Post by pogztimz on 2008-02-26
ok, it's done.. what am i suppose to see in there? didnt quite understand what u said in the last part...


P.S. packages are listed in there.. if that's what u meant?..

---

### Post by Yellow Pasque on 2008-02-26
Look for the packages you want to install. Use the search button to do it quickly.

---

### Post by pogztimz on 2008-02-26
OMG!!!!:) it worked.. ty a lot... i love u man... God Bless u..... :)

---

### Post by Yellow Pasque on 2008-02-26
You're welcome :)

---


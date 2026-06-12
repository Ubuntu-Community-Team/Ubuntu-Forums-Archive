---
title: "Q: Install Eclipse on Hoary?"
date: 2005-09-01
forum: General Help
---

### Post by Aero-Z on 2005-09-01
Is it possible to install Eclipse on Ubuntu 5.04 and how it can be done? Or is there any specific program like Eclipse for Ubuntu?

Thanks :)

---

### Post by KingBahamut on 2005-09-01
It is possible. 

If you have Java installed properly on your system, you should be able to compile from source and run with no problems. 

I dont normally use or wouldnt normally use Eclipse though. 

Anjuta, Kdevelop, and Bluefish/Nvu are the IDEs that I use when I do use one.

---

### Post by Aero-Z on 2005-09-01
[QUOTE=KingBahamut]
Anjuta, Kdevelop, and Bluefish/Nvu are the IDEs that I use when I do use one.[/QUOTE]
Which one of these programs are the most user-frendly and easy to install?

---

### Post by KingBahamut on 2005-09-01
Anjuta is the most intuitive in my opinion. 

Bluefish and Nvu are HTML / Wed Dev apps, so they dont count for developing Java much, which is what I suspect you want eclipse for.

---

### Post by shakin on 2005-09-01
Kdevelop is my favorite. It's very well done.

---

### Post by Pikapooh on 2005-09-02
You don't need to compile Eclipse from source. Just download binaries from their site and unpack, for example to /opt/eclipse or ~/eclipse.

Other nice free IDE is NetBeans (ok, don't like it personally but... :>) or if u want smth more lightweight - JEdit.

Considering java related development Eclipse is far more advanced IDE than Anjuta (it is primary C/C++ IDE). But... it is opensource all - download and try it ;-)

---

### Post by void_false on 2005-09-02
Dont we have Eclipse in repos?

---

### Post by lol on 2005-09-02
> Dont we have Eclipse in repos? 

Not in hoary repos. To install Eclipse, I added the breezy repositories to my sources. I had to upgrade a couple of libs, but not too many. You have to play a bit with apt preferences tough, otherwise it's going to do a full upgrade.

By the way, Eclipse doesn't compare with Anjuta, Kdevelop, or any other IDE for that matter. I wouldn't recommend it if you don't want to develop in Java, but if it's the case Eclipse is definitely the only IDE worth mentioning.

One of my friend teaching OO programming told me that students were able to gain 3 months on a one year project ever since they started to use Eclipse, and I honestly believe it. Try it for real during 1 month, and you will never be able to go back to another IDE... the productivity gain is just too amazing.

---

### Post by Pikapooh on 2005-09-02
[QUOTE=lol]By the way, Eclipse doesn't compare with Anjuta, Kdevelop, or any other IDE for that matter. I wouldn't recommend it if you don't want to develop in Java, but if it's the case Eclipse is definitely the only IDE worth mentioning.[/QUOTE]

Nah, there is many high-quality Java IDE. Eclipse is just one of them.

---


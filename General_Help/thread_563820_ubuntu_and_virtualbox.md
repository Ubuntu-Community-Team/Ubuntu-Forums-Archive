---
title: "ubuntu and virtualbox"
date: 2007-09-30
forum: General Help
---

### Post by dellboy on 2007-09-30
ok i want  to run virtualbox on ubuntu i have ubuntu 7.04  on my computer 

when i try to run the program i get this error: Dependency is not satisfiable :libxalan110

how do i get this to run on ubuntu i am a newbe lol 

i want to have ubuntu as my main os and just run xp if i need with virtualbox or maybe MAC or vista not sure yet lol 


Thank you 
for your 

Help

---

### Post by ryanVickers on 2007-09-30
First of all, I congratulate you on your selection of probably the only **good** virtualization software available :p

VMware is really slow and bad :p

I would just search for it and download it and put it in /lib

or you could reinstall it... Sounds like you've just got a deb package and it's missing stuff - I would recommend finding the package for it in the repositories - or [automatix - install it here!]("http://ubuntuforums.org/showthread.php?t=455753")

---

### Post by dellboy on 2007-09-30
ok  after a few  ubuntu  updates i can know run the deb file but when i run it is says 
i you can only run one software management  tool. as fair as i know i am .Can some help me 

i  am still a ubuntu noob lol 

can some help me 
and i am Glad that i have chose to use one of the best programs lol l :)

---

### Post by ryanVickers on 2007-09-30
You can only have one software manager open at once ex. update manager OR add/remove OR the .deb installer thing

---

### Post by maybeway36 on 2007-09-30
Can't you just add the APT source and the key? That's what I've always done.
To do it, you could even just type in the terminal:
```
sudo echo "deb http://www.virtualbox.org/debian feisty non-free" >> /etc/apt/sources.list
wget -q -O- http://www.virtualbox.org/debian/innotek.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox
```

---

### Post by dellboy on 2007-09-30
i am not running any other software manager tools :(

---


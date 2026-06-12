---
title: "Compiling and getting stunnel to work"
date: 2007-10-03
forum: General Help
---

### Post by ccpower on 2007-10-03
Complete newbie here. I downloaded the source for Stunnel, and to some minor success maybe even compiled it... i don't know. Running Kubuntu 7.10 beta.

./configure =/usr/lib/ && make && sudo make install  <-- is what i ran from the Konsole, it gave me some errors about not finding my SSL library installation, which i fixed with

sudo apt-get install libssl-dev

...and tried the first command again. It did something for a while and just said

make[2]: Leaving directory `/home/user/Desktop/stunnel-4.20'
make[1]: Leaving directory `/home/user/Desktop/stunnel-4.20'

and now what? Is it compiled? If it is, what do i do to get it working? If not, how does it get done?:confused:

---

### Post by cubeist on 2007-10-03
If you installed it correctly then you can run it from the konsole by typing the name of the program plus any options... so "stunnel [options]" enter

If it isn't installed, try those commands you entered one at a time

./configure

make

sudo make install

---

### Post by ccpower on 2007-10-03
Now it says mail.pem is missing. I assume i'd need to create some sort of an encryption key file? I read some instructions on that part, but...

God damnit, why is there no ready binary newsreader with SSL-support and at least 10 if not more concurrent connections for Linux? This is the only thing keeping Windows on my box at the moment, if not for this hassle i'd switch instantly.

And, it's the only program/issue i'm having trouble with, and this is my first day with Kubuntu. Not too bad for a dumbass.

---

### Post by cubeist on 2007-10-03
well, when compiling a program from source you do have to make sure you have all the dependencies installed before trying to compile.  I just downloaded a copy and tried compiling and it went aok... I am using gnome though... but that shouldn't really matter.  I don't know what mail.pem is... something to do with securing email I would imaging... perhaps try compiling without that package if you don't need it.

---


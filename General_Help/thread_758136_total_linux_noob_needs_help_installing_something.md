---
title: "total linux noob needs help installing something"
date: 2008-04-17
forum: General Help
---

### Post by mpc827 on 2008-04-17
okay so i downloaded nestra, so i could play NES games on my ps3's ubuntu OS which i just installed. so yeah i got a folder full of files and the readme says "run makefile" but when i double click it, it appears as a text file. how do i install this?

---

### Post by Joeb454 on 2008-04-17
Ok, so can you try this for me :)

Open up a terminal, from Applications>Accessories

Then use the 'cd' command to get to the directory it is saved in...say it's on your desktop, in a folder called nestra, you would run the following commands (1 line at a time!):

```
cd ~/Desktop/nestra
./configure
./make
sudo make install

```

When you run the last command, it will ask for your password, though not show anything being entered (it is being entered :))

---

### Post by mpc827 on 2008-04-17
ok so i got the directory selection working
but when i type ./configure it says
bash: ./configure: no such file or directory

and i just skipped it and did ./make, same thing was said

so then i did just "make"
and a ton of weird errors popped up.

---

### Post by qwalton on 2008-04-17
I just did a search in synaptic package manager and nestra is in the repositories so it would probably be easier for you to use synaptic to install nestra.  

just go System>administration>synaptic package manager and enter your password when it asks for it.

Once synaptic is open click on the search button, type in nestra, click the check box next to the nestra, click on mark for installation, and finally click the apply button to install the program.

---

### Post by strabes on 2008-04-17
qwalton is 100% right. Given your level of experience, forget about compiling things from source. Just install from the repositories. You could open a terminal (Applications > Accesories > Terminal) and run these two commands to install it:[code]sudo aptitude update
sudo aptitude install nestra[/code

You could also use the graphical method qwalton described.

---


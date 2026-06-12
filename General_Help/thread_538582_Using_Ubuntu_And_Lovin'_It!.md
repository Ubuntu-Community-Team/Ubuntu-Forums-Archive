---
title: "Using Ubuntu And Lovin' It!"
date: 2007-08-30
forum: General Help
---

### Post by adidaq on 2007-08-30
Okay. here's the story:

I AM PROUD TO BE A USER OF UBUNTU LINUX.

after a few minor issues after first installing ubuntu (waaaay back) I became very comfortable with the OS. it's simple to use, fast, efficient, and the program range is ALOT larger than i thought initially.

theres only a few TINY things i'm a bit curious about.

The first is a program I'm having a TINY BIT of trouble installing. 
( I pretty much found how-to guides on here (for which i am very grateful ^_^ ) for every application i couldn't find on synaptic)
But I can't seem to find any guide on how to install a gamecube emulator. 
(There is one called 'Gcube" url: [http://gcube.exemu.net/](http://gcube.exemu.net/) but i don't really have any ideas on how to install it, as i have never installed anything on my own.) 
Could someone please find/make a noob-friendly install guide?
I would REALLY appreciate it ^_^

the second thing, is a little more difficult to explain.
my 'top bar' is somewhat cluttered with applications and launchers 
(such as the "shut down" , trash can, clock, audio properties etc. )  
is it possible (like in mac) to enable a function/install an application that allows you to tap the mouse scroll (or use some keyboard command) to open up a sort of on-screen 'menu', that features these applications/menus?
this would clear up alot of clutter on my top bar, and make working alot easier for me.
I would REALLY appreciate it, if someone could tell me if this is possible.

THANK YOU IN ADVANCE. ^_^

---

### Post by jusmurph on 2007-08-30
I think you should check out gimmie for your menu problems
[http://www.getdeb.net/app.php?name=Gimmie](http://www.getdeb.net/app.php?name=Gimmie)

And it looks like you need to compile the Gcube... My assumption would be along the lines of:

You need to terminal to the extracted folder:

```
cd ~/Gcube... (whatever the location is)
```

then in the terminal:

```
./configure
make
make install
```

---

### Post by phillips321 on 2007-08-30
before using make and make install you might need to install "build-essentials" from synaptic

---

### Post by adidaq on 2007-08-30
Thank you everyone for your help!

I'm attempting to install gcube as we speak :D

unfortunately, gimme is'nt quite what I'm looking for. thank you anyway ^_^

---

### Post by por100pre1 on 2007-08-30
> **phillips321 said:**
> before using make and make install you might need to install "build-essentials" from synaptic

build-essential without an s:

```
sudo aptitude install build-essential
```

---

### Post by adidaq on 2007-08-30
Sorry to double-post, but both me and my very linux-savvy friend have tried installing it (the emulator), and failed. can anybody try and help?

---

### Post by jusmurph on 2007-08-30
I'm sure we could try... but that would require some details from you!

---

### Post by adidaq on 2007-08-30
what details would you like?

---

### Post by adidaq on 2007-08-31
Can someone please help me? ^_^;

---

### Post by kesman on 2007-08-31
could you post the output of the commands make and make install please? Without them it's quite hard to see what the problem is and try to solve it :F

---

### Post by Lord Illidan on 2007-08-31
Type ./configure in a terminal, and then give us the output. Normally, ./configure would fail because it needs a library that you don't have installed. In that case, from the output given we can see what library you need.

You might like this link : [http://en.wikipedia.org/wiki/Configure_%28computing%29](http://en.wikipedia.org/wiki/Configure_%28computing%29)

---


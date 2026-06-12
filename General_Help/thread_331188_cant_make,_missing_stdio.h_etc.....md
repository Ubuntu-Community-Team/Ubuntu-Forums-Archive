---
title: "cant make, missing stdio.h etc...."
date: 2007-01-04
forum: General Help
---

### Post by sdowney717 on 2007-01-04
I am trying to compile martian_modem and when I run make i get many errors due to several missing c compiler files.
namely
stdio.h
mman.h
string.h
signal.h
unistd.h

and on and on and on.

I installed ubuntu 6.1 from a live CD I bought from ubuntu on a 32 bit HP PC running 2.O ghz

So I am missing the developer environment?

How do I get and install it?

thanks

---

### Post by taurus on 2007-01-04
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by sdowney717 on 2007-01-04
thanks!
BUT
I am trying to get the modem to work in ubuntu, so I can only right now download from windows. I do know the martian_modem program works as I was able to make it in fc6.
So how do I download from windows?

---

### Post by taurus on 2007-01-04
The build-essential is on the CD!!!  So, insert the CD and from a terminal, run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by sdowney717 on 2007-01-04
thanks, that worked for me. I was able to compile martian_modem.

Now, I set up the modem but, how do I activate the modem?
I setup the modem in networking.
In fc6 I just click the activate and it dials, but I dont see a dialup activate for the modem in ubuntu.

---


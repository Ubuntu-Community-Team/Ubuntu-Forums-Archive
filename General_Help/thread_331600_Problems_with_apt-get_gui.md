---
title: "Problems with apt-get gui"
date: 2007-01-04
forum: General Help
---

### Post by nsabatino on 2007-01-04
hey guys,

I installed Easy Ubuntu to get some stuff on my new Edgy install. It downloaded all the packages fine until it got to flash-nonfree.

Sort of funny, but when i selected the stuff in the miniature console to and hit control - c to paste it here so you could see, i geuss its a shortcut to skip the package? anyways, it did everything else fine, but is now stuck on downloading this one package flashplugin-nonfree.

What should I do now?

Thanks

-Nick Sabatino

---

### Post by bruenig on 2007-01-04
try
```
sudo apt-get -f install
```

---

### Post by nsabatino on 2007-01-04
> **bruenig said:**
> try
```
sudo apt-get -f install
```

Sorry... I should do that in another terminal WHILE "Applying Changes" is running/frozen?

---

### Post by bruenig on 2007-01-04
Just get out of that installation and then do it. If you want to ctrl + c it or close the terminal and reopen it, however you want to do it.

---

### Post by khedron on 2007-01-04
Lol - Ctrl-C in the console means "end current program". To copy and paste from the console, select the text with your mouse. Then middle click into the textbox and the selected text will be pasted there. Very handy sometimes.

Anyway, paste the error here so we can take a look at it.

---

### Post by nsabatino on 2007-01-04
Ha. Well, shows what I know. Heres a screenie:

[BIG SCREEN SHOT HERE]("http://i119.photobucket.com/albums/o141/nicksabatino/Screenshot.png")

Thanks Guys

---

### Post by bruenig on 2007-01-04
Oh you are in gui, I guess I should have realized that from the name of the thread. Get out of that however you can, if you need to force it to quit go ahead, but just exit out of that. Then run that sudo apt-get -f install in the terminal.

---

### Post by khedron on 2007-01-04
I have to go to bed now, but if what bruenig suggests doesn't work, try the following in a console:
Dpkg can clear up any problems with existing packages that have half-installed:
dpkg --configure -a 

If that doesn't work, could you try to get the actual text of the error by scrolling up in the console?

---

### Post by nsabatino on 2007-01-04
```
nsabatino@Nick1:~/easyubuntu$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
nsabatino@Nick1:~/easyubuntu$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading... 

```

And I'm back where I started...

Any suggestions?

EDIT: Is this a bug? Should I put this in Bugzilla?

---

### Post by bruenig on 2007-01-04
This is not a bug, you stopped apt-get in the middle of it doing something. Sometimes apt-get won't stop running, you either need to kill it or restart, and then do 
```
sudo dpkg --configure -a
```
assuming sudo apt-get -f install doesn't work.

---

### Post by nsabatino on 2007-01-05
> **bruenig said:**
> This is not a bug, you stopped apt-get in the middle of it doing something. Sometimes apt-get won't stop running, you either need to kill it or restart, and then do 
```
sudo dpkg --configure -a
```
assuming sudo apt-get -f install doesn't work.

Well, I stopped it only because i left it going while I went out today. I was gone for almost 5 hours. Maybe it's trying to download from the wrong place??

---


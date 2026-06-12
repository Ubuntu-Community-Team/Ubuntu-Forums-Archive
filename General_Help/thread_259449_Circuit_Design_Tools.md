---
title: "Circuit Design Tools"
date: 2006-09-17
forum: General Help
---

### Post by rekahsoft on 2006-09-17
I am looking for some circiut disign tools that are open source and are writen for gnome. I have looked at the gEDA Project ([http://www.geda.seul.org/](http://www.geda.seul.org/)) but wasn't impressed...i just want to know if there are any other circuit design tools that meet my specification. I am lookig for a PIC simulator (something like gpsim which i couldn't get to work), schematic design tool and circiut board editor. gEDA has all of these tools but they did not look that good...am i wrong? What do you use? Thanks for your input :)

---

### Post by calvinthomas on 2006-09-19
Did you install Geda through Synaptic? If you did then it doesn't work at all properly, infact it quite simply doesn't work at all except fo gschem, i'm not sure why. If you download the iso file, mount it and install from there it will install properly (although I had to get some dependencies) beware, it compiles every package from source and so takes a while to install (on my computer about 50mins I think, Turion 3000+, 512Mb Ram). Having said that, I got it for my Dad he used Ares & Isis on windows and I don't think Geda is as easy to use as that but he said it does looks good.

If you search in the forums for Geda, there is a post started by me (its top of the search at the moment) that has installation instructions by someone else on. 

They seem to have it installed perfectly, i'm still having some problems with gspiceUI (the GUI for the simulator) and Geda itself (i.e. the project manager) neither of these are essential however.

I'm not sure of any other open source software but if you come up with any you think are better please let me know! If you do go for Geda its a good idea to look at the documentation on the geda site, there are lots of tutorials and stuff which make it easy.

Alternatively, if your prepared to pay then there is Eagle (or for free Eagle lite if you only need small boards with one layer)which is native to Linux and is supposedly one of the best on the market (although i've heard it isn't the easiest to use)

Finally, perhaps you could use whatever you use in windows via wine although i'm not at all sure if it would work!

Calv

---

### Post by rekahsoft on 2006-09-19
ok thanks

---

### Post by nousefreak on 2006-12-21
Is there a way I am able to make eagle to run with wine

when i do i get weard signs in stead of words

[http://users.telenet.be/de_lotus/eagle_under_wine.jpg]("http://users.telenet.be/de_lotus/eagle_under_wine.jpg")


I realy need to get this working because my project for school needs to be finished end of May

---

### Post by nousefreak on 2008-03-13
Solved


You can install eagle with sudo apt-get install eagle

stupid of me to try and wine it :p

---


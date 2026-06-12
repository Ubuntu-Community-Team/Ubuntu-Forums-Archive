---
title: "Is There a Great Karnaugh Map Generator/Minimizer/Solver for Linux?"
date: 2008-05-16
forum: General Help
---

### Post by SendDerek on 2008-05-16
Hello All!

I'm taking an digital design class and I'm finding that I spend most of my design time building and solving k-maps from a truth table.  I'm really hoping that there is a software package out there for Linux that automates this process.  I've seen a few already, namely [Karnaugh Map Minimizer](http://k-map.sourceforge.net/), [Boolean Expression Solver](http://linux.softpedia.com/get/Science-and-Engineering/Mathematics/Boolean-Expression-Solver-30928.shtml), and [Karnaugh Minimizer (Windows Only)](http://karnaugh.shuriksoft.com/).  These didn't seem to fit the bill.  I couldn't get the first installed ([same problem this guy had](http://ubuntuforums.org/showthread.php?t=356195)), the second is a CLI based solution, but it didn't look like it was going to do what I wanted it to, and the third isn't free.  The third option looks like it has some very powerful functionality, but I don't want to pay for a windows only program.

I guess what I'm asking is this:  If you're a computer engineer, what software programs do you use to aid you in the design process?  I'm up for any suggestions that you may have.

Thanks in advance,

-Derek

---

### Post by MaindotC on 2008-05-16
I didn't know about the Karnaugh Map Minimizer - wish I had when I was taking Digital Electronics last semester! You get a star for showing me this program.

The only digital design programs (if you call them that) I found where in the Add/Remove Software feature in the Education section.  Ksim and Klogic.

---

### Post by SendDerek on 2008-05-16
Well, thanks for the quick response with suggestions.  I very quickly looked into the programs you suggested and they just don't seem to do what I would like.  Besides, they seem old...

The Karnaugh Map Minimizer looks promising!  I tried to run it using the linux binary but I just couldn't get it to run.  I tried running the windows version in wine, and everything installs just fine, I can enter in the values just fine, but when I hit "solve" it locks up.  So, I'm done there.  Maybe I can compile it from source, but... I dunno.  That seems like a lot of trouble.

---

### Post by SendDerek on 2008-05-16
I found a pretty good one!  I would recommend this over the other solutions I mentioned before:

[http://www.inf.ufrgs.br/nangate/index.php?option=com_content&task=view&id=52&Itemid=51](http://www.inf.ufrgs.br/nangate/index.php?option=com_content&task=view&id=52&Itemid=51)

It's called Karma and it does a really good job!  Easy to use and is powerful enough for what I would like!  

Thanks for any help!

---

### Post by SendDerek on 2008-05-16
Another good program that I found is called Espresso.  The program and it's description can be found here:

[http://diamond.gem.valpo.edu/~dhart/ece110/espresso/tutorial.html](http://diamond.gem.valpo.edu/~dhart/ece110/espresso/tutorial.html)

Linux, Windows, Sparc downloads:
[http://fke.utm.my/downloads/espresso/](http://fke.utm.my/downloads/espresso/)

More instruction:
[http://www1.cs.columbia.edu/~cs4861/s07-sis/](http://www1.cs.columbia.edu/~cs4861/s07-sis/)


It's just a CLI program.  Neat program though.  I wish there was something for Linux that utilized the algorithm in a nice GUI!

Oh, and to run the espresso.linux file, you have to make it an executable first:
```
sudo chmod +x expresso.linux
```

Then run it in the terminal ```
./expresso.linux
```

Here's the "man" page for espresso:

[http://fke.utm.my/downloads/espresso/espresso.1.html](http://fke.utm.my/downloads/espresso/espresso.1.html)

---

### Post by MaindotC on 2008-05-16
Dude you da man - I'm not taking any ELEC classes this semester but over the break I'm going to crack open my dig electronics book and redo some problems and use some of these 1337 programs.  I remember I had such a difficult time understanding Karnaugh minimization above 2-input.  Just didn't understand about the grouping.  I googled and googled and all I found was a clip on youtube that was in spanish.  Thank you for whatever searching you did :)

---

### Post by bukka on 2010-10-24
The great visualizer of Karnaugh maps is Bmin. You can download it from [http://code.google.com/p/bmin/](http://code.google.com/p/bmin/)

---

### Post by DaveGK3 on 2011-09-26
> **SendDerek said:**
> Hello All!

I'm taking an digital design class and I'm finding that I spend most of my design time building and solving k-maps from a truth table.  I'm really hoping that there is a software package out there for Linux that automates this process.


Sorry about I'd popup old topic. 
There is the cool software for it - it's created special to prevent wasting time and remove pen and paper from developing process. Software is named "Gorgeous Karnaugh" and placed on [http://gorgeous-karnaugh.com]("http://gorgeous-karnaugh.com") site. Currently there is only Windows version, but the Linux version will coming soon.

---

### Post by oldos2er on 2011-09-26
Closed for necromancy.

---


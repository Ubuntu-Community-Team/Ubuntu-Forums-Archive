---
title: "CAD for Ubuntu"
date: 2007-10-03
forum: General Help
---

### Post by greenstar on 2007-10-03
**CAD for Feisty 7.04**

I saw a question about CAD on Ubuntu over at [pcmech]("http://www.pcmech.com/article/windows-to-ubuntu-transition-guide#comment-722") and was sure I had seen CAD packages for Ubuntu. I didn't reply at pcmech because I thought the chances of the right people actually seeing my reply would be slim, so I am posting this on the Ubuntu forums.

I did a quick search in synaptic and found QCad & PythonCAD in the repositories. QCad is in the main repository, PythonCAD is in the universe repository. They can be installed from terminal with:
```
sudo aptitude install qcad qcad-doc partlibrary
``````
sudo aptitude install pythoncad
```I also saw several other packages that seem to have CAD functionality. These are:
SagCAD is in universe, to install:
```
sudo aptitude install sagcad sagcad-doc
```VARKON is also in universe, to install:
```
sudo aptitude install varkon varkon-user-manual varkon-programmer-manual
```Electric is for electrical/electronic CAD applications:
```
sudo aptitude install electric
```If those don't do it for you, these 2 pages have many more links to CAD packages for Linux:
[http://www.tech-edv.co.at/lunix/CADlinks.html](http://www.tech-edv.co.at/lunix/CADlinks.html)
[http://www.tech-edv.co.at/lunix/UTILlinks.html](http://www.tech-edv.co.at/lunix/UTILlinks.html)

Hope this helps,
Greenstar

---

### Post by por100pre1 on 2007-10-04
Can you please provide some feedback on which are the better programs? Many people ask for CAD programs so it would be great to know which ones are the best. Thanks for posting! :)

---

### Post by greenstar on 2007-10-08
> **por100pre1 said:**
> Can you please provide some feedback on which are the better programs? Many people ask for CAD programs so it would be great to know which ones are the best. Thanks for posting! :)

Sorry, you'll have to try them yourself. I don't use CAD because I don't know a thing about it except for the meaning of the acronym: Computer Aided Drafting. 

I went the extra mile to find out what CAD software was available in the repositories and the web, and I don't even use CAD. Now you or someone who actually uses CAD is going to have to pick up the ball from here and give us field reports on the quality & functionality of those packages. I can't do it *all* for you.

Go ahead, try them. If you decide you don't like one of them and want a complete removal of the package then just swap 'purge' for 'install' in the commands listed in my previous post.

I just know how to find things. My unofficial title when I was in the army was SFC - as in Scrounger First Class. I could always be counted upon to 'appropriate' and/or 'liberate' supplies and/or equipment that were needed to complete the mission. This often meant looting the supplies/equipment from 'neighboring' units or departments, manipulating central supply, and sometimes just simple. old fashioned improvisation. I never cared, as long as the job got done. 

As an aside, I bet you're an American. Unfortunately, my fellow countrymen are far too easy to identify - for all the wrong reasons.
 
Greenstar

---

### Post by greenstar on 2007-10-08
Whoops! The refresh button reposted my last. Sorry folks.

Greenstar

---

### Post by Steveway on 2007-10-08
Since we use CAD at our work (Autosketch 8 and it sucks, so many bugs), I also looked what was avaiable.
I didn't try all very intensive but the best, in my opinion, are:
Qcad
Kicad (seems to be good for electrical schemas)
Qcad seems to be as featurefull as autosketch 8, minus autosketch's annoying bugs.

---


---
title: "Ubuntu OpenOffice Wizards hang"
date: 2007-06-22
forum: General Help
---

### Post by thegitksan on 2007-06-22
Good evening all. My OpenOffice.org 2.04 wizards will only partially work. For example, in BASE, the Tables and the Reports wizards will function, but not the FORMS wizard. Ther are others that are partially functional like this.

I dug around at the OpenOffice.org support website to see what I could find and they explicitly said that distros like Ubuntu (there are others) tinker with the OOo code to make it fit more easily within their distro. Unfortunately, this also means that higher level functions like wizards are hit-and-miss functional too. They recommended I contact the Ubuntu community and ask politely for a fix for this very (very) common problem. This is one of their most common problems, according to one post i read at OOo, that of distros tinkering (for best of intentions) and finding that useful stuff becomes lost or broken as a result.

FYI, the FORMs wizard runs almost all the way through my choices, but stops right at the very last stage, refusing to save my choices of form, and choosing to exit only tosses the wizard-derived results into ether.

Any ideas what I can do? Should I upgrade beyond the 2.04 OOo to the most recent 2.2.1 version and just install it in place of what came pre-installed with Ubuntu 6.10? Will it even install if Ubuntu had to tinker it before including it in a standard installation?

Best,
Russell in Canada

---

### Post by thegitksan on 2007-06-22
Nobody really interested, hey? I just watched the next post after me jump by hundreds of views and many posts, all within a few minutes.

O well, c'est la vie. Ba-bye.

---

### Post by swisscow on 2007-06-22
A little patience, waiting 2 mins between asking for help and then asking why you haven't got any isn't very long. Anyway, I have just got out of bed and can help you so here we go:

You are correct in saying the Ooffice in UBUNTU has been played round with and I have had exactly the same problems you are experiencing. I read many texts about Java being the culprit but couldn't pin it down so I just dumped the whole thing and then installed a completely new/untampered version from the openoffice website. This is how I did it:

[LIST]
[*]Cleaned out open office through Synaptic
[*]Installed alien through synaptic
[*]Download the tarball from the open office web site to the desktop and extracted it
[*]Renamed the extracted folder to something easier, like office
[*]Then in terminal:
[/LIST]

```
cd Desktop
cd office (or whatever you called the extracted folder)
cd RPMS
sudo alien --scripts --keep-version *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb
```

It takes a little time for Alien to convert the rpms to debs so be patient ;)

Good luck

---

### Post by thegitksan on 2007-06-23
hmmm.
Thank you for your carefully ordered reply. I deeply appreciate the time you've taken to answer my question. I've no idea at all what "alien" means here, but I will take that to mean homework on my part to learn what the beast is.

You instructions are explicit and to the point. I will endeavour to follow them and report back what transpires.

All my best,
Russell in Canada.

ps: it was much, much longer than 2 minutes I waited, despite the forum's reporting mechanism. It was more like 4-6 hours. I've no control over the time the scripts report I made my remarks, and I generally trust scripts to be time-correct, but in this case, it was not so. I suspect it's a glitch in the way the forum takes in and then processes new entries. Not sure. Even so, it was a long time before I saw movement. Assigning no blame of course in any direction.

---

### Post by swisscow on 2007-06-23
My apologies - I saw 2 mins between the posts but as you say, the time mechanism is perhaps not so reliable.

To clarify alien - it's a little program you can download via synaptic which converts rpms to debs. To explain, Ubuntu and some other linuxes use a sort of package (basically a 'box' in which the program is wrapped up) called debs, whilst other versions use a packaging called rpm. With Ubuntu, it's a lot easier to work with deb packages. 

However sometimes a deb version of a piece of software is not available, it may only be packaged in rpm format. This is where alien comes in.

Let me know how you get on with alien - I have had no problems doing the conversion of ooffice to deb but if it stuffs up there are deb versions available, may take a bit of searching though.

---

### Post by bsawler on 2007-06-23
Hello Swisscow,

I followed your instructions above.  I downloaded the tar with JRE. 

Everything installed, but when I run openoffice.org Base and I click on Tables I get an error

JRE is Defective
OpenOffice.org requires a Jave runtime environment (JRE) to perform this task.  The selected JRE is defective. Please select another version or install a new JRE and select it under Tools - Options - OpenOffice.org - Java.

I really need BASE to work, and I have now gone from bad to worse. Any suggestions?


Regards,
Bradley

---

### Post by bsawler on 2007-06-23
Russel in Canada, 

1. To install alien, go to System > Administration > Synaptic Package Manager
2. Search > alien
3. Mark for installation
4. Apply

Bradley 
(Canadian in Viet Nam)

---

### Post by swisscow on 2007-06-23
I hate Java problems!! Possible solutions:

[LIST]
[*]Ok, I see you are using Ubuntu 6.10. I am using 7.04 - Feisty and all the Java stuff (I am using standard, I have added nothing extra) works fine. So you could install Feisty but that is a bit drastic.

[*]Try selecting a different Java - tools options - Java. Be aware it takes a few moments for the Java you have installed to appear. I am using ths standard blackdown java but also have 1.6 installed

[*]Do a search for similar problems on this forum. I can guarantee someone else has had this problem before and perhaps they found a solution (like I said earlier, I installed the new version as above to solve mine)

[*]Use another database - Kexi is pretty good (KDE but will run happily in Gnome)


[/LIST]

Sorry I can't be anymore help and it's a shame that the alien method above didn't work so well. I wish you luck

---

### Post by bsawler on 2007-06-23
Thanks swisscow. 

I am running 7.04.  I had this same silly problem of the wizard not working.  The old Java stuff is way out of my league.  I installed Java Plugin Control Panel (1.4), Java Policy Tool (1.4), Sund Java 6 Plugin Control Panel and Sun Java 6 Policy Tool.  Not sure what all they really do, but when I use tightvnc to connect to my mothers computer in Canada the old Java app fires up and runs ok.

I will trying reinstalling the Java components and see what happens and will check the forum to see if I can resolve this unfortunate event.  Does not help that I am new to Linux...

Cheers,
Bradley

---

### Post by swisscow on 2007-06-23
Hey Bradley, good to have you on board.

I find it hard to believe that the main office suite has these problems - and a lot of people have them. I don't know if it's just with Ubuntu or other linuxes have these problems too. I do know that open offfice depends on Java for the bells and whistles like the wizards - but the wizards make life a lot easier. I used to work with MSAccess a lot and for initial set up of a form, you couldn't beat the wizard.

One thing that may be worth considering if you need it is that open office base isn't a relational database manager - possibly a reason to try another. And there are lots more.

Anyway, that's my 2 pence worth. Hope your problems are resolved as painlessly as possible.

And I still HATE java problems!!!!

---

### Post by bsawler on 2007-06-24
Ok fixed... very simple.  I thought I would post in case someone has the same issue.

After installation I ran BASE and got the following error that I stated in the prevous message

```
Please select another version or install a new JRE and select it under Tools - Options - OpenOffice.org - Java.

```

Now while it was late I did not realize that the message told me how to fix this.  I was looking under OpenOffice.org Base setting... not what the message says. 

Therefore if you go to (in Openoffice) Tools > Options > OpenOffice.org > Java you select the a version (I selected the most current 1.6 as this comes with openoffice 2.2, and there was also a 1.4 that was a default install on ubuntu).  

Restart OpenOffice ... all works well. All Tables > Queries > Forms > Report Wizards work. 

Swisscow - I found this after search on another post.  Thanks 

Back in business! For now!

Thanks,
Bradley

---

### Post by swisscow on 2007-06-24
Fantastic - I will make a note of this myself for future reference.

These forums are great - I've yet to be unable to solve a problem.......famous last words!

---

### Post by timrichardson on 2007-06-26
What do you mean OpenOffice Base is not a relational database manager? It supports SQL on data sources, just like Access, and this includes the embedded database format that comes with Base.

---

### Post by thegitksan on 2007-07-02
Okay then. I tried exactly as you suggested, marking everything already installed that was part of the existing OOo package group. 'Twas a bit scary doing it, cos if I blew it on the next steps it would all be gone.

Installed alien, and then working from RPMs from a DVD I ordered for version 2.2.1, copied the RPMs to an install folder, and aliened them all. It did take a while, thanks for the warning.

Then dpkged the works, and everything seemed to install fairly quickly. Finished the installation with the menu dpkg in the extra folder, and it all seemed to work fine.

Tested the wizards and immediately got the error message saying java was not yet installed. Checked it and it was installed, simply not yet selected. I selected the latest version installed, a 1.6.<something>, and restarted the OOo. Upon restarting, tested again, and it all worked just fine.

Thanks guys, for the help. Definitely appreciated.

Russ in Canada

---

### Post by BCtom on 2007-07-14
Thank you so much for this guys, I had given up on Open Office because of the broken wizards until I came upon this  thread; this How-To really helped me along. I followed the instructions, and set up the java first, and everything worked right from the start--like a charm.  The whole process took about 45 min, but it was worth it to have the wizards working. Creating forms with the wizards is way better than setting them  up from scratch.

Perhaps Ubuntu will have this Java thing fixed by the time the next release of  Open Office comes by???? *hint*

Tom from Canada  :)

---


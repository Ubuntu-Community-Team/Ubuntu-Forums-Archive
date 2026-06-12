---
title: "Dreamweaver alternative ..."
date: 2005-10-17
forum: General Help
---

### Post by dbee on 2005-10-17
I sometimes do php/html/css work and I'm familiar with the dreamweaver way of doing things. 

Unfortunately though, there really doesn't seem to be an alternative on linux ...

I've tried nvu and it's works fine but it doesn't have php support ...
I've also heard that dreamweaver doesn't work too well on those crossover, wine implmentation things ...

Has anyone else encountered the same problem ?
What did you do to resolve it ?

---

### Post by raublekick on 2005-10-18
try Bluefish. I use Macromedia Homesite+ both at home and at my job. Bluefish seems like a fine replacement for most of the stuff I do.

---

### Post by dspp on 2005-10-18
Try NVU. You should be able to install it via apt-get or Synaptic.

---

### Post by geekydiv on 2005-10-18
If you are used to code completion for tags and their attributes in html, you should try screem. its pretty neat

---

### Post by cytoplasm on 2005-10-18
Quanta Plus is another one to consider.

---

### Post by rykel on 2005-10-18
[QUOTE=dspp]Try NVU. You should be able to install it via apt-get or Synaptic.[/QUOTE]

if anybody is thinking of installing NVU easily, try the autopackage version. simply go to [http://www.autopackage.org/packages](http://www.autopackage.org/packages) and look for NVU.   :)

---

### Post by afonic on 2005-10-18
[QUOTE=rykel]if anybody is thinking of installing NVU easily, try the autopackage version. simply go to [http://www.autopackage.org/packages](http://www.autopackage.org/packages) and look for NVU.   :)[/QUOTE]

Autopackage sure is nice, but since there is a package in the repositories for Nvu I don't really see why he should use it and not just find it and install it through Synaptic.

---

### Post by strongmantim on 2005-10-25
[QUOTE=afonic]Autopackage sure is nice, but since there is a package in the repositories for Nvu I don't really see why he should use it and not just find it and install it through Synaptic.[/QUOTE]

Why am I not finding Nvu in the repositories? I have all of them enabled, as well as a few extras. ;)  All of them are updated, as well. (BTW, I am using Hoary, which may be the answer to my question)

---

### Post by rykel on 2005-10-25
[QUOTE=strongmantim]Why am I not finding Nvu in the repositories? I have all of them enabled, as well as a few extras. ;)  All of them are updated, as well. (BTW, I am using Hoary, which may be the answer to my question)[/QUOTE]

now u know why i recommended you to use the autopackage Nvu...   :KS

---

### Post by waffen on 2005-10-25
If you are in Breezy try AddProgram>Programming its appears in the soft list...

---

### Post by benplaut on 2005-10-25
it's a myth that dreamweaver dousn't work well in CXoffice... i haven't found any problems except for some odd errors popping up occasionally, but they never hamper doing anything. 

cxoffice includes a cool little script that makes "preview in browser" still work :D

---

### Post by AgenT on 2005-10-25
NVU is in the universe repository, which may be disabled on your system. Just enable it and you should be able to install it without problem.

And never use Autopackage unless you REALLY have to (that is, it's not in any repository). It's just not a good idea for a lot of reasons (no matter what the pro-autopackage people tell you). But this is not the place to discuss autopackage's pros and cons.

---

### Post by rykel on 2005-10-26
[QUOTE=AgenT]And never use Autopackage unless you REALLY have to...[/QUOTE]

excuse me, are you anti-autopackage? why should we "not" use autopackages when it is REALLY soooo easy to install our favourite firefox, nvu, gaim, abiword etc.?

i suggest tat everybody give autopackage a try, before criticising it.

just becoz it works like a windows/mac installer doesn't mean it's bad...

---

### Post by monkey89 on 2005-10-26
[http://www.licquia.org/archives/2005/03/27/autopackage-considered-harmful/](http://www.licquia.org/archives/2005/03/27/autopackage-considered-harmful/)
[http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys-2005-03-28-14-20.html](http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys-2005-03-28-14-20.html)

Just a few pages that came up on a quick google.  I think the idea is that its a better idea to use apt and synaptic when the software is available in the repositories (which it is, as said above) then to install an autopackage which is done right in the system directory and can create conflicts later.  Windows and mac don't have package management, which is why you need installers there.  On the other hand, Linux does, and it makes life easier.

Is it really easier to search online for a gaim autopackage which could be who knows where when you could just click on Install in synaptic, or type "apt-get install gaim" in a terminal?  Your call, not mine, but I prefer going with the package management.

-Monkey

---

### Post by dbee on 2005-10-26
So, I think I like bluefish the best ... but unfortunately it doesn't seem to support templates.

Is this true, or am I just imagining it ??

---

### Post by Thomas,Bakker on 2006-02-06
to install NVU just type the following in the terminal

[COLOR="Red"]**sudo apt-get install nvu**[/COLOR]
(you will be asked for a password its the same as your login pasword)

done you just installed NVU, its that easy no need for an autopackage
whit this install. 
oh by the way [COLOR="RoyalBlue"]**you will now find NVU under applications / internet **[/COLOR]

-*EDIT*-

its also easy to remove NVU whit the terminal
just type;
[COLOR="Red"][B]
sudo apt-get remove nvu[/B][/COLOR]
(you will be asked for a password its the same as your login pasword)
[COLOR="Red"]**when asked to remove type j**[/COLOR]

done you just remove nvu

-*EDIT*-

---

### Post by MarioFrick on 2006-02-06
I prefer Screem to NVU by far, and also to Bluefish. I was used to use DW as well, but since I got used to Screem I'm feeling really comfortable and all the code I write is much cleaner than with any WYSIWYG editor...

---

### Post by akiro.yamamoto on 2006-02-06
I've used Dreamweaver and Flash MX (not MX 2004) with wine 0.93 and it woks well.

---

### Post by dlai on 2006-02-07
According to the WineDB it should be possible to make it run, but not install: [http://appdb.winehq.org/appview.php?versionId=3673]("http://appdb.winehq.org/appview.php?versionId=3673")

---

### Post by nursegirl on 2006-02-07
[QUOTE=dbee]So, I think I like bluefish the best ... but unfortunately it doesn't seem to support templates.

Is this true, or am I just imagining it ??[/QUOTE]

You're right, it doesn't :(

---

### Post by curuxz on 2006-02-07
Erm guys they said in their orignal post that they had tryed nvu and did not like it for its lack of php support so why keep recommending it? (personaly i dont use it for the same reason). My vote goes with quanta I use it every day and its a great app, scream and bluefish are also quite good but for some reason I just prefer quanta :)

---

### Post by z_diver on 2006-02-07
I also use Quanta plus.  It's the only KDE/QT app I really like better than the Gnome/GTK equivalents.

As far as QT dependancies go, not an issue.  It only pulls in 2 small libraries from what I remember and upon exiting it shuts down whatever processes it started up.

---

### Post by dbee on 2006-02-19
Hi again,

wow, it's been a while since I posted my first message ... and thankfully I can say that now I do most of my web development on linux ... yippeee !

For php I use bluefish ... just because ! ... I'm sure quanta and the others are great as well.

As a dreamweaver alternative there are some outstanding extensions for the firefox browser that I do all my html and css work with. Try out codetch, css editor, color picker, ruler, web developer ... there's probably a few more that I'm not listing. 

None of them are perfect, and some aren't even finished properly ... but they still kick dreamweaver's butt IMO \\:D/    
... take that macromedia - for tying your products to the world's third best OS

---


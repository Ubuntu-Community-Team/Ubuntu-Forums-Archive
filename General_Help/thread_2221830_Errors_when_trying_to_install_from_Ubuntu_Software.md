---
title: "Errors when trying to install from Ubuntu Software Center"
date: 2014-05-03
forum: General Help
---

### Post by jbaerboc on 2014-05-03
Hey All,
  Just started having this issue recently. Wondering if anyone has come accross it and knows how to fix it? I can use synaptic just fine but would like the option to use the official Ubuntu Software Center as well. This is on a fully up-to-date 14.04 Ubuntu install. This happens for anything I try to install, screenshots are an example.

[ATTACH=CONFIG]252818[/ATTACH][ATTACH=CONFIG]252819[/ATTACH]

---

### Post by jbaerboc on 2014-05-04
I'm surprised no-body knows :-(

---

### Post by jbaerboc on 2014-05-04
Hmm ok so I think I figured out the problem. I ran gksu software-center in the terminal and was then able to install. Also if I try to run Synaptic from the unity panel it will not start but if I run gksu synaptic it runs fine. I think what's happening is that the su password prompt is not coming up when attempting to launch from Unity. Synaptic icon blinks like it's trying to launch but never get the su prompt. Software center also never prompts me when trying to install something. 

Never heard of this type of issue before, has anyone else?

---

### Post by jbaerboc on 2014-05-05
Bumpit

---

### Post by ian-weisser on 2014-05-05
How, exactly, did you install 14.04?

If you installed afresh from the normal 14.04 Desktop image, I don't  quite see how you could have a perfecty-working install but a borked  PolicyKit. It usually takes a lot of work to screw up PolicyKit.

The specific error you showed us means that user does not have permission to add/remove software. That's why you needed to gksu it.

---

### Post by ibjsb4 on 2014-05-05
I have had this happen to me on a fresh install.

My work-a-round for synaptic.

Open your text editor with

```
gksudo gedit /usr/share/applications/synaptic.desktop
```

and comment (#) out

> #Exec=synaptic-pkexec

then add this line below it

> Exec=gksudo synaptic

Save and close
Your launcher should now work.

I don't know if this will work with the software center, don't have it installed.

---

### Post by jbaerboc on 2014-05-05
> **ian-weisser said:**
> How, exactly, did you install 14.04?

If you installed afresh from the normal 14.04 Desktop image, I don't  quite see how you could have a perfecty-working install but a borked  PolicyKit. It usually takes a lot of work to screw up PolicyKit.

The specific error you showed us means that user does not have permission to add/remove software. That's why you needed to gksu it.

Fresh install, no changes aside from installing steam, wine, etc...and regular updates that the update manager advised. And it worked fine until about 5 days ago. I'm betting some update came through and didn't apply correctly but what do I know? 

Also Software Center has always asked me for a password before installing something [not at start-up like Synaptic does]. So not sure what your experience has been but lets not get all feisty just because someone has a problem you haven't seen before ;-).

---

### Post by jbaerboc on 2014-05-05
> **ibjsb4 said:**
> I have had this happen to me on a fresh install.

My work-a-round for synaptic.

Open your text editor with

```
gksudo gedit /usr/share/applications/synaptic.desktop
```

and comment (#) out



then add this line below it



Save and close
Your launcher should now work.

I don't know if this will work with the software center, don't have it installed.

Thanks will give that a try when I get home tonight. I'm betting a similar edit would work for Software Center as well.

 I like Synaptic better and use it more often but if I'm supporting a Linux distribution I try to use or at least acknowledge the software center for that distro.

---

### Post by jbaerboc on 2014-05-06
Alrighty so that fixed my Synaptic and I applied the same knowledge to the Software-Center. I created a new file named Software-Center.desktop [text document] and I put this in it:

[Desktop Entry]
Name=Ubuntu Software Center
GenericName=Software Center
Comment=Ubuntu's Software Center
Exec=gksudo software-center
Icon=software-center
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic

---

### Post by Kafshiel on 2014-08-27
I know this is not the proper thread but it's very late and my patience is being quite tested by this. Before of this day I could install Ubuntu Software Center in Lubuntu just by sudo apt-get install ubuntu-software-center or in case I could be suffering from mild Alzheimer would open Synaptic Package Manager, search for the package which is ubuntu-software-center and then install from Synaptic. But not so today. Nope Synaptic doesn't know about ubuntu software center although it knows about ubuntu kylin software center. So what has happened to Ubuntu Software Center in the joyful Lubuntu distro? Should I install Xubuntu instead? Is[FONT=arial, sans-serif] t[/FONT] his a bad YouTube movie? No but seriously: where's the Ubuntu Software Center? Coz I cannot run Ubuntu on this old piece of computer crap but yes I do love this old computer. Should I kill the computer coz Ubuntu won't share that piece of slow-mo, full of bugs, retarded code that they call Ubuntu Software Center? C'mon is there a PPA now or what? I'm tired and I might be being rude all along (you bet pal) but before was just: sudo apt-get install ubuntu-software-center. What is it now? Blow jobs to Canonical?
thanks in advance for any help although considering my rudeness I will understand that nobody will help me. I'm thinking about those Linux newbies and how I was one of them in 2013 and how things have changed for the worse, the Ubiquity installer doesn't ask anymore to "install alongside Windows" it just assumed the same stupid Microsoft attitude of: go frack yourself this is Linux (I'm sorry what?) and if you can't dual boot by preparing partitions and blabla blabla we are excatly like Microsoft now. Frack the newbies and this is the Ubiquitous installer good luck you Windows users. Yeah I was very sad after I saw the new Ubiquitous installer. I«'m very sad now for you all. So now hear this hear this: you have 2 choices as I see it: 1: you don't give a frack 2: you will consider new users. You will either go down as assholes or you will come up as persons. This is for all the Ubuntu and Buntus ecosystem. I'll personally make sure that your name and distros are down in the mud in every corner of the Internet if you do continue this ridiculous imitation of Microsoft arrogance. I will make sure that everybody knows about this. So you thoink all the above is a fairy tale? No unfortunately it isn't. It's the truth. When I first saw the new Ubiquity installer I said "hmm... I won't talk coz let's see if they change it" but no it wasn't changed. But this you should know: sometimes the voice of the few goes a long way. I don't even care about the Ubuntu Software Center now. There are other distros out there that don't imitate the Microsoft arrogance, I don't really need this crap out of any Buntu nor from Canonical. Frack you and good ridance!

---


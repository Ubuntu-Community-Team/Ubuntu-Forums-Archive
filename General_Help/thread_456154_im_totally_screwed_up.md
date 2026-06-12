---
title: "im totally screwed up"
date: 2007-05-27
forum: General Help
---

### Post by ayush3090 on 2007-05-27
hello guys im new to linux

im using ubuntu 7.04 feisty fawn

n im not bale to get any sound.............ive got problem with codecs and drivers and stuff

i want drivers for realtek HD audio ......... and a "HOW TO" on its installation

plus i want drivers for mp3 playback and acually all the codecs that are required to play general files

and is there a way to run *.exe files in linux

thanx in advance

---

### Post by Kobalt on 2007-05-27
[Here]("https://help.ubuntu.com/community/DebuggingSoundProblems") is some help for your sound problem.
For the multimedia, see [this]("http://ubuntuforums.org/showthread.php?t=413624").
No, .exe files are specific to Windows, you cannot run them in Ubuntu.

---

### Post by strabes on 2007-05-27
Actually, to install restricted and proprietary codecs you can simply install the ubuntu-restricted-extras package if you're using feisty. See [this](https://help.ubuntu.com/community/RestrictedFormats) page for more info.

exe files are windows programs. If the program is worth using the developers will provide a linux version.

---

### Post by Alterax on 2007-05-27
Some .exe files will run through Wine.  There are tutorials out there, so I won't take up too much time on the subject.

But be forewarned:  Wine is not a panacea for the Windows to Linux switch.  I've had problems with many programs running on it, and there just comes a point where you decide whether or not that particular program is worth the headaches.  Then you adapt, either by dropping the program entirely or looking for a native Linux equivalent.

Surprisingly enough, the Linux programs are often better.  Part of that is because they are often built by large groups of volunteering developers who are free to design programs with the kinds of functionality they want to use.  

Best of luck to you!  

--Alterax

---

### Post by ayush3090 on 2007-05-27
> **strabes said:**
> Actually, to install restricted and proprietary codecs you can simply install the ubuntu-restricted-extras package if you're using feisty. See [this](https://help.ubuntu.com/community/RestrictedFormats) page for more info.

exe files are windows programs. If the program is worth using the developers will provide a linux version.

guys im getting this error - The use, modification and distribution of Ubuntu restricted extras is restricted by copyright or by legal terms in some countries.
Ubuntu restricted extras cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by Kobalt on 2007-05-27
Have you tried [this way]("http://ubuntuforums.org/showthread.php?t=413624") ?

---

### Post by ayush3090 on 2007-05-27
> **Kobalt said:**
> Have you tried [this way]("http://ubuntuforums.org/showthread.php?t=413624") ?

[IMG]http://xs215.xs.to/xs215/07210/Screenshot.png[/IMG]

---

### Post by ayush3090 on 2007-05-27
ahh the problem is that im not able to download an of these things

plus whenever i try to install something i get errors

:(

---

### Post by taurus on 2007-05-27
Close synaptic.  Open a terminal, Applications -> Accessories -> Terminal, and see what happens when you run these two commands.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ayush3090 on 2007-05-27
> **taurus said:**
> Close synaptic.  Open a terminal, Applications -> Accessories -> Terminal, and see what happens when you run these two commands.

```
sudo aptitude update
sudo aptitude upgrade
```
another problem - [IMG]http://xs215.xs.to/xs215/07210/ubuntuuuu.png[/IMG]

---

### Post by taurus on 2007-05-27
Wait a second.  Can you post your /etc/apt/sources.list?  I see there are two different releases (feisty and dapper) in there!  If that's true, it's a real bad idea for mixing repos in /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by ayush3090 on 2007-05-27
> **taurus said:**
> Wait a second.  Can you post your /etc/apt/sources.list?  I see there are two different releases (feisty and dapper) in there!  If that's true, it's a real bad idea for mixing repos in /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```
[IMG]http://xs215.xs.to/xs215/07210/screenieeeeee.png[/IMG]

---

### Post by ayush3090 on 2007-05-27
GOD ive got releases in one............thats scary :S

---

### Post by ayush3090 on 2007-05-27
wot shud i do ....sir ???/

:'(

---

### Post by taurus on 2007-05-27
Are you running Dapper or are you running Feisty?  You cannot have two different repos (dapper and feisty) in /etc/apt/sources.list at the same time so I am not sure why you did that.

---

### Post by ayush3090 on 2007-05-27
> **taurus said:**
> Are you running Dapper or are you running Feisty?  You cannot have two different repos (dapper and feisty) in /etc/apt/sources.list at the same time so I am not sure why you did that.
i dont know how that happened

but i have the UBUNTU FEISTY CD.....and tats wot i installed

does this mean i hav to install it again
and sir cud u please PM me ur email ID (hotmail wud be preffered)

thanx sir

---

### Post by Lucifiel on 2007-05-27
Just curious: how on earth did you manage to add in the sources for Dapper into Feisty's sources.list ?

Edit: Are you really sure that's what happened when you installed Feisty? Because you've got to add in the sources yourself or through some other program.

---

### Post by ayush3090 on 2007-05-27
> **Lucifiel said:**
> Just curious: how on earth did you manage to add in the sources for Dapper into Feisty's sources.list ?

Edit: Are you really sure that's what happened when you installed Feisty? Because you've got to add in the sources yourself or through some other program.
ummm..........well even i dont know that

call me a genius or umm let say dumbass for dat hehehe

but srsly i need help..............plzz

---

### Post by ayush3090 on 2007-05-27
well i dont think it happened itself

i might hav added some wrong thing

and can i have ur ID also............so i cud get more help

plzzzz


thanx

---

### Post by Lucifiel on 2007-05-27
> **ayush3090 said:**
> ummm..........well even i dont know that

call me a genius or umm let say dumbass for dat hehehe

but srsly i need help..............plzz

Then, I suggest that you do a reformat and create an additional partition to use as /home. 

Oh and would you mind using proper spelling, grammar and punctuation? It's a bit difficult to read your sentences. 

Edit: I don't do IM or email troubleshooting. I'm busy enough. If you want to learn how to use Linux, you've got to start reading guides and asking plenty of questions. 


Thank you! :)

---

### Post by ayush3090 on 2007-05-27
yeah okay thanx anyways

and sure ........ back on normal english .............these IMs and text messaging hav really spoiled it :D


well it is already a different partition , but actually it was around 18gb of unallocated space

---

### Post by ayush3090 on 2007-05-27
NO HELPP :(

anyways i'll login 2moro..........its 4am here..........have to sleep
but all the respected members please leave ur ideas upon this

thnx to u in advance

and thanx @taurus sir

---


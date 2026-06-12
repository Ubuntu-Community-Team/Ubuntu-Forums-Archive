---
title: "How do i install anything?"
date: 2007-10-02
forum: General Help
---

### Post by Nirer on 2007-10-02
It's my first time using any Linux (so i figured out Ubuntu since it loox cool), anyways i wanna download some stuff for Linux and they come as .deb or .gz  or even .bin (.bin=real player).
HOW THE HECK DO I INTALL THEM?! PLEASE HELP ME!

---

### Post by Steve1961 on 2007-10-02
> **Nirer said:**
> It's my first time using any Linux (so i figured out Ubuntu since it loox cool), anyways i wanna download some stuff for Linux and they come as .deb or .gz  or even .bin (.bin=real player).
HOW THE HECK DO I INTALL THEM?! PLEASE HELP ME!

Just use synaptic - System>Administration>Synaptic

Search for a package, check the box to install and hit apply

---

### Post by Amazona aestiva on 2007-10-02
Now deb is like a exe. It should simply install the program.

gz bz tar bz2 are usually source files... You need to compile them ,but ,so...

See [this]("http://www.cutlersoftware.com/ubuntuinstall/") page. ;)

---

### Post by rsambuca on 2007-10-02
Your best bet is to try to find the programs in the Synaptic Package Manager first.  If you can't then try to find a .deb package.> Now deb is like a exe. It should simply install the program.Actually, a .deb file is more like a .msi file.

---

### Post by dabl on 2007-10-02
> **Nirer said:**
> 

HOW THE HECK DO I INTALL THEM?! PLEASE HELP ME!

Best advice for first timers is, first look at the 2200+ packages in the standard repositories, plus maybe you want to add Medibuntu for some of the "extras".

It gets tricky pretty quickly when you start downloading things from the Internet to your Linux box -- the things you learned to do in Windows will quickly start to haunt you!  Fair warning ... :guitar:

---

### Post by mali2297 on 2007-10-02
> **Nirer said:**
> It's my first time using any Linux (so i figured out Ubuntu since it loox cool), anyways i wanna download some stuff for Linux and they come as .deb or .gz  or even .bin (.bin=real player).
HOW THE HECK DO I INTALL THEM?! PLEASE HELP ME!

If you have downloaded RealPlayer10GOLD.bin to your Desktop, open a terminal and run
```

cd Desktop
chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```
and answer the questions given to you (just hit ENTER if uncertain). The routine is more or less the same for other .bin files.

---

### Post by Nirer on 2007-10-02
Well its helpfull but i still dont understand it completly and the gold real player thingi doesnt work :( anyways that synaptic how i add a package i downloaded?

I downloaded an online game it came as tgz how do i install it?

---

### Post by dabl on 2007-10-02
> **Nirer said:**
> 

I downloaded an online game it came as tgz how do i install it?

Right-click, "Extract Here", then open the new folder, find the .deb file, right-click it, and choose "Gdebi Install" (or close to that).  No guarantees on results ...  :)

---

### Post by r4ik on 2007-10-02
Please do have a look at the link  Amazona aestiva posted.

---

### Post by Nirer on 2007-10-02
I got that part and how do i install .bin?

---

### Post by por100pre1 on 2007-10-02
Do [this]("http://ubuntuforums.org/showpost.php?p=3405396&postcount=2"). It is easier if you just want Real Player.

---

### Post by strabes on 2007-10-02
Not to question your software preferences, but why would you ever want to use realplayer when there are so many other (better) media players out there?

---

### Post by Nirer on 2007-10-02
To my opinion they are better as well it's just that they don't support RMVB.... (And I'm an anime addict and they usually come as rmvb)

---

### Post by Yoyko on 2007-10-02
Altho it's a bit off-topic, they usually come as AVI...

---

### Post by mali2297 on 2007-10-02
> **Nirer said:**
> I got that part and how do i install .bin?

What doesn't work in the instructions I gave you? Describe what you did and the error you got.

---

### Post by Bablefish on 2007-10-02
If your looking for software the first place to look honestly is your Desktop as in Applications > Add Remove. There is 100s of programs listed. The second place is [http://getdeb.net](http://getdeb.net)

---

### Post by euthyfro on 2007-10-02
not to turn this into an anime thread, but a lot of fansubbing groups are now moving to .mkv (at least that's what i've been seeing a lot of recently).  seems like it's 50/50 .avi/.mkv now on the stuff i'm watching.
Oh to sail the sea of stars in the Arcadia of My Youth

---


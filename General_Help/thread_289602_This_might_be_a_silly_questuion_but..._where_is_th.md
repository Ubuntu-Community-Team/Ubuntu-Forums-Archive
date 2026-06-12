---
title: "This might be a silly questuion but... where is the dependency list saved ?"
date: 2006-10-31
forum: General Help
---

### Post by Trekos on 2006-10-31
This is why I am asking this :

I have a group of people, lined up to try Ubuntu.
They are all Linux virgins and cannot have internet access from their systems via Linux, due to them relying on internet accees via USB dsl modems or dialup modems and cannot/will not download the massive ammounts of data required.
Not only I want them to get the full Linux experience by using more than what a LiveCD can offer, but their needs vary :
One needs Dia for his work, another needs Kino, another needs Scribus etc... etc... etc.
I have retrieved from my system (/var/cache/apt/archives), a total of 800MB in packages which include them all and their dependencies.

Along with the Ubuntu disk, I can hand them the extra disk and instruct them to sudo copy through Nautilus, the extra disk contents into their /var/cache/apt/archives folder.

How will Synaptic find where to get the dependencty list from ?

Where is it sitting in the system, so I can retieve my dependancty list and have them copy it in their systems ?

I hope I made sense... :confused:

---

### Post by turkenator on 2006-10-31
i just did some internet research and nothing turned up besides lots of stuff about dependency hell this may sound like a noob way of doing things but it would propably work unless some1 is able to tell u where that list is stored my suggestion copy ur whole h/d over then uninstall the stuff not needed on ur friends machine and configure the drivers u propably thought of this aswell but worth a shot hope it helps 
good luck

---

### Post by nikhilk on 2006-10-31
I think all the dependency information for a package is contained within the .deb file itself. I don't think this information is external to the package.
There has to be something in apt-get/aptitude which shows the dependencies of a given package. Not at an Ubuntu machine right now so cant find out. Just see the man page of aptitude, you will find some clue there.

---


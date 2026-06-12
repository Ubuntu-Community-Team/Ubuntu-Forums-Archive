---
title: "Software to create a tree diagram/flow-chart of bash application"
date: 2014-08-19
forum: General Help
---

### Post by cj13579 on 2014-08-19
I have a application that we use at work for automation which has grown into a large collection of bash scripts (~45) with an equally large number of config and source files (~60). In order to be able to help get new starters to grips with the program quicker and assist us with developing (read: taming) the thing I think it would be a really good idea for us to create a tree-diagram/flow chart of the application.

I think that I will probably use MS Visio to draw the pretty pictures because we already have it, I have used it before and I have been recommended it by some friends who have used it in the past.

What I was wondering though is whether or not there is an application out there already which could do the leg work for me and analyse the programs and create the hierarchy diagram? I can then take that and colour it in (basically) in Visio.

My Googling is normally pretty good but I have come up short in this search. Hopefully someone has wanted to do something like this before and can point me in the right direction. Or, equally as fair, tell me to stop being lazy and get to work ;) !!

---

### Post by nerdtron on 2014-08-19
That means those scripts are custom made. I'm not familiar of any program that can read several bash scripts and automatically provide a diagram of their inter-connectivity. That seems to be too complicated. I guess a diagram from visio is your best shot.

---

### Post by dragonfly41 on 2014-08-19
Here is a first very rough idea (untested) ..

(1) apply optional **trace** (or **strace**) to all your bash script .. to monitor the process flow

(2) somehow parse the output(s) into intermediate **json** format

(3) apply a visualisation library such as **D3** to json

(4) the library can be stored in a json db such as **mongodb**

As I wrote above .. just a rough untested idea.

---

### Post by cj13579 on 2014-08-20
Thanks for the suggestions guys. There is probably an idea for a project in there somewhere, though I suspect it hasn't been done because its waaay more complicated that I would like it to be! Maybe I will work on it at some point.

---


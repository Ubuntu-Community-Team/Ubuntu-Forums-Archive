---
title: "Can't find certain apps anymore"
date: 2012-10-21
forum: General Help
---

### Post by MadsRC on 2012-10-21
I recently installed Lubuntu 12.10 on a old laptop and I've run in to a few, caveats...

In the software center, there's certain apps I can't find. One being k3b, another one being firefox (Not that I want to use it, I just know that firefox should be there.)

I've got main, universe, multiverse and restricted sources allowed, plus canonical partners and independent enabled.

With my other machine (Ubuntu Minimal installed with LXDE Core on top) have no problem finding k3b.

Did something change in 12.10 that I'm not aware of?

Also, searching for "restricted" doesn't yield anything... Should yield ubuntu-restricted-extras atleast.

The same applies for Synaptic Package Manager

EDIT: Just found out conky isn't found either. So either my install is borked OR a whole lot of programmes were remove from the repositories?

---

### Post by jerrrys on 2012-10-21
What happens if you do:

sudo apt-get install k3b

If it installs then its got to be there somewhere.  Maybe try synaptic.

---

### Post by MadsRC on 2012-10-21
This is what happens:

> xxx@xxx-xx:~$ sudo apt-get install k3b
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package k3b

Synaptic doesn't find it either.

---

### Post by jerrrys on 2012-10-21
Sounds like you need to:

sudo apt-get update

---

### Post by Dennis N on 2012-10-21
Firefox is in the Lubuntu Software Center and also installable with Synaptic Package Manager.

k3b seems not to be in the Lubuntu Software Center (and probably shouldn't be there), but IS installable with Synaptic. 

Try 'reload' in Synaptic to refresh the lists. Also be sure the necessary repositories are checked as being active.

---

### Post by MadsRC on 2012-10-21
I HATE when the solution is THAT simple and THAT obvious. apt-get update solved the problem.

---

### Post by jerrrys on 2012-10-21
Been there, done that  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


---
title: "[SOLVED] HELP! my computer wont let me up-date."
date: 2007-08-16
forum: General Help
---

### Post by crazygun on 2007-08-16
[SIZE="2"]hey,

im having trouble in getting my Update Manager to just update anything. For some reason it keeps telling me there is an error.

error : E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open()failed,please report.


I dont even know what i should do from here. can anyone help me? [/FONT][/FONT][/SIZE][/SIZE]

---

### Post by kellemes on 2007-08-16
> **crazygun said:**
> [SIZE="2"]hey,

im having trouble in getting my Update Manager to just update anything. For some reason it keeps telling me there is an error.

error : E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open()failed,please report.


I dont even know what i should do from here. can anyone help me? [/FONT][/FONT][/SIZE][/SIZE]

Open a terminal and type "dpkg --configure -a"

---

### Post by UK-Wobbie on 2007-08-16
> **crazygun said:**
> [SIZE="2"]hey,

im having trouble in getting my Update Manager to just update anything. For some reason it keeps telling me there is an error.

error : E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open()failed,please report.


I dont even know what i should do from here. can anyone help me? [/FONT][/FONT][/SIZE][/SIZE]

Can you go in to Synaptic Package Manager? And look at the Broken Packages? 
(System -> Administration -> Synaptic Package Manager)
It sounds like you have got some or one Broken Packages.. Ubuntu will not do any more updates Or instill any thing if you have got Broken Packages.

Have a look in that and see if that will fix it :)

---

### Post by crazygun on 2007-08-16
I try to go to System> Administration> synaptic package manager

it gave me the same thing... I dont know what is going on with this computer. I have only had it for month and half. So im still really new to it all.

---

### Post by kellemes on 2007-08-16
Assuming you have not done this..
Open a terminal and type "dpkg --configure -a"

---

### Post by crazygun on 2007-08-16
and how do i do that?? see i dont know anything about this computer. So im like hopeless in so many ways.

---

### Post by Seisen on 2007-08-16
Its Applications>Accessories>Terminal

---

### Post by crazygun on 2007-08-16
thanks... i will see if that works

---

### Post by crazygun on 2007-08-16
this is great... i have an other problem. When i went into my synaptic package manager.. it said the same error. I did want you side and that worked, but i still can't up-date any thing. and on top of that my other thing isn't working. so now what do i do?

---

### Post by crazygun on 2007-08-18
okay i got into terminal and i type dpkg --configure -a
now what do i do>?
         it wont let me open synaptic package manager... i am getting the same error on that too.
can yall help me? please

---

### Post by g2g591 on 2007-08-18
press enter? you might need to use "sudo dpkg --configure -a" and if that doesn't work (also in a terminal) use "sudo apt-get install -f"

---

### Post by crazygun on 2007-08-18
yeah i went in and i put in "sudo dpkg --configure -a" and it worked. i also putted in my password. by the way it looks i think it is working.  but now what do i do?

---

### Post by g2g591 on 2007-08-18
see if you can update or install packages, if you still can't in a terminal use "sudo apt-get install -f"

---

### Post by crazygun on 2007-08-18
OKAY.... i have tried both of them and they worked. i just need to know if i have to do anything else.

---

### Post by g2g591 on 2007-08-18
nope, your done, enjoy. oh, under thread tools (on this page) mark the thread solved

---

### Post by crazygun on 2007-08-18
yeah but im not done... it still wont work! 

 i went to update and this is what is said....

it is impossible to install or remove any software. please use the package manger "synaptic" or run "sudo apt-get install -f" in a terminal to fix issue at first.

so i did that......... 

E: dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem.

now im lost again...

---

### Post by forestpixie on 2007-08-18
same as your other thread

---

### Post by g2g591 on 2007-08-18
did you interupt it when you ran sudo apt-get install -f ? if so thats why its asking you to do it again

---

### Post by crazygun on 2007-08-18
okay i ran the sudo apt-get install -f again and it asked me if i want to go on [Y/N] ...
do i hit Y or sure i not go on>?

---

### Post by g2g591 on 2007-08-18
yes, do hit Y.

---

### Post by crazygun on 2007-08-18
OKay: Now i got this...

it went to a blue screen and it saids this,,

package configuration 

 Configuring sun-java5-bin

Operating System Distributor License for Java v1.1 (DLJ)
 and its goes into the whole law crap.. 

put its not letting me do anything else.. now what?

---

### Post by g2g591 on 2007-08-18
hold enter until it asks you yes or no, then say yes

---

### Post by crazygun on 2007-08-18
i did

---

### Post by crazygun on 2007-08-18
okay now it kicked me out of my terminal... now i have to do it all over again

---

### Post by crazygun on 2007-08-18
okay now i have a new problem!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

my update was running so it was fix until i got this error...

E:/var/cache/apt/archives/sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb:
subprocess pre-installation script returned error exit status 1
E:/var/cache/apt/archives/sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb:
subprocess pre-installation script returned error exit status 1



now what in the world does that mean?

---

### Post by por100pre1 on 2007-08-18
It seems to be an issue with sun-java5-bin package. Try removing it.

```
sudo apt-get remove --purge sun-java5-bin sun-java5-plugin
```

If it works, update your system

```
sudo apt-get update && sudo apt-get upgrade
```

and reinstall

```
sudo apt-get install sun-java5-bin sun-java5-plugin
```

Let's see if this helps...:-k

---

### Post by crazygun on 2007-08-18
it said that it couldn't find the package sum... on the first step. should i try to go on... or what?

---

### Post by g2g591 on 2007-08-18
you mistyped...

---


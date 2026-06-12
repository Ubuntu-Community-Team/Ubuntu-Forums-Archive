---
title: "Re: Adept Package Manager Problem."
date: 2008-06-25
forum: General Help
---

### Post by tru infini on 2008-06-25
i have a problem with my package manager. I am running kde 4.8  and my amarok was inconveniently updating its music collection at the same time i was using my package manager to get a program. (celestia) something weird happened and my computer froze. upon Ctrl+Alt+backspace-ing my computer and logging back in i find that my thing is unlocked (or unlocked) where i cant download anything and my package manager only opens in read only mode. when i looked at it. i find i do have celestia, BUT its not in any of the menus! if i want to open Celestia i have to go through Root/usr/bin to get to it. ive enver seen it do this before, could somebody please help?
i have a solution for this problem to any programmers out there that help build the next versions of all linux:
         make so it autolocks (or auto-unlocks) that folder when you log off or shut down so it wont say something to the effect of "another program is using that, your screwed now cause the terminal lines im giving you dont really do any good"
all this started when i was downloading all the firefox plugins so i could watch youtube (but i can only hear it for some reason)

anyone has any sloutions to any of these problems please help im going crazy:confused:

---

### Post by PmDematagoda on 2008-06-26
Perhaps you may need to configure Celestia, open a terminal and execute:-
```
sudo dpkg --configure -a
```
or
```
sudo apt-get install -f
```
if the previous command doesn't work.

---

### Post by tru infini on 2008-06-27
its not so much as Celestia im worried about its the fact that my adept installer is messed up. it wont let me download anything because its always in read-only mode. i was just including that bit about Celestia to show what it did when it got messed up. its always saying this:
_____________________________________________________________
| Database Locked - Adept Batch                              |
|____________________________________________________________|
|                                                            |
| Another process is using the packaging system database     |
| (probably some other Adept application or apt-get aptitude)| 
|                                                            |
| would you like to attempt to resolve this problem?         |
| No will enter read-only mode and cancel to quit and resolve|
| this issue yourself.                                       |
|____________________________________________________________|

so i click "yes" and it brings 3 pop-ups
1: there was an error committing  changes. possibly there was a problem downloading some packages or the comment would break packages

2: failed to unlock database. please try to resolve this issue 
'sudo dpkg -configure -a' may help

3: is a loader bar that says "unlocking" and is stopped at 50%


so i open terminal and type: sudo dpkg -configure -a
for a read out of:
robert@truInfini:~$ sudo dpkg -configure -a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
robert@truInfini:~$   
is there anything out there that can help? i also tried what you said but nothing changed.:confused:

---

### Post by PmDematagoda on 2008-06-27
The command isn't:-
```
sudo dpkg -configure -a
```
it's:-
```
sudo dpkg _**-**_-configure -a
```
there are two "-"s before configure.

---

### Post by tru infini on 2008-06-27
well it still doesn't work, here is what happened:

root@truInfini:~# sudo dpkg --configure -a
root@truInfini:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@truInfini:~#

"sudo dpkg --configre -a" literally did nothing. 
and "sudo apt-get install -f" keeps telling me that 0 to be upgraded, installed, remove and not upgraded. 
 i beleive its telling me this because my thing wont unlock.

---

### Post by PmDematagoda on 2008-06-27
Can you post the output of:-
```
sudo apt-get install celestia
```

---

### Post by tru infini on 2008-06-28
when i try that it says that it is already downloaded to the newest version of celestia (i cant give the exact reading because i'm on my friends computer as my internet is down), but,...THAT IS BESIDE THE POINT... right now fixing celestia first is like shoveling the manure out of the stream before getting the cows out. i say lets deal with the cows right now and then later if there is still a problem we can deal with celestia.
   all i ask is that someone please let me know how to unlock that folder. so i can download stuff again.

---

### Post by PmDematagoda on 2008-06-28
> **tru infini said:**
> when i try that it says that it is already downloaded to the newest version of celestia (i cant give the exact reading because i'm on my friends computer as my internet is down), but,...THAT IS BESIDE THE POINT... right now fixing celestia first is like shoveling the manure out of the stream before getting the cows out. i say lets deal with the cows right now and then later if there is still a problem we can deal with celestia.
   all i ask is that someone please let me know how to unlock that folder. so i can download stuff again.

When you try to install an application through the terminal what error do you get? If the error has a path included and says that it was unable to lock it then do:-
```
sudo rm /path/specified
```
and see if that fixes it.

---

### Post by tru infini on 2008-06-29
When you try to install an application through the terminal what error do you get? If the error has a path included and says that it was unable to lock it then do:-
```
sudo rm /path/specified
```
and see if that fixes it.[/QUOTE]

if i can know what it does and what it means i will remember it better, if you would be so kind as to explain this code?

---

### Post by PmDematagoda on 2008-06-29
> **tru infini said:**
> When you try to install an application through the terminal what error do you get? If the error has a path included and says that it was unable to lock it then do:-
```
sudo rm /path/specified
```
and see if that fixes it.

if i can know what it does and what it means i will remember it better, if you would be so kind as to explain this code?

It basically removes a lock file(if you provide the right path), this lock file is used to ensure that another package process doesn't run while one is already working(it gives exclusive access), however if a package process was stopped incorrectly then the lock still remains and it could prevent any package process from occurring.

---

### Post by tru infini on 2008-06-29
how do i know the right path? to the lock file?

---

### Post by PmDematagoda on 2008-06-29
> **tru infini said:**
> how do i know the right path? to the lock file?

Try and install an application(such as X-Chat with:-
```
sudo apt-get install xchat
```
the error(if any) should provide the path.

---

### Post by tru infini on 2008-06-30
a'ight, i'll give it a try and see what happens.

---

### Post by tru infini on 2008-07-03
```
robert@truInfini:~$ sudo apt-get install xchat
[sudo] password for robert:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xchat
robert@truInfini:~$

```
thats all it did. is there anyway to look across your computer to kinda get an idea of what it might be?

---

### Post by PmDematagoda on 2008-07-04
Hmm, so it looks like it needs a valid package name. Ok, try this:-
```
sudo apt-get install xchat-gnome
```

---

### Post by tru infini on 2008-07-04
this is all it did.

```
robert@truInfini:~$ sudo apt-get install xchat-gnome
[sudo] password for robert:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xchat-gnome
robert@truInfini:~$

```

please note i am using the latest version of kde.

---

### Post by PmDematagoda on 2008-07-05
Try doing:-
```
sudo rm /var/cache/apt/archives/lock
```
and see if that fixes it.

---

### Post by tru infini on 2008-07-07
nope that didn't do anything either, i'm just going to do a complete systems wipe.

---

### Post by tru infini on 2008-07-09
thanks tru infini, it's nice to see someone around here that knows how to fix this problem. i'm willing to bet that this will fix most problems anyones got on any kind of linux computer. so i guess this should not be targeted only towards kde computers, but in a broad range of all types now.

---


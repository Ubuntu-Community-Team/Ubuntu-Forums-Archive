---
title: "System now freezes after attempt to install a game."
date: 2014-05-03
forum: General Help
---

### Post by sarahfoxnz on 2014-05-03
[https://help.ubuntu.com/community/Games/NativeFreeUbuntuGames#Nexuiz](https://help.ubuntu.com/community/Games/NativeFreeUbuntuGames#Nexuiz)

Hello.

is the abovE NEXUIZ game spam / hack or something ?

I installed / ran it just now, & it completely froze my system.

i have 2 issues 

1) How do turn the volume Off (or down ?). 

when i activated / started the game, it looked quiite good, however the volume was loud. 

My curser was RESTRICTED to that screen - i could not go to the sound part of my computer to turn the sound down.


2) How do i QUIT / STOP / END the game. (my curser was restricted to that screen - could not go to the left side menu to "quit" the game.)

---

### Post by sarahfoxnz on 2014-05-03
Hello.

yesterday I tried this, [http://ubuntuforums.org/showthread.php?t=2221652](http://ubuntuforums.org/showthread.php?t=2221652). And ever since then my PC freezes.

im typing on my ipad now.

I've removed the programme last night, but had to reboot my PC a number of times today.

can anyone advise a possible solution for general freezing ?

---

### Post by sarahfoxnz on 2014-05-03
Further -I can move my mouse to other areas of the screen, but if I click on anything it doesn't do anything, or takes 10 + minutes or so to change. I have rebooted several times today.

edit:system monitor

load averages 1, 5, 15 minutes - 0.00, 0.01, 0.05

---

### Post by Kaloyan_Banev on 2014-05-03
Did you check your system for viruses? Something might be using your resources.

---

### Post by sarahfoxnz on 2014-05-03
Il try - when my PC unfreezes.

---

### Post by QIII on 2014-05-03
[I]Threads [B]Merged. 


[/B][/I]Title changed to reflect situation.  This is a continuation of a single event.

---

### Post by sarahfoxnz on 2014-05-03
What is the command line to install avg?

ive got the terminal running, but I don't want to open a browser to freeze PC again.

---

### Post by sammiev on 2014-05-03
Here's the one for Bitdefender.

Add the repository by going to System - Administration - Software Sources, click on the 'Other Software' (previously 'Third Party Software') tab. Now click on 'Add' and enter.

```
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
```

```
wget http://download.bitdefender.com/repos/deb/bd.key.asc
sudo apt-key add bd.key.asc
```

```
sudo apt-get update
```

```
sudo apt-get install bitdefender-scanner-gui
```

Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications - System Tools - BitDefender Scanner).

Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button.

License

BitDefender comes with a standard 30 day free license, when first installed. It is free for private and personal use - the license can be extended to one year by requesting a new license key from [http://www.bitdefender.com/site/Products/ScannerLicense/](http://www.bitdefender.com/site/Products/ScannerLicense/) For all business use a paid for license is required.

---

### Post by sarahfoxnz on 2014-05-03
No command 'deb' find.
is there a command to install 'deb' ?  I've googled and found instructions on install deb files, but not deb itself.

:(

---

### Post by sammiev on 2014-05-03
Second thought you can delete the FireFox directory and then reinstall FireFox again using Software Center or Synaptic Package Manager.

---

### Post by sarahfoxnz on 2014-05-03
I've found instructions on installing deb. now I have 3 terminals open and my PC froze..   Waiting....

il il email again in 87 hours...

---

### Post by sarahfoxnz on 2014-05-04
hi. ive got AVG installed now. but getting errors


 sudo avgscan  /home/
AVG command line Anti-Virus scanner
Copyright (c) 2013 AVG Technologies CZ

Virus database version: 3722/7437
Virus database release date: Sat, 03 May 2014 19:55:00 +1200

/home/sarah/  Object scan failed; Permission denied

Files scanned     :  0(0)
Infections found  :  0(0)
PUPs found        :  0
Files healed      :  0
Warnings reported :  0
Errors reported   :  1


How do i scan everything (possible) ?

---

### Post by sandyd on 2014-05-04
Does Ubuntu freeze when you run it from a LiveCD?
Does Ubuntu freeze when you create a new user in your current install and login as that user?

---

### Post by sarahfoxnz on 2014-05-04
> **sandyd said:**
> Does Ubuntu freeze when you run it from a LiveCD?
Does Ubuntu freeze when you create a new user in your current install and login as that user?

1) i dont have CD. (if i have, ive lost it) - just been upgrading online for last few years whenever an upgrade is avaialable.

2) havn't tried adding a new user - but not sure if that is going to do much.

Right now, i'm on the PC - & using mozilla. 

my mouse works, i can switch between tabs & type thintgs etc - HOWEVER, if i click on my side menu & open a terminal / system monitor or something - NOTHING happens - itsa s if i never clicked it. but, i camn still use mozilla firefox as normal. 
(but thats the present state at this time. it amy cahnge in 5 or 10 mins.)


3) i'm googling, trying to find out why i can't just use AVG to scan "whole computer" (i am using sudo). 

(i like ubuntu, but everything is so complex to use - for simple things you havn't tried before.. )



EDIT - QUESTION.

Is there a command to say :- scan everything, ignore all errors & scan something else that has no errors (dont stop scanning until its scanned everything)

- also, tell me what the errors are, so i can figure out how to fix it :-)

---

### Post by sarahfoxnz on 2014-05-04
Oh well. Never mind. Today is a lost cause.

my PC mouse batteries died. I'm recharging.  Il do something else. Maybe tomorrow I can get AVG going.

---

### Post by sarahfoxnz on 2014-05-04
I think my freezing is not to do with the recent upedates. my Pc has d/loaded a LOT of updates (moree than i think should be).

refer here - [http://ubuntuforums.org/showthread.php?t=2221843](http://ubuntuforums.org/showthread.php?t=2221843)

---


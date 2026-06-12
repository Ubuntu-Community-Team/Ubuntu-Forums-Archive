---
title: "Installing NVIDIA Drivers on Asus G75VW"
date: 2015-05-10
forum: General Help
---

### Post by derek-andrew-moore on 2015-05-10
Hi Guys, 

First time to the forums so apologies in advance if I seem like "That guy" ):P



Ok so here's what I have going on. I installed Ubuntu 14 on my Asus G75VW (Been away from linux way too long, talk about Coming back Home) and my model has an NVIDIA GeForce 660M GPU. I have the driver saved to my Desktop. Everyone has been telling me (including the installer) I need to kill my X Server and install over the terminal only. Great. So im about to log into my account:

CTRL - ALT - F1 to do that...Screen goes dark and you can tell the X server was killed. Great.......Except I don't see the terminal come up. It's literally a blank screen. 



Yet if I do CTRL - ALT - F7 , the X Server comes back up and good Ol' Gnome returns. 



Any thoughts? My overall goal is to install the NVIDIA drivers to get Steam rocking at a decent pace. Nothing intense, just a little gaming on occasion.

---

### Post by Bashing-om on 2015-05-10
derek-andrew-moore; Hello, Welcome back !

Here's the deal, that GeForce 660M GPU uses the Nvidia 346 version driver. That driver is not available in 14.04's repo.
So, rather than installing from the Nvidia site, install from a supported PPA.
To do that with no driver installed one boots with the boot parameter "nomodeset" ( or boot the recovery console and reset '/root' r/w).

Nomodeset way:
Boot the system and as soon as the bios screen clears, depress and hold the right-shift- key -> grub boot menu;
with the ubuntu normal kernel selected press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " and arrow across to the terms "quiet splash"; add the term "nomodeset" after "quiet splash" ;
key combo ctl+x to continue the boot process .
At the login screen does the key combo ctl+alt+F1 now get you a console interface ? login here with username and password ( no response to the screen when pass word is entered. enter your password blindly and hit the enter key ).
Now we install a driver, I do highly suggest and recommend from A PPA:
```

sudo service lightdm stop
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346

```
Reboot:
```

sudo shutdown -r now

```

Do you now come up with a fully functional desktop ?

[INDENT][INDENT]looks like a plan to me
[/INDENT][/INDENT]

---

### Post by derek-andrew-moore on 2015-05-10
So I did that to the T. The only thing I noticed fishy was that it did kick back an error code (1) after it downloaded and was installing the driver.
 
I rebooted and logged in no problem, just like normal. So here is the Noob-ish question:




How do I know if it worked? just pop open steam?

---

### Post by Bashing-om on 2015-05-10
derek-andrew-moore; Yepper, ya got that right;

The test is if steam runs:
presently to make sure all is as should be:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```
IF all that runs clean install steam:
```

sudo apt-cache show steam

```
You like what you read, and understand:
```

sudo apt-get install steam

```

[INDENT][INDENT]happy as a lark
[/INDENT][/INDENT]

---

### Post by derek-andrew-moore on 2015-05-10
You're awesome, Thanks! I did notice something was applied for the GPU. Except I do have a question again lol 


I tried the apt-get install steam, and I got a few errors. I attached a screen grab to show what im looking at. [ATTACH=CONFIG]261905[/ATTACH]

---

### Post by Bashing-om on 2015-05-10
derek-andrew-moore; Yuk !

Somehow your control files have become corrupted .

A fix:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt-get update.

Now is all good ?, Can we not now mark this thread as "solved" - as we are getting way off the original topic.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by derek-andrew-moore on 2015-05-10
I'll give it a try, thanks!! 


Oh yes, definitely marked as Solved. If I still have Steam issues I'll find the right section in the forums. Again, I don't want to be "That Guy". 


It's great to be home again, AH!

---

### Post by Bashing-om on 2015-05-10
derek-andrew-moore; Great !

I expect that now you are home free. 
Shinning like a new penny.

Only you can mark the thread 'solved' :
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and just keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


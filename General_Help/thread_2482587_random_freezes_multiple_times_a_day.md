---
title: "random freezes multiple times a day"
date: 2023-01-05
forum: General Help
---

### Post by strange on 2023-01-05
i did a fresh install of xubuntu 22.10 everything is working fine untill it just completely locks up.
no capslock light no ctrl + alt + 1-9 to get into a prompt nothing.
i run it on a t14 gen2 lenovo laptop could anyone point me to which logs i could post to get a better understanding of what causes it?

help very much appreciated

---

### Post by HermanAB on 2023-01-05
Usually, there is nothing helpful in the logs for sudden crashes. Some googling will find you the log display tools.

I would divide and conquer:
Boot with install media, let it go to a full desktop and leave it there.  Does it ever lock up?
If yes, then you likely have a hardware problem (fan dirty, memory or PSU). 
If not, then you have a graphic driver problem (the installer runs a simple graphics driver).

---

### Post by strange on 2023-01-05
i have intel 620 how would i go about uninstalling everything related to that and just running default driver ?

---

### Post by TenPlus1 on 2023-01-05
Go into the bios and change Sleep State to Linux.

---

### Post by strange on 2023-01-05
what does that do? i dont think it has to do with anything regarding sleep seeing it just happens when im active too it could last for a day for 10 minutes. it just happens at random intervals

---

### Post by strange on 2023-01-06
its still happening, what i just noticed is that after it freezes nad i reboot the brightness of the laptop is at maximum might that be a clue?

---

### Post by strange on 2023-01-06
i just upgraded graphic drivers from ppa:kisak/kisak-mesa and now after freeze it doesnt put brightness on max anymore, could someone point me to a purge command to remove everything related to my video driver and reinstall it?
or maybe a command so i can post what i have intsalled and maybe someone can point me to what might be conflicting?

---

### Post by TenPlus1 on 2023-01-07
Changing the bios option I mentioned to "linux" helps the kernel better switch between power states on the motherboard and cpu when idling.

---

### Post by strange on 2023-01-07
ok i will change it to that now the freezes have increased to like once every 2-3 hours, and earlier today it happened twice during the login to the xfce

---

### Post by strange on 2023-01-07
thanks for the help so far

---

### Post by strange on 2023-01-07
nope still froze just happened again

---

### Post by dragonfly41 on 2023-01-07
Some thoughts ..
Does a LiveUSB running separate Ubuntu session - "Try Ubuntu" - also freeze?

Does a new user desktop account created on laptop (not LiveUSB) also freeze?

Have you tried inspecting the list of running processes? I use Stacer GUI but you can use command line.

What browsers are running?

How many open browser tabs? Each tab consumes resources.

Further thought - carefully clean edges of memory card(s). If you have two, you can try running on one card, test, then swap, to see if there is a memory card issue. Just trying a process of elimination.

---

### Post by strange on 2023-01-07
its a laptop so i cant open it but memory test runs just fine and i let windows run for 2 days without crashing i have a feeling its related to the videocard like someone else said
i am only running firefox with about 10 tabs. before this installation of ubuntu 22.10 i ran 21.04 this was about 4 days ago and it ran for weeks on end without crashing. 
i dont see any weird processes
i was trying to get worms wmd running it was spitting weird errors and i ran some apt install sudo apt install libgl1-mesa-* command im thinking thats the culprit
is there a way to reset whatever packages i installed for that ?

---

### Post by strange on 2023-01-07
i have just noticed that when it crashes my screen does moves to the right here are pictures i took with my phone from the top left edge of my screen and the right
left:
[IMG]https://fyrkat.strangled.net/~strange/1.jpg[/IMG]
right:
[IMG]https://fyrkat.strangled.net/~strange/2.jpg[/IMG]

that might indicate it has to do with video?

---

### Post by wesselaar2 on 2023-01-08
had freezes for the last few months here with my dell optiplex 7020 with radeon r5 240  in  ubuntu 22.04.1 and same in debian 11 gnome, linux mint cinnamon 21.1 ,  no problems at all with same distro`s with mate desktops so i switched to mint 21.1 mate
the moments it was frozen was when surfing websites in chrome or firefox,  no problems with other software.
could it be a gtk3/4  problem?

---

### Post by strange on 2023-01-08
well mine also freezes during the login to xfce sometimes its really random it could be during any application and on 21.04 i had 0 issues i also dont have radeon just intel uhd620

---

### Post by strange on 2023-01-10
this is still happening when im not using my computer it doesnt freeze at all i leave it on overnight with screen on no issues but when i use it sometimes it takes 20 hours sometimes just a minute and it poof freeze.

---


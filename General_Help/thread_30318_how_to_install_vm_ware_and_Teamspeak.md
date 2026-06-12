---
title: "how to install vm ware? and Teamspeak"
date: 2005-04-28
forum: General Help
---

### Post by kisain on 2005-04-28
ok here it goes i'm a linux n00b.......
i want to install vmware in ubuntu and i don't know the proper commands i end up getting stupid errors like it can't find something i don't know if i'm entring the command wrong or what i downloaded a thing that looks like a box the title under it is: VMware-workstation-5.0.0-13124.i386.rpm. now i have no idea how to work with this type of file (i'm used to .exe) and i don't want to go back to windows (it sucks) but i want to be able to run my games and my old programs and using an emulator is not such a bad idea for me i've already tryed crossoffice and wine but the programs jsut won't function can anyone help me with step by step?
the other thingy that looks like a box is called : VMware-workstation-5.0.0-13124.tar.gz. i don't know how to get eather of these files to run....plz help a dumb n00b. :(

now as for teamspeak the box thingy has this title under it :ts2_client_rc2_2032.tar.bz2

if you have any questions plz feel free to ask i hope i gave enough info :(

this new os rocks and i just want to make it function well enough to replace my windows installs on all my computers 
well thanx for reading this and helpin if ya did :)

---

### Post by lao_V on 2005-04-28
The file that you're trying to install in a rpm. This doesn't work on Ubuntu as ubuntu is debian based and uses *.deb files. 

The tar.gz file you have, contains the source code, you need to unzip them and read the 'readme' in there on how to compile/install them. Most of the time it will be: ./configure && make && make install

---

### Post by kisain on 2005-04-28
ok i have no idea what your talkin about this is the first time that i have ever used linux or been able to install it i have blunderd my way through the installs and the updates and such just doin what i thought was logical.......i do not have the technical ability at this time to install these programs in ubuntu i don't know any commands or proccesses that would enable you to do these things.....i'm sitting here tryin to figure this out and i'm about to cry cause if i can't get them to run then i'll have to go back to (bad taste in mouth) windows xp :( and i want to avoid this at all costs(hate microsofts meglomania) so if anyone can please help a really stupid n00b plz do so i'm at my wits end :(






[QUOTE=lao_V]The file that you're trying to install in a rpm. This doesn't work on Ubuntu as ubuntu is debian based and uses *.deb files. 

The tar.gz file you have, contains the source code, you need to unzip them and read the 'readme' in there on how to compile/install them. Most of the time it will be: ./configure && make && make install[/QUOTE]

---

### Post by lao_V on 2005-04-28
If you don't want to use Windows then what exactly are you installing VMWare for?

---

### Post by codejunkie on 2005-04-28
couldn't he also use alien to create a .deb or to install the rpm? if he doesn't no how to compile it or would that not work on vmware just an idea don't know if it would work   or not but it may be worth a try.

---

### Post by kisain on 2005-04-28
[QUOTE=lao_V]If you don't want to use Windows then what exactly are you installing VMWare for?[/QUOTE]
 i'm trying to install it cause i need to be able to play lightside legend ragnarok (you can find it @ [www.clownphobia.com](www.clownphobia.com)) and wine nor crossover can handel it so i have to install an emulator
if there was some way around it than i would use it but for right now getting this to install is what seems to be the best solutionb and i was wondering if there is a way to give the files to someone and have them compile them for me?

or can i have a step by step walkthrough for really dumb n00bs like myself?

---

### Post by lao_V on 2005-04-28
[QUOTE=kisain]i'm trying to install it cause i need to be able to play lightside legend ragnarok (you can find it @ [www.clownphobia.com]("http://www.clownphobia.com")) and wine nor crossover can handel it so i have to install an emulator
if there was some way around it than i would use it but for right now getting this to install is what seems to be the best solutionb and i was wondering if there is a way to give the files to someone and have them compile them for me?

or can i have a step by step walkthrough for really dumb n00bs like myself?[/QUOTE]

You do know that VMWare is not the same as Crossover office/WINE, right? You will still have to install an OS in VMWare before you can install your game!

---

### Post by kisain on 2005-04-28
[QUOTE=lao_V]You do know that VMWare is not the same as Crossover office/WINE, right? You will still have to install an OS in VMWare before you can install your game![/QUOTE]
 i understand this but it seems to be the only option because i can't get the programs or there linux counterparts to install in ubuntu i like this os better than windows but still need the functionality of windows untill linux can support them nativly if you could help me i would really be thankfull and you would save me the trouble of having to totaly go back to windows to support my needs so can you help me? i also found a program called win4lin pro but i don't know how to install either of them.

any help you could give would be awsome
and thank you for your time

---

### Post by lao_V on 2005-04-28
There is a step by step on how to install VMware on Linux [here.]("http://rtfm.dyndns.info/tips/2000/06/24/35.shtml")

You will need to follow steps 6,7 and 8

---

### Post by kisain on 2005-04-28
ok i did what ya said and it worked awsome thank you very much.......is there a possibility you could help me with 2 things in vmware i have it up and running wirth my copy of xp pro installed but i gets an error 

thank you for helping me out i really apriciate it.









[QUOTE=lao_V]There is a step by step on how to install VMware on Linux [here.]("http://rtfm.dyndns.info/tips/2000/06/24/35.shtml")

You will need to follow steps 6,7 and 8[/QUOTE]

---

### Post by lao_V on 2005-04-28
ok, you will need to install the header files for your kernel. To do this, go into synaptic package manager and search for 'linux-kernel-*' and chose the one that matches your kernel. Then try to re-install vmware and see what it says. It is also advisable to install build-essential and g++ packages while you are in synaptic.

sorry, can't help with your mouse problems. have you checked  the batteries? :-) i have a wireless keyboard which rarely doesn't work. i simply restart.

---


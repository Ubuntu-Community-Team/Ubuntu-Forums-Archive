---
title: "plz help ..........sym linking????"
date: 2006-12-09
forum: General Help
---

### Post by slyjelly on 2006-12-09
hi, im trying to sym link some files.

i dont know precisely how to do it properly. this is the extract from the guide im trying to follow (the part that im stuck on):

sim link this file: /lib/libslang.so.1-UTF8 

to

 /home/<username>/DropTeam/lib/libslang-utf8.so.1

if someone could explain this to me in regards to the following quetions...

im guessing the first line is the filename of the file im creating a link to?
the second line is where the link is placed ?
i find the first line is also a file thats linked to another file called (libslang.so.1-UTF8.4.9), what should the line in the properties tab say next to "linked to"?
can i link a file to another linked file?

by the way, all this is for a game demo called dropteam to run on my ubuntu 64 bit. here are some links which explain my problem in greater depth (the 2nd one is best):

[http://www.battlefront.com/cgi-bin/bbs/ultimatebb.cgi?ubb=get_topic;f=60;t=000100](http://www.battlefront.com/cgi-bin/bbs/ultimatebb.cgi?ubb=get_topic;f=60;t=000100)
[http://ubuntuforums.org/showthread.php?t=206889](http://ubuntuforums.org/showthread.php?t=206889)

basiclly if you could make sense of the second link above, that would be great. 

plz help me , this is my second thread for this problem thanks in advance
](*,) :-k

---

### Post by aysiu on 2006-12-09
Pasting this command into the terminal ```
ln -s lib/libslang.so.1-UTF8 ~/DropTeam/lib/libslang-utf8.so.1
``` should do the trick. *ln* links, and *-s* makes it a symbolic link.

---

### Post by slyjelly on 2006-12-09
hi thanks for the reply im almost there,

the problem i have now is i cant create the link properly

i have a game demo folder on the desktop, which when i try to create the link in, its broken (got a weid red x and a yeloowish question mark on the file icon)

i also have 1 game file in my usr folder which i cant create the same symlink file, could you place a command for this file instead?

its in my usr local games folder

---

### Post by po0f on 2006-12-09
The above command has a typo, should be:
```
[FONT="Courier New"]$ ln -s /lib/libslang.so.1-UTF8 ~/DropTeam/lib/libslang-utf8.so.1[/FONT]
```
(The command *does* work, if you are in /.)  :)

[EDIT]

Without knowing file/directory names, I can't post any commands.  Aren't you installing this in ~/DropTeam?  Why is the game folder on ~/Desktop/DropTeam now?

---

### Post by aysiu on 2006-12-09
I think you're best off going the point-and-click route, as I don't know what files you're talking about.

If you're using Ubuntu, open up two windows with your file browser, and then middle-click-drag the file or folder you want to symlink to where you want to symlink it to. When you let go of the mouse wheel, select **link here**.

If you're using Kubuntu, do the same thing except right-click-drag instead of middle-click-drag.

A symlink is basically like a Windows shortcut or a Mac alias. It just points to the real file's location.

---

### Post by aysiu on 2006-12-09
> **po0f said:**
> The above command has a typo Thanks for catching that! That's what I get for not taking my own advice. I retyped instead of copying and pasting...

---

### Post by slyjelly on 2006-12-09
hi again, 

getting very close!!!

now when i type runclient ~/DropTeam$ sudo sh runClient.sh


it says 

runClient.sh: 2: pushd: not found
runClient.sh: 3: ./SpaceVikings: not found

any ideas?

---

### Post by po0f on 2006-12-09
slyjelly,

Where did you download this file?  I can't diagnose problems without (at least) most of the information.  If I could try to install the demo, I could tell you how to do it.

---

### Post by slyjelly on 2006-12-09
are you sure you want to?

that would be very kind although quite time costly, the link is below

[http://www.3ddownloads.com/Simulation/DropTeam/Demo/DropTeam_Linux_MP_Demo.tar.bz2](http://www.3ddownloads.com/Simulation/DropTeam/Demo/DropTeam_Linux_MP_Demo.tar.bz2)

thanks very much for you interest

---

### Post by slyjelly on 2006-12-09
a new error type:

./SpaceVikings: error while loading shared libraries: libslang-utf8.so.1: wrong ELF class: ELFCLASS64

this one is when booting the client from the usr local game folder, instaed of desktop or home folder

---

### Post by po0f on 2006-12-09
slyjelly,

I have to wait 8 min, *then* I can start downloading the 241MB file.  :rolleyes:

Helping you out is really no problem.  I do it for free, because I like to help others.  Just don't yell at me and it'll be all gravy.  :)

[EDIT]

Is your box a 64-bit installation of Ubuntu?  You'll probably run into a lot of problems trying to install games downloaded from the internet.

---

### Post by slyjelly on 2006-12-09
yes its 64 bit ubuntu

works great with doom 3 quake 4 and others, this is the last decent game left for me to try and its really appealing, everyne says its heavy on resources, perfect for my amd64 geforce 6600!!

i just wanna see my machine struggle for once!! :D

---

### Post by hytek on 2006-12-09
I found that the ia-32 libs (in synaptic) usually solves most of my errors with games or particular apps (like vmware server).

---

### Post by slyjelly on 2006-12-09
quote: I found that the ia-32 libs (in synaptic) usually solves most of my errors with games or particular apps (like vmware server).

thanks but i have them installed, they help with doom 3 and quake 4 etc.

This is slightly more tricky i think, probably due to dropteam being newer and more underdeveloped (is that a word?)

---


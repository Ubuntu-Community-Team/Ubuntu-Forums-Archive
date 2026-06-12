---
title: "Using Programs Installed from Synaptic"
date: 2007-07-20
forum: General Help
---

### Post by newbiefromwindows on 2007-07-20
I just installed Ubuntu on my computer using Wubi. Wubi works great and is a great way for windows users to try Linux.

I am having a problem downloading programs. If a program is under applications add/remove installation works great. However, I have so far been unable to download programs from the internet. With windows I just click download and it does it for me. 

Reading this: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

it says to use synaptic package manager to download programs. Synaptic seems to have anything you would ever want. I found a couple programs that I wanted and I downloaded them. The instructions on the linked page says that once you install with synaptic if the program does not create a short cut install the debian menu and use it to find the program. I got the package for Debian and followed this pages instructions to no avail. I have installed the package for the Debian menu, but I still don't have the menu after following the instructions.

I have tried getting help in the IRC channel none of which produced a Debian menu or the ability to run the programs I downloaded. I would be greatful for any help you can give me.

---

### Post by tgm4883 on 2007-07-20
> **newbiefromwindows said:**
> I just installed Ubuntu on my computer using Wubi. Wubi works great and is a great way for windows users to try Linux.

I am having a problem downloading programs. If a program is under applications add/remove installation works great. However, I have so far been unable to download programs from the internet. With windows I just click download and it does it for me. 

Reading this: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

it says to use synaptic package manager to download programs. Synaptic seems to have anything you would ever want. I found a couple programs that I wanted and I downloaded them. The instructions on the linked page says that once you install with synaptic if the program does not create a short cut install the debian menu and use it to find the program. I got the package for Debian and followed this pages instructions to no avail. I have installed the package for the Debian menu, but I still don't have the menu after following the instructions.

I have tried getting help in the IRC channel none of which produced a Debian menu or the ability to run the programs I downloaded. I would be greatful for any help you can give me.

Hadn't heard about the whole debian menu (why would i want another menu when I could just add the launcher myself)

What i usually do is after I install the software, if no menu laucher is added.  I open up terminal and try the name of the program (ie amarok)

If that doesn't work, i find it again in synapic, right click on it and go to properties.  Click on installed files.  then look for files that could start the program (I usually find them in /usr/lib)  (ie, for amarok it shows /usr/lib/amarok.  For totem /usr/lib/totem) I write these down and test them in terminal.

Once I find the right command I just open System > Preferences > Main Menu and make a new launcher for it

---

### Post by Nythain on 2007-07-20
a lot of programs available are command line programs...
what happens if you open up a terminal and try to type the name of the program? you could also use the command locate to find out if and where the program is installed to...

once you get it working, you could always add an entry for it in your applications menu

---

### Post by newbiefromwindows on 2007-07-20
> **tgm4883 said:**
> (why would i want another menu when I could just add the launcher myself)


Because the original menu that comes with Ubuntu is not showing the program. No one (at least no one who has previously been using a windows or mac computer) wants to enter lines of code into the directory to make something work. It should just work (this is not to say that Mac and Windows just work, but they don't have this particular problem).

Thanks for the help, I'll try the suggestion.

If anyone else can help me get a Debian menu (which at least supposedly eliminates the whole me typing code part) it would also be greatly appreciated.

---

### Post by tgm4883 on 2007-07-20
> **newbiefromwindows said:**
> Because the original menu that comes with Ubuntu is not showing the program. No one (at least no one who has previously been using a windows or mac computer) wants to enter lines of code into the directory to make something work. It should just work (this is not to say that Mac and Windows just work, but they don't have this particular problem).

Thanks for the help, I'll try the suggestion.

If anyone else can help me get a Debian menu (which at least supposedly eliminates the whole me typing code part) it would also be greatly appreciated.

Windows doesn't have that problem just like Ubuntu doesn't have that problem.  If a menu item isn't made, blame the program, not the OS.

On a different note.  If you can't handle a little (and I mean little) command line (or the run box if your prefer), then linux probably isn't for you.  Some time down the road, your going to have to enter a command in somewhere.

---

### Post by newbiefromwindows on 2007-07-20
> **tgm4883 said:**
> Windows doesn't have that problem just like Ubuntu doesn't have that problem.  If a menu item isn't made, blame the program, not the OS. 

A technical difference which the average computer user doesn't really care about. I have no windows program which when installed it didn't place itself in the start menu and give me a shortcut on the desktop if I wanted it. My understanding is that there are many programs which are only available through synaptic or something like it. So no, it is not necessarily the fault of linux or ubuntu that this is a problem. However, the fact that there are several programs which don't automatically add themselves to the start menu is a problem.

> **tgm4883 said:**
> If you can't handle a little (and I mean little) command line (or the run box if your prefer), then linux probably isn't for you.  Some time down the road, your going to have to enter a command in somewhere.

I have quickly come to understand this. And that's fine, but to nontech savvy users (a day with Ubuntu/linux and I have put myself back into the nontech savvy category! I was born there was a computer in my house, I grew up with them, I help friends and family when they have computer problems) command is a massive headache. Telling someone who sets up Ubuntu (I read reviews of various linux versions and this seemed to be one of the most widespread and idiot friendly)  that they have to use command is like telling a windows xp user that they are going to have to open up MS Dos to use certain things.

---

### Post by tgm4883 on 2007-07-20
> **newbiefromwindows said:**
> A technical difference which the average computer user doesn't really care about. I have no windows program which when installed it didn't place itself in the start menu and give me a shortcut on the desktop if I wanted it. My understanding is that there are many programs which are only available through synaptic or something like it. So no, it is not necessarily the fault of linux or ubuntu that this is a problem. However, the fact that there are several programs which don't automatically add themselves to the start menu is a problem.


Actually, it's more the opposite.  There are no programs that only synaptic has (well, maybe meta packages but you can still download and install those elsewhere).  Thats the nature of repo's.  Your not going to have every piece of software in it

> **newbiefromwindows said:**
> 
I have quickly come to understand this. And that's fine, but to nontech savvy users (a day with Ubuntu/linux and I have put myself back into the nontech savvy category! I was born there was a computer in my house, I grew up with them, I help friends and family when they have computer problems) command is a massive headache. Telling someone who sets up Ubuntu (I read reviews of various linux versions and this seemed to be one of the most widespread and idiot friendly)  that they have to use command is like telling a windows xp user that they are going to have to open up MS Dos to use certain things.

True, I suppose I could have given you instructions without using the command line, but I chose to go the easier route.  In windows, you still have to know the execution command, and rather than send you on a wild goose chase looking for the software, I gave you an easier way.

There are a few administrative things that are done easier/quicker in the command line in windows instead of using their GUI counterparts.

I suppose the problem lies in the fact that you expect Windows users to come here and expect everything to work in a windows way, which simply isn't the case.  If you want it to work like windows, then use windows.  There is no person (that knows what they are talking about) that says linux is better than windows simply because linux is an alternative to windows.  And alternatives usually have an alternative way of doing things.

---


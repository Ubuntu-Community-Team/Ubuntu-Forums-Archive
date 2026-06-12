---
title: "Menu items not showing up after install."
date: 2007-02-04
forum: General Help
---

### Post by ZaphodBbl on 2007-02-04
The problem is that, after installing many software packages, I started to notice that the program links were not showing up in the Applications menu.  I've looked in /usr/share/menu, and I see the names of files that I've installed there, some of which do not show up in my menu.   Comparing files there with others there that did show up in my menu showed no discernable difference in how they were made, other than the locations of some of the configuration lines.  I tried changing a few to match the format of ones that did show up in the menu, but that didn't work.

I've looked in several places for the answer to this problem.  Some referred me to /usr/share/menu, some to /<home directory>/.gnome/Apps, and probably another place or two that I am too upset to remember.  Sorry, but I do get frustrated easily.

I looked in /.gnome/Apps, and there are desktop configuration files there for every program I can remember installing.  They can't be edited, though (I tried gedit on them).  So I don't think those are going to solve the problem.

This is not an Edgy problem.  It happened in Dapper, too.  But in Dapper, there was this nice little Debian menu addon that could be installed (I can't remember the name of it right off hand) that showed everything that had been installed.  I can't find it in the Synaptic list anymore, though, so I guess it was removed.

What I want to know is where do I go, or what do I do (other than manually adding the programs to the menu using that extremely slooooow menu layout program), to get those program links to show up in the menu where they belong.

Anyone who can help with this will have my undying gratitude.  I might even name my firstborn child after you. Thank you for your time.

I hope this is in the right section of the forum, but I couldn't see an adequate heading to put it under other than this one,.

---

### Post by STREETURCHINE on 2007-02-04
have you looked in synaptic for" debian menu"

i have always used automatix for this.

---

### Post by ZaphodBbl on 2007-02-04
Okay.  I did find the Debian menu addon, and it's installed.  But the Debian menu entry isn't showing up in Ubuntu.  I installed the KDE package and it shows up there, but not in Gnome.  Strange, huh?

I'll have to look up this automatix.  I've never heard of it before.  Thanks for the tip.

Edit:  I installed Automatix, but it doesn't do what I need to do.  All I really want to know is where the Gnome Applications menu stores it's information.  Can someone who knows please provide an answer for that?  Again, any help is greatly appreciated.

---

### Post by ZaphodBbl on 2007-02-04
I know someone has to know the answer to this,  Please, give me a hand here.  I'll put you in my will.  :)

---

### Post by enixon on 2007-02-06
I'm having the same problem!

---

### Post by meng on 2007-02-06
It depends on what you're installing. Not everything comes with a menu entry. So perhaps if you told us what programs you've installed ... we could help.

---

### Post by enixon on 2007-02-06
The only thing I've installed that added its own menu icon was programming tools, and games. Every thing else does not put it's own icon in the app menu after being installed. I have no idea how to open the apps after synaptic manger has installed them. Thats the real issue here. For instance, If you download 3d desktop from the synaptic manger, it installs it for you but gives you no way of knowing how to start it. The debian menu doesn't show up what so ever, even after installation and restart.

I'm on ubuntu edgy, 64bit amd

---

### Post by meng on 2007-02-06
Okay so you've told us ONE of the applications that you installed, 3ddesktop. Not surprisingly, it doesn't have a menu entry, it's not meant to! See here for instructions:
[http://linuxreviews.org/features/3ddesktop/](http://linuxreviews.org/features/3ddesktop/)
There's plenty of other sites with instructions too, Google will help you out.

Now, any other questions?

---

### Post by RUSHMORE? on 2007-03-07
dangit! i'm having the same problem. i'm uning kubuntu 6.06 LTS and i installed "alien" for installing non-active packages but its not showing up and its buggin the crap outta me. i tried looking in /usr/bin/alien etc etc but it doesnt work. any help?:confused:

---

### Post by Benjabba on 2007-05-31
I am having the same problem, I used synaptic to install a program called "dome" which calculates and designs domes.  I cannot find it in any menu, synaptic shows it as installed.
Please help. Ubuntu 7.04 Feisty faun.

---

### Post by measekite on 2007-10-18
> **ZaphodBbl said:**
> The problem is that, after installing many software packages, I started to notice that the program links were not showing up in the Applications menu.  I've looked in /usr/share/menu, and I see the names of files that I've installed there, some of which do not show up in my menu.   Comparing files there with others there that did show up in my menu showed no discernable difference in how they were made, other than the locations of some of the configuration lines.  I tried changing a few to match the format of ones that did show up in the menu, but that didn't work.

I've looked in several places for the answer to this problem.  Some referred me to /usr/share/menu, some to /<home directory>/.gnome/Apps, and probably another place or two that I am too upset to remember.  Sorry, but I do get frustrated easily.

I looked in /.gnome/Apps, and there are desktop configuration files there for every program I can remember installing.  They can't be edited, though (I tried gedit on them).  So I don't think those are going to solve the problem.

This is not an Edgy problem.  It happened in Dapper, too.  But in Dapper, there was this nice little Debian menu addon that could be installed (I can't remember the name of it right off hand) that showed everything that had been installed.  I can't find it in the Synaptic list anymore, though, so I guess it was removed.

What I want to know is where do I go, or what do I do (other than manually adding the programs to the menu using that extremely slooooow menu layout program), to get those program links to show up in the menu where they belong.

Anyone who can help with this will have my undying gratitude.  I might even name my firstborn child after you. Thank you for your time.

I hope this is in the right section of the forum, but I couldn't see an adequate heading to put it under other than this one,.

You said this better than I did that is why I am quoting your entire message.

In Windows, which I am attempting to transition away from, you type setup and your program (package) gets installed.  During the process the install program will usually ask you if you want an icon on the desktop and or in the task bar and automatically places a menu entry in Program Files.

As you stated this does not happen in Linux (Ubuntu Feisty 7.04).  So I am asking the same question as you are.  Now if you could find the executable (something that you can type on the command line without a sudo prefix then you might be able to add it to the menu system manually.

Now there was one program where I found some script in /usr/share that when I typed the name it made the entry for me but for many other programs, as you, I do not have a clue.

Can anyone out there provide an answer to the question that so many people are having a problem with and that is so basic?

---

### Post by eldergod on 2007-10-22
> **meng said:**
> Okay so you've told us ONE of the applications that you installed, 3ddesktop. Not surprisingly, it doesn't have a menu entry, it's not meant to! See here for instructions:
[http://linuxreviews.org/features/3ddesktop/](http://linuxreviews.org/features/3ddesktop/)
There's plenty of other sites with instructions too, Google will help you out.

Now, any other questions?

There is a program, which after its installed, creates an entry in your applications menu called "Debian" and it has EVERY program installed, weather the program creates a menu entry or not. I have used it before but can't remember what or where it is.
I am having an issue with codeweaver not creating a menu entry which it used it in 7.04, but not in 7.10

---

### Post by peter brasem on 2008-01-01
I am experiencing the same in Gutsy when installing Eagle 4.16, no tag appears in the application menu. However when installing Kicad , a similar schematic and pcb layout program, a kicad sub tag appears under the Application Programming header. 
And this opens another question, since PCB layout design is not "Programming" is there a way to create additional  Application/menu  headers say for example "Hardware Design" under which Kicad and Eagle 4.16 can be installed/found/launched?

---


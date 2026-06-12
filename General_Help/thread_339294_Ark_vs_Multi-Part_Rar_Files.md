---
title: "Ark vs Multi-Part Rar Files"
date: 2007-01-15
forum: General Help
---

### Post by stormyuk on 2007-01-15
Hi,

I have installed the archive utilities in Automatix in Kubuntu and I can get Ark to see the Rar files but if I try and open a multi part Rar it just extracts the one piece, the odd this is Ark seems to realise the full file should be 300Mb+ yet only extracts the one part which it also realises is only 14Mb or so.

How do I get it to extract the Rar sequence? This file is not corrupt as it extracts in WinRar in windows, Ark reports it as Version 2.

Cheers,

Mike

---

### Post by taurus on 2007-01-15
You can unpack the first one and it will automatically unpack the rest from a terminal.

```
unrar x first_rar.rar
```

---

### Post by stormyuk on 2007-01-15
Thanks, is there no way to do it in the Ark-GUI? Its a bit of a ballache getting the path info right and then trying to get it to output to the right dir :(

Cheers,

Mike

---

### Post by stormyuk on 2007-01-16
If there is no way in Ark is there another way to handle multi-part rars in some kind of GUI?

Is there another application maybe or something within Konqueror which will allow the support of multi rar files?

Cheers,

Mike

---

### Post by Hallvor on 2007-01-16
I have the same problem. Help would be appreciated.

---

### Post by stormyuk on 2007-01-17
Hi,

So far the only viable options I have had from help on other forums is:

1. rargui2

[http://www.vsite.gr/modules/mydownloads/viewcat.php?cid=4](http://www.vsite.gr/modules/mydownloads/viewcat.php?cid=4).

2. use winrar via wine

I was really hoping there would be a better way. :(

I have not tried the rargui2 but if anyone knows of a way to get Konqueror/Ark to support multi-part Rars properly I would really appreciate it.

I also wonder if it depends how the multi part rar is named, for example sometimes they are file_part1.rar, file_part2.rar etc and othertimes file.rar, file.r01, file.r02 etc. but unrar (in command line) and of course winrar (in XP) dont seem to have any trouble with either.
 
Cheers,

Mike

---

### Post by Hallvor on 2007-01-17
Perhaps this thread will help you: 

[http://ubuntuforums.org/showthread.php?t=339986&highlight=rar](http://ubuntuforums.org/showthread.php?t=339986&highlight=rar)

Multi part rar-files work just like in Winrar for me after this.

Hope it solves your problem.


Hallvor

---

### Post by stormyuk on 2007-01-17
Are you using Ark or File-roller Hallvor? File-roller is for Gnome isnt it? What are the implications of me installing it in KDE and how would I do it? Will I have to install a lot of other Gnome stuff?

(i have the unrar-nofree and rar installed already)

Cheers,

Mike

---

### Post by Hallvor on 2007-01-17
I`m using the file roller/archive manager on ubuntu dapper. Think it`s on gnome, but I can`t answer your question. (I`m just a newbie, having used Ubuntu for less than a month.) Perhaps some of the more experienced users can give you a hint.

Anyway, good luck! :)

---

### Post by stormyuk on 2007-01-17
Yeh, I don't really want to install file-roller if I can avoid it, I just wish I knew what was going on with my Ark and why it wont do such a simple task for me. Been struggling with this for 2 days now! :( very demoralising that I cannot get such a simple thing working.

At this stage I dont know if its a bug or something wrong with my setup.

Mike

---

### Post by Patrick-Ruff on 2007-01-17
why can't you guys be content with the terminal?  who needs a GUI to extract files from an archive . . . what does it matter? after they're extracted you'll be accessing them with the GUI. 

don't be afraid of the terminal, it's your friend.

---

### Post by stormyuk on 2007-01-17
If they are in /home/me then fine but I have lots of files on my existing windows partitions which are buried in long paths, its just so ultra tedious having to type those multiple paths in.

I just want the GUI to work. :(

---

### Post by Patrick-Ruff on 2007-01-17
lol it always cracks me up to see people so addicted to the GUI that their whole world comes crashing down at the thought of using a terminal . . . .

you know, you can make a custom script for it . . .

---

### Post by stormyuk on 2007-01-17
Aww :( I dont want this to turn into a GUI vs Command Line debate, if you dont like the GUI I am happy for you. :) I do actually use the terminal for lots of commands and I love the commands that are available via the command line.

I do like the GUI too and prefer to use it for some operations, Rar/Unrar is one of them. Its just I cannot get it to work properly so would like some assistance.

Cheers,

Mike

---

### Post by Patrick-Ruff on 2007-01-17
this isn't a GUI vs Command Line debate.

the command line appears to be your only option, and you are denying it.


see, GUI's have pre-defined commands that they run whenever you press a button, keystroke, click, etc.  basically, everything you're doing is still going through the terminal in some sense, to actually make functions work if they are malfunctioning, the GUI either has special settings, or you have to reprogram it. 

at this moment, you don't appear to be the type of person that could reprogram a GUI to work for you, you have to use the command line for these particular needs, if not, I doubt you'll find a real solution.

---

### Post by stormyuk on 2007-01-17
Reading between the lines in some threads here and on other forums, *some* people seem to have Ark working with multi-part rar's or at least thats the impression I get. 

Thats why I am trying to narrow down if its really just me that has this problem, or if its ark thats doing something odd. If its the latter I can always try reporting it on the KDE bug website I suppose.

Mike

---

### Post by stormyuk on 2007-01-17
Most curious, I have just booted up today and its working, lol. I am not doing anything differently...

I really cannot understand it now..

Mike

---


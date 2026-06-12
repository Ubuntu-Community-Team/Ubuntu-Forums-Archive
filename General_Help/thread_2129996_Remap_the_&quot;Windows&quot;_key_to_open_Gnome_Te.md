---
title: "Remap the &quot;Windows&quot; key to open Gnome Terminal."
date: 2013-03-28
forum: General Help
---

### Post by KittyCatHerder on 2013-03-28
I spent 15 minutes searching the forum for an answer to this question but did not find one. Perhaps I don't quite understand how the search system here works. Anyway, I'm trying to map my Windows key to open Gnome Terminal. I have done this before in another Ubuntu 11.10 based OS but I do not remember how, and I haven't been able to find exact instructions by searchign the internet. I guess I would just have to remap the key to "ctrl+alt+T" but I can't seem to find the way. I'm sure someone else has done this before and it should be pretty simple, right?

---

### Post by KittyCatHerder on 2013-03-28
Can no one help me? I have been searching far and wide, trying all kinds of suggestions I found on the internet, installed several pieces of software including xbindkeys which didn't work. There is another piece of software that promises to allow me to map my windows key to open terminal but it is something like 372 megabytes and I'm running a 60GB SSD.

I can't believe it is so difficult to figure out how to remap a single key to run a single command in Ubuntu 12.04!!!!!

---

### Post by Vaphell on 2013-03-29
may i ask why you want to sacrifice usability of the whole environment for the trivial thing that has perfectly usable key combo already? WIN is the master key in unity, not yet another unimportant key you can just override.

---

### Post by Slim Odds on 2013-03-29
> **Vaphell said:**
> may i ask why you want to sacrifice usability of the whole environment for the trivial thing that has perfectly usable key combo already? WIN is the master key in unity, not yet another unimportant key you can just override.
+1

---

### Post by CaptainMark on 2013-03-29
I think since gnome3 the win key is considered a modifier key for shortcuts and can't be used on its own as a standalone keyboard shortcut

---

### Post by Stonecold1995 on 2013-03-29
> **Vaphell said:**
> may i ask why you want to sacrifice usability of the whole environment for the trivial thing that has perfectly usable key combo already? WIN is the master key in unity, not yet another unimportant key you can just override.
Is it the same on KDE?  If not, I've been looking for the same thing as OP (except I want it to open KickOff).

---

### Post by KittyCatHerder on 2013-03-30
> **Vaphell said:**
> may i ask why you want to sacrifice usability of the whole environment for the trivial thing that has perfectly usable key combo already? WIN is the master key in unity, not yet another unimportant key you can just override.

I don't run Unity and the Super key does nothing on its own. On the contrary, I won't be sacrificing any usability. I will be reducing three key strokes using two hands to one key stroke.

---

### Post by KittyCatHerder on 2013-03-30
> **CaptainMark said:**
> I think since gnome3 the win key is considered a modifier key for shortcuts and can't be used on its own as a standalone keyboard shortcut

Surely with an open source OS there is a way to change the software so that the Super key can be used as a stand alone short cut key! Given that maybe it's something I won't want to do once I learn the other things that that will be caused by changing whatever needs to be changed in order for it to work but I guess I will cross that bridge when I come to it.

Do you think it makes any difference that I don't run Gnome 3? I'm using Gnome Classic.

---

### Post by coldcritter64 on 2013-03-30
> **KittyCatHerder said:**
> I don't run Unity and the Super key does nothing on its own. On the contrary, I won't be sacrificing any usability. I will be reducing three key strokes using two hands to one key stroke.
[s]What DE are you using ?[/s] Gnome classic, d'oh  #-o

On non Unity / Gnome-shell installs it may be possible via System settings > Keyboard > Keyboard shorcuts tab,  and assign a custom key setting for the Super key (Windows key) to utilise the command "gnome-terminal".

---

### Post by KittyCatHerder on 2013-03-30
> **Stonecold1995 said:**
> Is it the same on KDE?  If not, I've been looking for the same thing as OP (except I want it to open KickOff).

I have found a technique for changing the key bindings so that you can cause a key combination to run a command. It has worked for me yet but I'm not sure why. Maybe, as another post in this thread suggests, the Super key can not be used as a stand alone short cut key in envnments newer than Gnome 2. 

Anyway, running gksudo gconf-editor and navigating to the /apps/metacity/global_keybindings, you can edit the value field of one of the ten empty run_command_X entries to reflect the keys/key combos that you want to use, and then navigate to the corresponding keybinding_commands field and change the value to whatever command invokes the process that you want to run. 

Like I said, this hasn't worked for me yet but I suspect I'm doing something wrong. Maybe it hasn't worked because the Super key can't be mapped as a stand alone short cut key in environments after Gnome 3. I will add more information as I get it.

---

### Post by Vaphell on 2013-03-30
the environment you use and the tech it's built upon are important. Granted, you had your post tagged with gnome, but didn't make it 100% clear that you are not running stock ubuntu configuration. Is it gnome classic based on gnome2 or gnome3 libraries (i assume gnome3)?

---

### Post by KittyCatHerder on 2013-03-30
> **coldcritter64 said:**
> What DE are you using ?

On non Unity / Gnome-shell installs it may be possible via System settings > Keyboard > Keyboard shorcuts tab,  and assign a custom key setting for the Super key (Windows key) to utilise the command "gnome-terminal".

I'm using Gnome Classic. I tried for a long while to find a way to accomplish the task with the keyboard short cut settings but I don't think there is a way to do it using that. I changed some stuff in the /apps/metacity/global_keybindings and the /apps/metacity/keybinding_commands files, in the same way I got it to work on Ubuntu 11.10 a year or so ago, but it hasn't worked. I suspect this method can still work and that I'm just missing a step somewhere. I tried calling the Super Key "Super_L", "Super", "<Super_L>", "Super", and so on until I tried all the possible combinations. 

Nothing has worked o far but I'm going to keep trying, hopefully with new information learned here.

---

### Post by KittyCatHerder on 2013-03-30
> **Vaphell said:**
> the environment you use and the tech it's built upon are important. Granted, you had your post tagged with gnome, but didn't make it 100% clear that you are not running stock ubuntu configuration. Is it gnome classic based on gnome2 or gnome3 libraries?

I'm running Ubuntu 12.04, Gnome Classic, but I don't know which libraries the Gnome Classic environment are built upon. If you can tell me how to find out I will look and post the answer here.

What is the difference, relatively, between Gnome Classic being based on the Gnome 2 or Gnome 3 libraries? Is it because, as another poster suggested, Gnome 3 and later don't allow for the Super key to be mapped as a stand alone short cut?

---

### Post by CaptainMark on 2013-03-30
You _*ARE*_ running gnome 3, you are confusing Gnome 3 with gnome-shell they are totally different things. Gnome 3 is the underlying libraries which are used by a lot of common desktop environments including gnome-shell, gnome-classic, unity and cinnamon. They all still use gnome 3

---

### Post by KittyCatHerder on 2013-03-30
> **CaptainMark said:**
> You _*ARE*_ running gnome 3, you are confusing Gnome 3 with gnome-shell they are totally different things. Gnome 3 is the underlying libraries which are used by a lot of common desktop environments including gnome-shell, gnome-classic, unity and cinnamon. They all still use gnome 3

I don't know about gnome-shell. I haven't learned anything about that yet so I couldn't be confusing it with Gnome 3. I'm gonna have to Google some Gnome+X stuff. I guess maybe that explains why editing /apps/metacity/global_keybindings and /apps/metacity/keybinding_commands doesn't work. Now the question is, what is the right way to make Super_L invoke gnome-terminal.

---

### Post by KittyCatHerder on 2013-03-31
> **CaptainMark said:**
> You _*ARE*_ running gnome 3, you are confusing Gnome 3 with gnome-shell they are totally different things. Gnome 3 is the underlying libraries which are used by a lot of common desktop environments including gnome-shell, gnome-classic, unity and cinnamon. They all still use gnome 3

So what is Gnome 3 and what is gnome-shell? Gnome 3 is a set of files, but it's not also its own seperate desktop environment? I haven't heard of gnome-shell before you mentioned it. What's the difference between gnome-shell and gnome-classic? 

In trying to figure this out, I came across some documentation that said the newest Unity interface (I don't remember which is the current version) includes and option to use the newest libraries while also reverting the look of the interface to something more similar to gnome-classic. I do like the idea of having the newest software and that's true of  whatever UI libraries/version I am running on my Ubuntu installation. I  can't do Unity on this 1024 X 600 netbook so I do hope there is a way to remap my keys to whatever I want without using Unity. I am obviously confused by all of these versions and libraries and stuff. Who can help clue me in?

---

### Post by iaw4 on 2013-04-03
is there an answer to this thread?

I actually don't want the control=control, alt/option=windows, and command=alt keys (Mac=Windows) to do anything by themselves.  I only want them to be used as modifiers (just like the control key).

I hit these accidentally a lot and it interrupts the flow of whatever window I am in.

/iaw

---

### Post by CaptainMark on 2013-04-03
> **KittyCatHerder said:**
> So what is Gnome 3 and what is gnome-shell? Gnome 3 is a set of files, but it's not also its own seperate desktop environment? I haven't heard of gnome-shell before you mentioned it. What's the difference between gnome-shell and gnome-classic? 

In trying to figure this out, I came across some documentation that said the newest Unity interface (I don't remember which is the current version) includes and option to use the newest libraries while also reverting the look of the interface to something more similar to gnome-classic. I do like the idea of having the newest software and that's true of  whatever UI libraries/version I am running on my Ubuntu installation. I  can't do Unity on this 1024 X 600 netbook so I do hope there is a way to remap my keys to whatever I want without using Unity. I am obviously confused by all of these versions and libraries and stuff. Who can help clue me in?
Wikipedia describes it better than I can > The GNOME project provides two things: The GNOME desktop environment, a graphical user interface and core applications like Web, a simple web browser, and the GNOME development platform, an extensive framework for building applications that integrate into the rest of the desktop and mobile user interface.So the first part (the desktop environment) is what you see when you interact with the computer, gnome-shell, unity, gnome-classic, kde, cinnamon are all examples of these
The second part (the development platform) is all the bits you don't see that make the desktop environment work as it does.

Off topic now, so I'll but out here because I can't help with your original post
Sorry

---

### Post by KittyCatHerder on 2013-04-05
> **iaw4 said:**
> is there an answer to this thread?

I actually don't want the control=control, alt/option=windows, and command=alt keys (Mac=Windows) to do anything by themselves.  I only want them to be used as modifiers (just like the control key).

I hit these accidentally a lot and it interrupts the flow of whatever window I am in.

/iaw

So far my question has not been answered but I think I might be able to help you anyway.

If you gksudo gconf-editor, navigate to /apps/metacity/global_keybindings, you will see a list of the keys on your keyboard and the things that they shorcut to. From here you can change keys to be shortcuts or not be shortcuts. You might have to also navigate to /apps/metacity/keybinding_commands and change the corresponding key commands to accomplish what you want. I am not well versed in this method and I don't know what might go wrong as a result of changing things here. I'm also not 100% clear on the syntax and format that needs to be used when re defining your keys so at least look at examples from existing entires so that you can get an idea of how to define the keys with the correct format.

Unfortunately it doesn't work for the Super key, something to do with Gnome 3 not allowing the Super key to be a stand alone short cut. I'm still looking for an answer to my question but I hope I could help you with yours.

---

### Post by KittyCatHerder on 2013-04-05
> **CaptainMark said:**
> Wikipedia describes it better than I can So the first part (the desktop environment) is what you see when you interact with the computer, gnome-shell, unity, gnome-classic, kde, cinnamon are all examples of these
The second part (the development platform) is all the bits you don't see that make the desktop environment work as it does.

Off topic now, so I'll but out here because I can't help with your original post
Sorry

OK, so, the way I thought of it was correct after all. Gnome 3 describes the version of the user interface and Gnome-Shell describes what the interface is made of that is not in user space.

Thanks for helping with that. I can't learn enough fast enough about this stuff!

---

### Post by CaptainMark on 2013-04-05
> **KittyCatHerder said:**
> OK, so, the way I thought of it was correct after all. Gnome 3 describes the version of the user interface and Gnome-Shell describes what the interface is made of that is not in user space.

Thanks for helping with that. I can't learn enough fast enough about this stuff!
Urm you have the concept but it's the other way round, Gnome-Shell is the user interface Gnome3 is the behind-the-scenes structure

---

### Post by coldcritter64 on 2013-04-05
> **CaptainMark said:**
> Urm you have the concept but it's the other way round, Gnome-Shell is the user interface Gnome3 is the behind-the-scenes structure
+1, this OP.

---

### Post by KittyCatHerder on 2013-04-21
Well, I have pretty much given up on this for now. I have been trying to figure this out for 3 weeks and I haven't been able to find any definitive information. Please post if you know the answer.

---

### Post by HermanAB on 2013-04-21
Hmm, umpteen responses and not a single soul with the correct answer.

You need to read the xbindkeys and xmodmap man pages.  With those two, you can do anything.

Oh, and xev.

---

### Post by KittyCatHerder on 2013-04-22
> **HermanAB said:**
> Hmm, umpteen responses and not a single soul with the correct answer.

You need to read the xbindkeys and xmodmap man pages.  With those two, you can do anything.

Oh, and xev.

Sounds like a good idea. I'll try that out! Thanks!

---

### Post by prodigy_ on 2013-04-22
> **Vaphell said:**
> why you want to sacrifice usability of the whole environment
Now if only Unity had any usability to sacrifice...

---


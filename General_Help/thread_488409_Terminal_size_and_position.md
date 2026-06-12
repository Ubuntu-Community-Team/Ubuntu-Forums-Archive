---
title: "Terminal size and position"
date: 2007-06-30
forum: General Help
---

### Post by PaulFXH on 2007-06-30
I have tried using this command
```
gnome-terminal --geometry 150×25+100+80
```
either in a terminal (to open another terminal) or in System>Preferences>Main Menu>Applications>Accessories>Terminal>Properties>Command in an effort to always get the terminal to show up with the same size and at the same location on the screen.
Strangely, it doesn't seem to affect either the size or the screen position of the terminal on my computer.
Anybody know why?

---

### Post by mali2297 on 2007-06-30
When I copied the line into my terminal, I got an error. However, when I changed "×" into "x", it worked just fine. 

By the way, how do you create this character "×"?

---

### Post by PaulFXH on 2007-06-30
Thanks for your reply.
I got this tip from this [link]("http://www.ultimolog.com/2007/06/26/otimizandocustomizando-definindo-a-posicao-e-o-tamanho-da-janela-do-terminal-no-ubuntu/") which is actually in the Portuguese language.
Nevertheless, even with the larger "x", it still only works from the terminal and not by making the change in System>Prefernences>Main menu>Terminal as the oriinal link suggests.
Does anybody know how to change the terminal size and position permanently in Ubuntu?

---

### Post by strabes on 2007-06-30
In KDE you can set the default size/llocation of any window or application in the menu conveniently located in the right click menu of the titlebar. I don't know about gnome.

---

### Post by PaulFXH on 2007-06-30
Yes, doing this in Gnome seems to be a bit of a mystery.
However, if it can be done in KDE, it would be quite amazing if it had been completely forgotten about in Gnome.
I came across this [thread]("http://ubuntuforums.org/showthread.php?t=255048&page=2") which seems to provide an answer. However, once again, it just doesn't work for me.
One thing, though, is that my terminal size and position seem to always be the same (just not the size and location I would prefer). So, these parameters must be fixed somewhere.
Anybody else knows how to do this?

---

### Post by taisao on 2007-07-08
try this to see if it works:

**gnome-terminal --geometry=130x25+20+525**

if that does work, then you can change the size to yours liking in this format:
**--genometry=widthxheight+positionHor+positionVer**

and if you want to use it as default, then:

**System -> Preferences -> Preferred Applications -> System**

For *terminal emulator *select **Custom**
fill yours liking at Command in, example: **gnome-terminal --geometry=130x25+20+525**
and execute flag with nothing :)

---

### Post by zorba64 on 2007-07-09
I simply put this
gnome-terminal --geometry=105x30 
in the command section of the Launcher Properties on the panel.

I use a 1024x768 desktop and it seem to centre quite nicely.

---

### Post by PaulFXH on 2007-07-09
> try this to see if it works
Tried it, unfortunately doesn't work but this is no different than the command I mentioned in the first post.
Assuming it is not just a matter of luck as to whether this command works or not, I'm still looking for whats so different on my computer that I cannot get this simple command to work.

---

### Post by taisao on 2007-07-09
that's weird, then I don't know :(

But just to make sure

[LIST]
[*]it's just a small x
[*]this is my setup:
[IMG][IMG]http://img.photobucket.com/albums/v292/WhyYouPickMyName/comp/Screenshot-1.png[/IMG][/IMG]
[/LIST]

---

### Post by PaulFXH on 2007-07-10
Thanks you very much for the detailed tutorial and indeed I have now made some progress but there are still some mysteries here.
First, it seems my problem with getting this command to work in a terminal was simply due to a typo (look at the command in my first post which is missing the equals sign after the word "geometry"). With the equals sign included it works fine, but only from a terminal.
Now, the remaining mystery centers on the fact that, on my computer,  I can open a terminal in three different ways (in addition to from another terminal):
1) From launcher in AWN dock
2) From icon in top panel
3) From Applications>Acessories>Terminal

When I make the changes to the Properties section of the Main Menu item Terminal, the first two Terminal opening procedures above continue to give the exact same size terminal as before.
But, the third one opens a terminal with size and position as demanded by the newly-added command.

I think this should now be easier to resolve although as yet I have no clear idea where the problem is.

---

### Post by taisao on 2007-07-10
You're welcome.

> 
1) From launcher in AWN dock
2) From icon in top panel
3) From Applications>Acessories>Terminal

All three are just shortcut, the shortcut from place 1 and 2 are created before you edit the terminal item in the main menu. So they dont have that --geometry... , but only gnome-terminal. You can change it by right clicking the shortcut, select propeties and then you can file in the --geometry things.

Or you can delete the 2 shortcut and make a new one that is base on the one from the main menu. Just do what you like.

--
--geometry should work with most applications (that is what I think), so if you want you can use that for others applications too.

--

oh, and here is a extra way to fire up the terminal, using keyboard shortcut is very handy, how you can modify the keyboard shortcut can be found at System Preferences.

---

### Post by PaulFXH on 2007-07-11
Yes, you hit the nail right on the head.
I deleted the icons from AWN and the top panel and replaced them from Applications>Acessories>Terminal and now all terminal conform to what is demaned by the "geometry" part of the comand.
Very many thanks
Paul

---


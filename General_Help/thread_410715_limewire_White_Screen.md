---
title: "limewire White Screen"
date: 2007-04-16
forum: General Help
---

### Post by spankymasterc on 2007-04-16
Well i got limewire Pro 12.13.0 beta and it install fine and everything but when i try to run it opens and ill i see is a white screen

---

### Post by andrew.46 on 2007-04-17
Hi,

 Sounds like a Java problem. Not sure about Limewire but I have seen similar problems with Frostwire and normally much of this is fixed by install / reinstall (Sun) Java.

                           Andrew

---

### Post by rocknrolf77 on 2007-04-17
Do you have beryl? I get a blank windows too with frostwire when I run beryl. If you do try swithing from beryl to metacity from the tray icon when running *wire :)

---

### Post by spankymasterc on 2007-04-18
Fixed!

it was a problem with java so i looked around 

found that i had to tweak it a little so all i did was make a startup script

> #!/bin/bash
cd /usr/lib/LimeWire/
export AWT_TOOLKIT=MToolkit && java -jar LimeWire.jar 

made it and saved it as Limewire_fix.sh 

and changed the command on the limewire icon done if anyone else needs help hit me up :D

the fix is for java 6

---

### Post by dragoncow2 on 2007-05-13
I've tried java1.5 and 1.6, I get a white screen on both. I can set my window manager to metacity and then it shows up - and then switch it back to beryl and it continues to work just fine. quirky little bug. :)

---

### Post by QwUo173Hy on 2007-06-02
Worked for me Spanky, thanks.

<edit> Whoops, it doesn't take keyboard input... If I figure this one out I'll post up here </edit>

---

### Post by karmy on 2007-07-16
> **spankymasterc said:**
> Fixed!

it was a problem with java so i looked around 

found that i had to tweak it a little so all i did was make a startup script



made it and saved it as Limewire_fix.sh 

and changed the command on the limewire icon done if anyone else needs help hit me up :D

the fix is for java 6

Could you please explain what exactly did you do?
Made this startup script, and saved it in /etc/init.d/ directory. 
But what about this changing command on LimeWire icon? :confused:


EDIT:
Never mind - found solution [here]("https://help.ubuntu.com/community/LimeWire")

---

### Post by kkkkatie on 2007-10-13
Hey, I'm new to this but I had this problem so i quit lime wire, got rid of all my desktop effects and backgrounds - basically went back to factory settings, Then i started it up and all was fine, with the programme still open, I put my settings back to normal and now it runs fine. :KS

---


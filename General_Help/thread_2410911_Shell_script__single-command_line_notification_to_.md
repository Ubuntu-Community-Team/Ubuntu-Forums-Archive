---
title: "Shell script // single-command line notification to IRC/Discord/Something else?"
date: 2019-01-22
forum: General Help
---

### Post by melsen on 2019-01-22
Hello,

i'm looking for a command line tool that can take an input parameter and paste it as a notification straight to ... something over the internet... an IRC channel.. a discord channel... something.

I found a 3rd party developed fb-messenger-cli, but that doesn't work unfortunately.. 

I'm running a shell based application, that receives and sends text from a network monitor at work.
From within that application, I can set up an event, that can do various actions, based in the text it receives..
This application has a system function, that can execute a shell command in the background.. so what I'm trying to accomplish, is a setup where I with one single command, can write a specified text to for example my own IRC channel, to share information with others? (doesn't have to be discord.. just something a group of people can get notifications on their phone from - android and iOS)


Does anyone know how to accomplish this?

---

### Post by dragonfly41 on 2019-01-22
Just one idea.
There is a very basic accessory named Actiona which you can use to mockup various automation tasks.
It is in the Software Centre.
After creating an Actiona script (and testing in the GUI) it can be run by the command

actexec myscript.ascr

---

### Post by melsen on 2019-01-22
I only have shell access... so cant go that route,,,,

---


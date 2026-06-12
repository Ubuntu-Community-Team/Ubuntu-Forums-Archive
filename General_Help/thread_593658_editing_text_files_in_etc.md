---
title: "editing text files in /etc"
date: 2007-10-27
forum: General Help
---

### Post by telovoyagarcar on 2007-10-27
I don't understand why there is not a "switch to administrator" button in every GUI application that might need it.

Im using Kubuntu and need to edit the blacklist file trying to make work my wireless card .
Sure... no write access to system files by just opening them with Kate or Kwrite. So ok... i open a terminal, then SU to become root, and then "kwrite blacklist". But i get this: 

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0


So how can i do to edit the file and all the others that i will need to change ?

And can someone please answer this: Why it is being said everywhere that Linux is just easy as cake and user friendly when the reality is that a noob like me need to be asking for help in a forum to just be able to edit a text file?
Thanks

---

### Post by TidusBlade on 2007-10-27
On ubuntu I use "gksudo nautilus" to open the file manager running under root, you can try something like "gksudo Konqueror" or "gksudo Dolphin" or whatever file manager you use...

---

### Post by telovoyagarcar on 2007-10-27
Again... Im using Kubuntu. and why would i "sudo" if i am already root in the terminal.. ?

---

### Post by TidusBlade on 2007-10-27
Maybe it only works for me? I remember that I had problems editing files in /etc so opening my file manager using gksudo worked, even though I tried root from Terminal, thought you had the same problem as me.

---

### Post by FuturePilot on 2007-10-27
If you're using Kubuntu you should use kdesudo for running graphical apps as root. Just use a regular terminal. It's safer

---

### Post by telovoyagarcar on 2007-10-27
I found an option in dolphin to open folders and edit files as root. So problem solved.
But still... no one answers my question about user friendliness and why i get that error in the terminal when i want to open any program

---

### Post by telovoyagarcar on 2007-10-27
> **FuturePilot said:**
> If you're using Kubuntu you should use kdesudo for running graphical apps as root. Just use a regular terminal. It's safer


root@kubunt:/etc/modprobe.d# kdesudo kwrite
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesudo: cannot connect to X server :0.0


I get this error no matter what program i want to use..

---

### Post by TidusBlade on 2007-10-27
It's a piece of cake for me, because I can just go to the forums and ask for help, which I think is pretty easy to do. About the X server error, i think I recently saw a few threads about it around this forum, but I really dont know much baout it :(

---

### Post by FuturePilot on 2007-10-27
> **telovoyagarcar said:**
> root@kubunt:/etc/modprobe.d# kdesudo kwrite
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesudo: cannot connect to X server :0.0


I get this error no matter what program i want to use..

Don't use a root terminal. Try it from a regular terminal

---


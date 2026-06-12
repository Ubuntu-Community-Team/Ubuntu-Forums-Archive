---
title: "ubuntu starting on tty1, gnome seems to be gone"
date: 2014-07-03
forum: General Help
---

### Post by nat00 on 2014-07-03
First of all, I want to say that I have no idea of what caused the following bug. My computer was working properly under ubuntu and I did nothing I don't usually do on it. Anyway at some point my mouse stopped working properly. In some areas of the screen I cold click and in others I could not. I know this is not a hardware problem, because I tested my mouse on another computer and it works fine, and the trackpad did that too. Anyway I ran the following command in hope to fix it :

> metacity --replace

It did not do anything. I shut down my computer and restarted it in hope it would be fixed, but it did just the contrary. When the computer turned on, it was in the tty1 login screen. I used ctrl+alt+f7 and ctrl+alt+f8 to go back to my desktop, but it led to an empty, black screen, as if gnome was no longer working. I searched the internet  a bit and tried all of the following : 

> sudo service gdm start

it said "gdm : unrecognised service"

> sudo /usr/sbin/gdm

it said " usr/bin/gdm : command not found"

> startx

it printed down a bunch of text and in the end did nothing.

> sudo apt-get -f install gdm

It did a bunch of stuff and in the end it wasn't fixed but when I went to ctrl+alt+f7 there was "sd" instead of nothing on the screen.

I sort of understand what gnome is, but I have no idea how it works exactly, and I don't understand what is happening. I would like to hear any explanation/suggestion. thank you.

---

### Post by nat00 on 2014-07-03
I restarted my computer after doing all of the above and it worked great. I have no idea what fixed it but restarting it before did nothing. Anyway if you encounter this problem I think sudo apt-get install gdf does the trick.

---


---
title: "sun-java6-plugin not found using apt-get - simple but please help!"
date: 2008-04-24
forum: General Help
---

### Post by GrantsV on 2008-04-24
When I run:
sudo apt-get install sun-java6-plugin

It says "Not available but referred to by another package".  I have added the Multiverse repo and all the other in Synaptic.

What am I dont wrong!?

BTW, I am running 64-bit Ubuntu

---

### Post by justleen on 2008-04-24
did you run a ```
 sudo apt-get update 
``` after enabling the repros?

---

### Post by GrantsV on 2008-04-24
Thanks for your reply, yep!
It appears java-plugin is not available for 64-bit unless anyone knows more?

The icedtea plugin does not run my sons Runescape.

---

### Post by justleen on 2008-04-24
hmmm

installing the 32-bits version is a bit overkill for Runescape? :)

---

### Post by GrantsV on 2008-04-24
I dunno, its the only app he uses!

Maybe I could install sun-java6 for 64 bit manually or with a 32-bit wrapper?

---

### Post by twright on 2008-04-24
if you uninstall the iced tea plugin when you visit a site with java on it will allow you to automatically set up the 32 bit plugin with wrapper

---

### Post by Chibana on 2008-04-26
> **twright said:**
> if you uninstall the iced tea plugin when you visit a site with java on it will allow you to automatically set up the 32 bit plugin with wrapper

It does?  In what version of Firefox?  When I got to one of the java test sites without icedtea plugin installed, I get prompted to install GCJ plugin, or GCJ plugin based on OpenJDK, neither of which I can get to work.  Every java test site I got to just does nothing.  Sometimes I get "Loading applet" and nothing ever happens.

Are there instructions for manually installing the 32-bit plugin with wrapper to work in 64-bit Firefox?

---

### Post by petri on 2008-05-04
You could try Kilz script which installs 32-bits Firefox with Java (and flash if you want to) in 64-bits Ubuntu:

[http://sudan.ubuntuforums.com/showthread.php?t=202537](http://sudan.ubuntuforums.com/showthread.php?t=202537)

---

### Post by diodoros on 2008-05-04
I'm having the same experience as GrantsV and Chibana. I wonder what the story is with the 64-bit sun java plugin....

---


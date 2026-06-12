---
title: "Can server be installed on top of Desktop?"
date: 2008-05-07
forum: General Help
---

### Post by xwisdom on 2008-05-07
Hello,

I have XUbuntu desktop install but I would like to get the benefits of the server OS.

Can I install the ubuntu server on top of my xubuntu desktop? If so how?

---

### Post by tamoneya on 2008-05-07
yes it can be installed on top.  The real different between the two install CDs is that you wont get a GUI on the server CD since if you want to have a computer dedicated as a server you dont want to waste resources on a GUI.
I like the ubuntu guide as they have a section for several types of servers.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Servers](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Servers)

---

### Post by xwisdom on 2008-05-07
Thanks for the information but can't still get the benefits of the server OS but startup the GUI when I need it?

I'm not very good with terminal commands and I feel much better using the gui for some operations. I would like to be able to start the gui and stop it when I don't need it.

Can this be done?

---

### Post by FakeOutdoorsman on 2008-05-07
Seems to me that you want to run a desktop Ubuntu install with the ability to serve (I'm assuming here) web pages: [Apache, PHP, mySQL]("https://wiki.ubuntu.com/ApacheMySQLPHP") at Ubuntu Wiki.

Ubuntu Server has the same repository as standard desktop Ubuntu, but has some different packages installed by default including a different kernel.  If you need a GUI, then it is generally recommended to use standard Ubuntu and add apache, etc to that.  The server kernel isn't suited as well for a graphical system.

---

### Post by tamoneya on 2008-05-07
this is what you have with the desktop edition.  Just stay with what you have.  In the server edition you dont have any gui installed.  While you can install it afterwards it is rarely done since it is meant for dedicated servers which rarely have monitors attached anyways.  With the server loads(small) you are expecting though you should be fine with the desktop version.

---

### Post by zvacet on 2008-05-08
**Synaptic>edit tab>select packages by task>LAMP**

---


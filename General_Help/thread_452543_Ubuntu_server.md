---
title: "Ubuntu server?"
date: 2007-05-23
forum: General Help
---

### Post by Quickjelly on 2007-05-23
I've got a question(s) about using ubuntu on a remote server.

I'm planning on getting a dedicated server which I am going to install torrentflux on. As you may know torrentflux requires a LAMP set up.

When ordering the server, I'll have to specify which OS I want installed on it. They offer both the desktop version of ubuntu and the server version. The problem is I'm not sure which one to choose.

What I basically want to install on it is some ftp programs and torrentflux. I haven't been using ubuntu for more than a couple of months so I'm not all that comfortable with command lines and I would prefer to manage the server with some form of GUI.

If I choose to install the desktop version, would I be able to connect to it via ubuntu remote desktop and run an xserver on it? Would that be just like having a second desktop running under my home desktop? And if I choose to use the desktop version, how do I set it up so I can connect and manage it?

I presume that if I install the server version, I will have to do things with command lines and no GUI's, am I right? Is it even possible to install torrentflux on a server edition since torrentflux uses a GUI?

These questions might seem a little noobish, but I need to clear some of these things out since I don't want to waste money on a server which I might not be able to use. Thanks in advance :)

---

### Post by blazercist on 2007-05-23
Well if you want LAMP your best bet would be the server install, if you want a GUI you could install it over the server install via SSH, it IS a little command line work to install the GUI but nothing serious.  Look into installing GUI over the server install before you attempt it on a remote machine cuz it might cost u to get them to reinstall the OS.

---

### Post by bukwirm on 2007-05-23
You can install whatever you want on the server version, you will just need to start from the command line.
There are a variety of ways to connect to a server remotely - I prefer ssh, with X-forwarding enabled if I need graphical stuff.

---

### Post by TheodoreWard on 2007-05-23
> **Quickjelly said:**
> I've got a question(s) about using ubuntu on a remote server.

I'm planning on getting a dedicated server which I am going to install torrentflux on. As you may know torrentflux requires a LAMP set up.

When ordering the server, I'll have to specify which OS I want installed on it. They offer both the desktop version of ubuntu and the server version. The problem is I'm not sure which one to choose.

What I basically want to install on it is some ftp programs and torrentflux. I haven't been using ubuntu for more than a couple of months so I'm not all that comfortable with command lines and I would prefer to manage the server with some form of GUI.

If I choose to install the desktop version, would I be able to connect to it via ubuntu remote desktop and run an xserver on it? Would that be just like having a second desktop running under my home desktop? And if I choose to use the desktop version, how do I set it up so I can connect and manage it?

I presume that if I install the server version, I will have to do things with command lines and no GUI's, am I right? Is it even possible to install torrentflux on a server edition since torrentflux uses a GUI?

These questions might seem a little noobish, but I need to clear some of these things out since I don't want to waste money on a server which I might not be able to use. Thanks in advance :)

After you install the server version, you can install X and a window manager. For instance:
[FONT=Courier New]sudo apt-get install xubuntu-desktop[/FONT] 
will install xfce, 
[FONT=Courier New]
sudo apt-get install kubuntu-desktop[/FONT] 
will install kde, 
[FONT=Courier New]
sudo apt-get install ubuntu-desktop[/FONT] 
will install gnome.

---

### Post by Quickjelly on 2007-05-23
Ok, the server version sounds good then, I'll go with that. 

Thanks guys, really appreciate it. This forum is some serious kick ***. Even though I haven't been posting in this forum before you help me right away. Thanks. :)

---


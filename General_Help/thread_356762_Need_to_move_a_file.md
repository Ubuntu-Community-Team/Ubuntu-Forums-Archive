---
title: "Need to move a file"
date: 2007-02-08
forum: General Help
---

### Post by whayong on 2007-02-08
Hi!  Noob here.

I'm trying to move a file to /usr/lib/hotplug/firmware/

The file is /home/bastard/isl3890.

It needs to look like this in the end: /usr/lib/hotplug/firmware/isl3890.

How do I do that?  I can't seem to move it.  I always get some kind of error like "no such file or directory."

Another problem that I have is that the /hotplug/firmware/ part of the location doesn't exists.  I have to make it from scratch.  I just don't know if I make sense anymore, lol!

Thanks!

---

### Post by divague on 2007-02-08
just use ina terminal:

gksudo nautilus

and you can create the folders your need, and you can move the file

---

### Post by cleentrax on 2007-02-08
Just a slight correction...

In a terminal you should use "sudo nautilus."

In the "Run Application" Window (Alt+F2) you would use "gksudo nautilus."

If you do run Nautilus as root, be sure to close the window as soon as you're done so you don't mistake it for a normal user nautilus window.

---

### Post by Maestro23 on 2007-02-08
> **whayong said:**
> Hi!  Noob here.

I'm trying to move a file to /usr/lib/hotplug/firmware/

The file is /home/bastard/isl3890.

It needs to look like this in the end: /usr/lib/hotplug/firmware/isl3890.

How do I do that?  I can't seem to move it.  I always get some kind of error like "no such file or directory."

Another problem that I have is that the /hotplug/firmware/ part of the location doesn't exists.  I have to make it from scratch.  I just don't know if I make sense anymore, lol!

Thanks!

Command line:

Where you are trying to copy/move to is owned by root.  You will need to put "sudo" in front of your command.

Basically:
> 
#sudo cp isl3890 /usr/lib/hotplug/firmware = places a copy of the file there. 

#sudo mv isl3890 /usr/lib/hotplug/firmware = moves the file to the destination.  No copy is made.

Anytime you need to know the syntax of a command, you can type:
#man <command>

Will give you the syntax and arguments for the command.  Also there are many websites that discuss the terminal commands as well.

---

### Post by whayong on 2007-02-09
Excellent!   Thanks a lot fellas!

---


---
title: "'Save as' in Gedit..."
date: 2007-01-22
forum: General Help
---

### Post by speedwell68 on 2007-01-22
Hi,  I have started having problems saving files with the 'Save as' command in Gedit.  If I do this for example:  sudo gedit /etc/apt/sources.list and save the file using save as Gedit hangs.  I works fine  in gnome, I only have a problem in the terminal.  Any suggestions?

---

### Post by taurus on 2007-01-22
```
gksudo gedit /etc/apt/sources.list
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by speedwell68 on 2007-01-22
> **taurus said:**
> ```
gksudo gedit /etc/apt/sources.list
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I tried that and got this result...

[IMG]http://i80.photobucket.com/albums/j185/Speedwell68/Screenshot-johnjohn-laptop.png[/IMG]

---

### Post by speedwell68 on 2007-01-22
Also I get the same problem if I use Leafpad or Mousepad, it hangs when I select Save As.  So it suggests the problem is nothing to do with Gedit it's self.  Anymore suggestions as this is a strange one.

---

### Post by taurus on 2007-01-22
From a terminal, Applications -> Accessories -> Terminal, do

```
sudo nano -w /etc/apt/sources.list
```
When you are done with editing, hold down <Ctrl> while pressing x to exit.  It will ask you the name of the file you want to save it to (it shows the default name).  Now, type in the new name for it.

---

### Post by speedwell68 on 2007-01-22
Thanks a lot, love it.  I'd still like to know why the GUI editors have started hanging though.

---

### Post by taurus on 2007-01-22
I have seen that same error message a few times around here but not sure why.  In the meantime, just use that old fashion text based editor nano.  ;)

---

### Post by speedwell68 on 2007-01-22
> **taurus said:**
> I have seen that same error message a few times around here but not sure why.  In the meantime, just use that old fashion text based editor nano.  ;)

Yeah, I'm a relative noob, I didn't know about Nano, very much like Edit in MSDOS 6.  Edlin was the best though.:D

---


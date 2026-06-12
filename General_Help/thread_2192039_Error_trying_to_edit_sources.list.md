---
title: "Error trying to edit sources.list"
date: 2013-12-05
forum: General Help
---

### Post by keifus-rahn on 2013-12-05
can someone please help me ive been fighting this error for about a week now and can not figure it out ive uninstalled  and reinstalled and it just keeps coming back :/  I just dont know what to do ](*,)  Im a person that don't like to give up but i just dont know what else to do

*********************************************************************************************************************************************************************************************************
keith@keithrahn:~$ sudo gedit /ect/apt/sources.list
[sudo] password for keith: 

** (gedit:11303): WARNING **: Could not load Gedit repository: Typelib file for namespace 'GtkSource', version '3.0' not found

(gedit:11303): IBUS-WARNING **: The owner of /home/keith/.config/ibus/bus is not root!

(gedit:11303): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

correct line 57 and other offending lines if necessary

---

### Post by papibe on 2013-12-05
Moved to its own thread.

---

### Post by deadflowr on 2013-12-05
You should try running it with gksu, instead of sudo.
What are you trying to edit in the sources.list file?

---

### Post by keifus-rahn on 2013-12-05
Im getting a pop up- E:Malformed line 57 in source list  /etc/apt/sources.list (URI parse), E:The list of sources could not be  read., E:The package lists or status file could not be parsed or opened.  And also getting this Sorry Ubuntu 13.10 has experienced an internal error  /usr/bin/software-properties-gtk  Problem Type= Crash   Architecture= amd64    E:Malformed line 57 in source list  /etc/apt/sources.list (URI parse..       Here is the orig thread i started a couple days ago [http://ubuntuforums.org/showthread.php?t=2191333](http://ubuntuforums.org/showthread.php?t=2191333)

---

### Post by deadflowr on 2013-12-05
What's the output of
```
cat /etc/apt/sources.list
```

copy this and paste it into a terminal.

And if gedit is failing you, try
```
sudo nano /etc/apt/sources.list
```
to edit the file.
Use ctrl+x to save the file and exit.
Or ctrl + o to save.

Please, though, post the output of /etc/apt/sources.list.

---


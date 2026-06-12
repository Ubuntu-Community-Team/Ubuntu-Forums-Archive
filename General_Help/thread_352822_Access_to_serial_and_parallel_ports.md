---
title: "Access to serial and parallel ports"
date: 2007-02-03
forum: General Help
---

### Post by morganGDFP on 2007-02-03
Hello.
I have just migrated from Windows to ubuntu 6.10 and i am loving it.
There are however some problems..

I am trying to start programming some AVR microcontrollers using avr-gcc and some other programming tools like avrdude, uisp or something else.

One of my problem is that I need to get access to the parallel and serial port in order to communicate with my programmer.

I have found out following things about the parallel port:
For the  port the following three modules needs to be running:
parport_pc, ppdev and parport.
When i start up ubuntu parport and parport_pc are running but not ppdev.
I then have to start up ppdev by running 
sudo modprobe ppdev
Therafter I have to give access to the ppdev device by typing 
chmod 666 /dev/parport0

For the serial port it is something similiar, I think.
I haven't gotten around to trying that yet.

Can anyone please tell me how I can get access to the parallell port (and the serial port) with all those three modules running automatically when I boot my ubuntu.

Thankful for help
Morgan

---

### Post by WW on 2007-02-03
To load a module at boot, add it to /etc/modules.

---

### Post by morganGDFP on 2007-02-03
Hi sorry, I am really new in using linux...
There is no /etc/modules in my file system..
I have a /etc/modutils do you mean that one?
And if you do how do I add a module to it? 

And will that give me access to the parallel and seriel port?

cheers
Morgan

---

### Post by WW on 2007-02-04
The file is definitely /etc/modules, but I don't know why you don't have it.  I am running dapper (6.06), upgraded from breezy, and I have that file.  I also tried a 6.10 LiveCD, and it had /etc/modules (but with no modules listed in it, just comments).  I hope someone more knowledgable about modules and/or 6.10 can explain why you don't have the file.

You could creat the file and see if it works.  The file should be just a list of modules, one per line.  Lines beginning with # are ignored.

If /etc/modules works, you will still probably have to figure out how to  do the chmod somewhere, but I don't know the best way to make that permanent or automatic.

---

### Post by morganGDFP on 2007-02-04
Sorry again, my mistake..
I was looking for a modules folder...
I found the file and just added ppdev to it.

I also figured out how to get permissions to parport0
I went in (as root) and changed the permissions on /dev/parport0 to read and write and voila.

Beautiful, I will stick with ubuntu for a while longer.
Thank you.

---


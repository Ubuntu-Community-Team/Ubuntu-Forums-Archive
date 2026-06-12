---
title: "Out of Frequency Range Error"
date: 2007-01-02
forum: General Help
---

### Post by shansen77 on 2007-01-02
I'm trying to use the ubuntu 6.06 in Live CD mode and I get this error message:

Out of frequency range
H: 31-54 KHz
V: 50-120 Hz
Check PC Display Settings?

How do I correct this?

Thanks,
Stephanie

---

### Post by bodhi.zazen on 2007-01-02
> **shansen77 said:**
> I'm trying to use the ubuntu 6.06 in Live CD mode and I get this error message:

Out of frequency range
H: 31-54 KHz
V: 50-120 Hz
Check PC Display Settings?

How do I correct this?

Thanks,
Stephanie

If this does not fix your problem:

sudo dpkg-reconfigure -phigh xserver-xorg

Restart X: Ctrl-Alt-Backspace or```
sudo /etc/init.d/gdm restart
```

It would be helpful if you posted your video card and monitor.

---

### Post by moogii on 2007-01-02
i'm trying to load the live cd

but after booting my monitor goes off ...it says Out of frequency....imediately shut down


LG LCD monitor..flatron 563le

---

### Post by shansen77 on 2007-01-02
> **bodhi.zazen said:**
> If this does not fix your problem:

sudo dpkg-reconfigure -phigh xserver-xorg

Restart X: Ctrl-Alt-Backspace or```
sudo /etc/init.d/gdm restart
``` 


Forgive me for being a little slow but I'm not sure what I'm supposed to do with this information.  

After putting  the disk it in does some loading and then it goes to a black screen with this error message in the middle of the screen.  After a few seconds the monitor hibernates.  So, in order to fix the problem, what exactly would I need to do?



> **bodhi.zazen said:**
> It would be helpful if you posted your video card and monitor.

My monitor is a Compaq MV520 (circa 1999) and my video card is an ATI Radeon Xpress 200


Thanks,
Stephanie

---

### Post by bodhi.zazen on 2007-01-02
It appears as if ubuntu does not recognize your video card and/or monitor.

You should be able to get to a command line interface (CLI) with the combination of Crtl-alt- F1

You likely will need to install the ATI drivers, which can be difficult.

Here are directions:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

It will likely seem like Greek to you, and I hope this helps 8)

---

### Post by shansen77 on 2007-01-02
I read over this one:

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

and it talks about enabling repositories... is it possible to do that without having ubuntu installed?

---

### Post by bodhi.zazen on 2007-01-02
Yes, I'm sorry.

Here is how:

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then, in a terminal: ```
sudo aptitude update
```

---

### Post by anilbhx on 2008-03-11
> **bodhi.zazen said:**
> Yes, I'm sorry.

Here is how:

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then, in a terminal: ```
sudo aptitude update
```
I had installed 7.04 then Upgraded to 7.10. 
This problem was not there. My video card seems to be recognised properly as pro savage..
For certain reasons I had to do a reinstallation with a 7.10 live CD . Got the same error . Maybe this will help me too.

---


---
title: "Gui slows performance??"
date: 2007-02-01
forum: General Help
---

### Post by mymuscle on 2007-02-01
Ive been reading that a gui for ubuntu server will slow down performance.... is this really the case? If so then how much will it take away from performace? I don't see how it can take away enough resources to actually make a difference?? please give me some input, I have a web server that im setting up and I want to install a gui on it, but if its that much better without a gui then I will just learn to use the command prompt. My server is pretty powerful though.

Dell PowerEdge 1950 Server
Dual (2x) Dual Core Intel Xeon 5060 at 3.20GHz/2x2MB, 1066MHz
4 GB DDR2 SDRAM 667MHz (4 DIMMS)

---

### Post by JamieC on 2007-02-01
Using a graphical interface will inhibit performance since running the X server uses memory and processing power, resources that would otherwise be available for server software.

However, with a machine of that specification, using a graphical interface will probably have little or no noticeable effect.

---

### Post by mymuscle on 2007-02-01
Thank you Jamie!

---

### Post by bscbrit on 2007-02-01
Basically, a true server rarely has anyone logged into it as a normal user and so the provision of a GUI is simply wasted capacity - both in storage and processing power.  In your particular case, you will probably not see much difference but, whether you can measure it easily or not, it will be wasting capability.

BUT (and there is always a BUT)!

Installing the GUI will, in all probability, install more active services and any one of these could, potentially, provide another access point for an attack or inject of malicious software.  A server that is based on the CLI has only those items which are essential for its function installed.  It is then comparatively easy to provide the necessary security to protect it from outside threats.

Only you know the environment in which you wish to operate the server and therefore you are in the best position to make the judgement.  However, if you take the time and effort to learn the CLI, bash scripting or whatever shell you use, and perhaps perl, you will have learned something that will prove invaluable time and time again.  I think that everybody initially fights against learning the CLI and,  those that do succeed, find themselves using it more and more.  It is very rewarding to automate much of what you might do now manually.

---

### Post by JamieC on 2007-02-01
You're welcome. What I'd advise you to do is to set up and administrate your server using a graphical interface for a while, whilst learning the command line.

When you feel your command line knowledge is competent, you can then continue to perform administrative tasks using it (still within a graphical interface).

Then, when you get the gist of things and believe that you are capable of using just the command line, you can switch to it completely.

It may be worth mentioning that the Ubuntu server installation is not complete with a graphical interface and you will be required to download packages in order to install one.

---

### Post by mymuscle on 2007-02-01
Thank you 2!

Ok, where can I learn this CLI stuff? Is there a class I can take or is there a website that can walk me through it?

And can I install the GUI and then set up my server, then take the GUI off again?

---

### Post by bscbrit on 2007-02-01
1.  Two quick links:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

[http://www-128.ibm.com/developerworks/library/l-bash.html](http://www-128.ibm.com/developerworks/library/l-bash.html)

Try Googling/Yahooing for BASH howto.

There are numerous good books on the subject - I like Bash Scripting from O-Reilly.


2.

Yes, you can always remove the desktop GUI afterwards.

---

### Post by reclusivemonkey on 2007-02-01
> **mymuscle said:**
> Thank you 2!

Ok, where can I learn this CLI stuff? Is there a class I can take or is there a website that can walk me through it?

And can I install the GUI and then set up my server, then take the GUI off again?

You might want to take a look at webmin or one of the other remote server admin tools.

[http://www.webmin.com/](http://www.webmin.com/)

I think there even may be an Ubuntu one...

---

### Post by mymuscle on 2007-02-01
Ubuntu has a web based administration of its own??? Please tell me where I can get it.

---

### Post by mymuscle on 2007-02-04
BUMP... anyone know of the Ubuntu remote admin tool?

---

### Post by dcstar on 2007-02-04
> **mymuscle said:**
> BUMP... anyone know of the Ubuntu remote admin tool?

The easiest thing would be to install X on the server and then do a Remote Login to it from another Ubuntu machine.

If you want to use Webmin then you will have to install it yourself.

---

### Post by reclusivemonkey on 2007-02-05
> **mymuscle said:**
> Ubuntu has a web based administration of its own??? Please tell me where I can get it.

I think I must of dreamt it. I've googled around and I don't seem to be able to find it. Have you tried Webmin? This will accomplish pretty much everything you need.

---


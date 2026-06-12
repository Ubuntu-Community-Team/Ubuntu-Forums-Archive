---
title: "Help with Ubuntu Server"
date: 2007-04-03
forum: General Help
---

### Post by Scheater5 on 2007-04-03
I have installed the Ubuntu 6.10 Server with the LAMP option on a computer recently.  I need to sign into a network to access the internet.  Windows users do so through a program called Clean Access Agent, Mac and Linux users merely through a web-based authentication page.  But how would I sign into something like this on a base installation of Ubuntu?  I have access to other computers to the internet, so it's concievable I could download packages and then dpkg them onto the server, but I don't know what program could possibly allow me to do this.  Anyone have any ideas?

---

### Post by Scunizi on 2007-04-03
With the server install you are droped to a text prompt for logging in..  You can log in from there but the question is do you want to use a text based browser or something like firefox that is gui based?  If you want the gui based browser you'll need to install a graphical environment on the server.  To keep it light and fast, I use xubuntu which in essence is xfce.  sudo aptitude install xubuntu-desktop... or is it sudo aptitiude install desktop-ubuntu.  I always get the two mixed up.  That's my lixdexia showing :)

---

### Post by Scheater5 on 2007-04-03
That's just the problem - I can't access the internet at all without signing in.  Therefore, I can't apt-get.  I would prefer to not have a graphical environment - but I will freely admit that I have little experience with servers, so I don't entierly know what I want.

---

### Post by Scunizi on 2007-04-03
I'm not sure what you mean exactly by "signing in".  When you installed the server part of the process was to give a user name and password.  That should get you signed into the machine, not neccessarily apache or mysql. Once logged in you can apt-get or aptitude for anything else you need.  If you want to browse the internet from the command line elinks or lynx are two of your options.  lynx might already be installed.  If not both can be had from apt-get or aptitude.

---

### Post by Scheater5 on 2007-04-03
> I need to sign into a network to access the internet. Windows users do so through a program called Clean Access Agent, Mac and Linux users merely through a web-based authentication page.

I'm aware of the user system of Ubuntu, and that the server install has no gui.  I'm asking how am I supposed to sign into a network when I can't get to a web browser?

---


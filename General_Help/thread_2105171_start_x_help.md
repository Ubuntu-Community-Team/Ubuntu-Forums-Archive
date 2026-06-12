---
title: "start x help"
date: 2013-01-15
forum: General Help
---

### Post by caleb12134 on 2013-01-15
Im getting angry with this stupid thing. i type start x and it tells me to enter the sudo apt-get install xinit and it says unable to locate package E: 
 
PLEASE HELP. how do i fix it.:guitar:

---

### Post by Cheesemill on 2013-01-15
Have you got an internet connection on your machine yet?

As I have explained previously just installing xinit won't give you a desktop environment. There are tens (possibly hundreds) of packages needed to get a GUI.

There are  a few different options available to you, you can either get an internet connection and then use apt-get to install the DE (desktop environment) of your choice or you can just start fresh and install the desktop version of Ubuntu to begin with.

The best option however would be to not use a GUI at all and instead learn how to configure your server using the command line as this is how Ubuntu Server is designed to be used.

For anyone that's interested you should look at caleb12134's previous topics on this same issue.

[http://ubuntuforums.org/showthread.php?t=2102802](http://ubuntuforums.org/showthread.php?t=2102802)
[http://ubuntuforums.org/showthread.php?t=2104823](http://ubuntuforums.org/showthread.php?t=2104823)

---

### Post by asmoore82 on 2013-01-15
Start over using Ubuntu Desktop Edition. Technically, there is nothing the Server Edition can do that the Desktop Edition cannot; they are just different default starting configurations. Start with the Desktop Edition to learn the ways. It's also best on a production server to not have extra's (GUI, Office, Games) installed but for a Home, or Home Office or Personal Server it'll be fine.

---

### Post by caleb12134 on 2013-01-15
ok i am gonna install ubuntu desktop. what do i need to do after that to make it run like server so i may host websites and php files and crap along with email

---

### Post by Wim Sturkenboom on 2013-01-16
The command is _startx_, not _start x_ ;) Question is why you need it on a server?

> 
ok i am gonna install ubuntu desktop. what do i need to do after that to make it run like server so i may host websites and php files and crap along with email

To get the LAMP part going
```

sudo apt-get install lamp-server^

```
I haven't used mail servers so can't help with that part.

To make the system boot into text mode (if needed), you need to edit the grub configuration.

Edit _/etc/default/grub_ (with root privileges), find the line containing _quiet splash_ and replace _quiet splash_ by _text_. Next run _sudo update-grub_

---

### Post by caleb12134 on 2013-01-16
so what do i need to install once i install ubuntu desktop to make it run like a server.

---

### Post by haqking on 2013-01-16
> **caleb12134 said:**
> so what do i need to install once i install ubuntu desktop to make it run like a server.

a server is any machine providing a service.

Whatever services you need you install then it is a server.

Be it file, print, web, application etc

---

### Post by caleb12134 on 2013-01-16
SO we got start x installed and now it just shows a white square.

---

### Post by caleb12134 on 2013-01-16
Hello. i got startx up but when i type and enter startx in the top left  corner appears a white box and i cant type. how do i get to the actual  desktop on the server.

---

### Post by ljmhk on 2013-01-16
> **haqking said:**
> a server is any machine providing a service.

Whatever services you need you install then it is a server.

Be it file, print, web, application etc

haqking has the answer for you, rather than work a desktop environment into a server build of Ubuntu, it would be far easier for you to perform a desktop installation and then install the services you need from there. 

The only sticking point here is that should you have specific services you DONT want enabled on the server the desktop installation may well come with some additional bloat you dont need (bear in mind however most of that bloat is X!)

What is the primary function of the server exactly? A LAMP configuration perhaps or a file / print server?

---

### Post by caleb12134 on 2013-01-16
can someone just tell me what the issue is with the square

---

### Post by steeldriver on 2013-01-16
Installing xinit / startx and a minimal X server is nothing like a full integrated desktop - in particular, unless you also install and configure a window manager, or write a custom .xsession or .xinitrc to tell it what to do next, all you will get is an empty session

[http://www.tldp.org/HOWTO/XWindow-User-HOWTO/runningx.html](http://www.tldp.org/HOWTO/XWindow-User-HOWTO/runningx.html)

The simplest 'useful' .xsession would probably consist of just a single xterm on a gray background, that's a good next step if you insist on doing things this way

---

### Post by kerryhall on 2013-01-16
If you install just x.org by itself, you will end up with something *very* minimal.

If I were you I would try installing fluxbox, fluxbox is a nice lightweight window manager.

[http://fluxbox.org/screenshots/](http://fluxbox.org/screenshots/)

if "sudo apt-get install fluxbox" and then restarting x doesn't work, there is probably a config somewhere where you will need to tell x to use fluxbox as your window manager.

[http://en.wikipedia.org/wiki/X_window_manager](http://en.wikipedia.org/wiki/X_window_manager)

---

### Post by kerryhall on 2013-01-16
Yeah here we go:

[http://www.tuxfiles.org/linuxhelp/changeman.html](http://www.tuxfiles.org/linuxhelp/changeman.html)

That tells you how to set your window manager if you are starting x manually.

BTW I know this can be frustrating, but stick with it :)

---

### Post by caleb12134 on 2013-01-16
i might as well get windows server :P

---

### Post by haqking on 2013-01-17
> **caleb12134 said:**
> i might as well get windows server :P

here you go [https://www.microsoft.com/en-us/server-cloud/windows-server/buy.aspx](https://www.microsoft.com/en-us/server-cloud/windows-server/buy.aspx)

have fun

---

### Post by caleb12134 on 2013-01-17
So startx. i just got i working. I see a black background and the ubuntu symbol in white. What can i do to make it more like a desktop. new packages for like adding users and stuff?

---

### Post by Zill on 2013-01-17
caleb12134:  All the answers you need are in this thread.  **Please read it from the start!**

---


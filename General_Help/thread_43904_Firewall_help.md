---
title: "Firewall help"
date: 2005-06-23
forum: General Help
---

### Post by arunsub on 2005-06-23
Does anyone know any Firewall that functions like Zone Alarm or Norton Firewall for Windows?  I'm using Firestarter, but I want a user friendly firewall where I can configure which programs to access internet and which one shouldn't. Any help would be appreciated.

Thanks.

---

### Post by jcs296 on 2005-06-25
You may want to check out guarddog (for kde), which gives a bit more control of setting up access for specific applications.  However you really don't need that level of control; the important part is blocking incoming connections which is easily done through firestarter.  Outgoing connections are a problem on windows since you'd like to keep any worms/spyware from connecting outward (or unnecessary parts of installers) but the same situation doesn't apply in linux.  Hope this helps.

---

### Post by wadesmart on 2005-06-25
06252005 0931 GMT-5

I too am very new to linux but I installed Firestarter and have been monitoring the usage and it works fine. 

You have to remember that for starters, linux is inherently more secure than windows.  So much of what you HAVE to have on widows you do not need here. 

Wade

---

### Post by cutOff on 2005-06-25
[QUOTE=arunsub]Does anyone know any Firewall that functions like Zone Alarm or Norton Firewall for Windows?  I'm using Firestarter, but I want a user friendly firewall where I can configure which programs to access internet and which one shouldn't. Any help would be appreciated.

Thanks.[/QUOTE]
Firestarter is able to create rules according to your needs.

Take a look to

[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

---

### Post by arunsub on 2005-06-25
I agree with you both. It's much safer than Windows, but If I can control individual program, I'll have more control on what is accessing my internet connection. What if i install some program for non-internet related use, but that uses  internet connection to send information about my activity? How do I control that? It's possible to do that in Linux.

---

### Post by arunsub on 2005-06-25
[QUOTE=cutOff]Firestarter is able to create rules according to your needs.

Take a look to

[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)[/QUOTE]

I'll have to try this and see how it works.

---

### Post by jfdill_2 on 2005-06-29
Having finally got around to tweaking iptables today, this is what I found:

[firehol](http://firehol.sourceforge.net/) was extremely easy to configure, and that worked the best for some servers where I could not rely on easy access to a GUI interface.

[fireflier](http://fireflier.sourceforge.net/) is the most similar to Norton or Zone Alarm, it runs as a daemon and lets you create "rules" based on program executables as well as ports.  However, it seems to have some stupid defaults, like all internal loopback traffic is blocked, which means GNOME or KDE won't work--Better make sure that you have all of the necessary holes opened BEFORE you reboot or exit your desktop!  I had it mostly working, but could not get a desktop after I rebooted because apparently certain IPC services from loopback to loopback were still blocked.    So, I had to login to the text console and shut it down.  I'll probably give it another shot, but found that annoying.

---

### Post by arunsub on 2005-06-29
Thanks. That's quite helpful. I'll take a look.

---

### Post by wadesmart on 2005-06-30
06302005 1203 GMT-5

Are either of those really a good idea for beginners? The fireflier doesnt seem to be as, if you got yourself locked out, I would be totally screwed not knowing exactly what I need to let through. The other one, firehol, I found bits and pieces of information, mainly from debain, but I didnt feel I was totally ok with that one either. 

Im still using firestarter and to be really honest, I cant tell if its doing anything or not. With ZoneAlarm I was sure what was needing access out and what was being blocked coming in. With this, Im uncertain. I can see right now for example, that in the Active Connections box there are two connections: one is the local loopback titled Ipp under service, and the other is HTTP service. A second HTTP service with program firefox-bin shoes up when the page refreshes. 

Wade

---

### Post by jcs296 on 2005-07-01
Firestarter does work, even though it may not appear to be doing anything.  You can see that it does indeed start at boot: once the gnome login screen appears, press Control+Alt+F1, which brings you back to the console startup messages are sent to. you should be able to see a line about firestarter starting up. To return to the login screen press Control+Alt+F7.  

As for really verifying that the firewall blocks incoming requests; try installing nmap or nmapfe from apt-get/synaptic (the latter has a graphical frontend).  This is a program to do port scans, allowing you to test the firewall.  Put in your IP address (not 127.0.0.1, use your actual IP which you can find at a terminal with 'ifconfig'), and set it to scan all ports. With firestarter running (keep in mind you don't have to have the GUI open for it to be running) you'll see all ports closed.  Try putting in 127.0.0.1, and you'll see some entries pop up since it's now hitting the loopback device; that's ok since it's internal only.  If the results show up as all ports closed on the external IP, then you're fine and can relax about whether the firewall is working or not.

Sorry about the length of this post, but I hope it helps.

---


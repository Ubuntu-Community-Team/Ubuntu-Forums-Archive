---
title: "KDM won't start automatically"
date: 2007-10-22
forum: General Help
---

### Post by cdiem on 2007-10-22
Hi there! I upgraded from Ubuntu 7.04 to Ubuntu 7.10, then did "sudo apt-get install kubuntu-desktop", then removed through synaptic almost everything of Gnome (libs, etc.); GDM inclusive. I'm running almost purely KDE now.
However, KDM won't start at startup. I have to write "sudo /etc/init.d/kdm start" to log in my system; starting it with "startx" does not show some options for my lappy (like hibernate, etc) and I don't want to use them through command line. 
In "/etc/X11/default-desktop-manager" the path is set to "/usr/bin/kdm". 
I guess I have to add the kdm's daemon to the list of other daemons, that start with the startup of the system; however, I can't seem to find their location. Could someone please help me? 

P.S. : "sudo dpkg-reconfigure kdm" did not solve the problem.
P.P.S.: Would the somehow adding of kdm to /etc/rc.local start it automatically?

---

### Post by prince_niceguy on 2007-10-22
install sysv-rc-conf using synaptic.

now run it as root and ensure kdm is selected for 2,3,4 and 5.

---

### Post by Orbitize on 2008-02-20
Hello! 

I am rather new to (K)Ubuntu and Linux generally, and I also have a similar problem. When I start my computer, I do not get a GUI, just a prompt requesting me to log in. After I enter username and password, I have to run 'sudo kdm' to get to the normal log-in screen.

I have tried "sudo dpkg-reconfigure kdm", and the sysv-rc-conf trick mentioned above, but still no luck.

Any help would be greatly apreciated!

-O

---

### Post by stooshbunutu on 2008-02-20
Just found a soultion to getting programs to start auto.

System >>> preferences >>> Sessions

Then click on ADD and enter the command you would runt in terminal. This should work :)

---

### Post by prince_niceguy on 2008-02-20
> **stooshbunutu said:**
> Just found a soultion to getting programs to start auto.

System >>> preferences >>> Sessions

Then click on ADD and enter the command you would runt in terminal. This should work :)


you should not be starting kdm like this. kdm is desktop manager and it should be started before the desktop environment can start. i.e. gnome or kde can start.

the best way to start is through the services like i have mentioned above.

---

### Post by Orbitize on 2008-02-21
Thank you for the replies! However, I do not believe the idea stooshbuntu mentioned will help me, as technically my session has not started when I log in.

Again, thanks,

-O

---


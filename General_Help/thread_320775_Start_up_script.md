---
title: "Start up script"
date: 2006-12-17
forum: General Help
---

### Post by rado_london on 2006-12-17
Hello
I want to put the following line into the startup script so it loads on boot:
```
/opt/lampp/lampp start
```
How do I do that?

Cheers

---

### Post by dbbolton on 2006-12-17
can you add it under system>prefs>session>startup ?

---

### Post by dbbolton on 2006-12-17
maybe try it gentoo style:

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=4)

---

### Post by rado_london on 2006-12-18
> **dbbolton said:**
> can you add it under system>prefs>session>startup ?

It doesnt work cause it requieres password so I want to put it in the init script. I didnt find my way in the gentoo documentation. Anyone help me please!

---

### Post by ciscosurfer on 2006-12-18
> **rado_london said:**
> It doesnt work cause it requieres password so I want to put it in the init script. I didnt find my way in the gentoo documentation. Anyone help me please!You can creating a script and then place the location of that script into your Sessions | Startup Tab as follows...create a the scrip with whatever filename you'd like, for example:```
sudo gedit lampp-startup.sh
```Now add the following the the script:```
#!/bin/bash
#startup script for the lampp suite

#sleep the script allowing other startup apps/scripts to load first
#the sleep number is in seconds 
sleep 10

#call gksudo to allow user the be prompted to enter password
#once the following line is read, it will prompt you for your password
#enter in your password, and lampp should startup
exec gksudo /opt/lampp/lampp start
```Save and exit the file.  Now you need to make it executable, in a terminal, wherever you've saved the file, enter in```
sudo chmod +x lampp-startup.sh
```Let's say that the file is located in your Home directory, you'll now go back to Sessions | Startup Tab and click Add and enter in the following: /home/<yourUserName>/lampp-startup.sh

You can also create a laucher that you click on after your logged in.  To do this, right-click the Desktop and click Create Launcher.  Enter in your details, and for the command, enter in sudo /opt/lampp/lampp start and choose the box that says Run from Terminal.

The first option that I gave you may not work because gksudo works on GUI apps...you may try substituting gksu or simply sudo and then adding a line for the app to sleep to give you enough time to enter in your password at startup.

The Xampp suite actually has a GUI to do all fo this: start, stop, restart...don't know is lampp suite does or not.

Hope this helps a little, or at least gets you started. :D

---

### Post by tari on 2006-12-18
Try adding a script to run that to /etc/init.d for example:
/etc/init.d/lampp
```

#!/bin/sh
/opt/lampp/lampp $1

```
or even just make /etc/init.d/lampp a symlink to /opt/lampp/lampp
Now run
```

sudo update-rc.d lampp

```
and it'll start lampp on system boot as root user, although I'm not entirely sure the update-rc.d is required, not sure if I ever had to do that when adding things to /etc/init.d..

---


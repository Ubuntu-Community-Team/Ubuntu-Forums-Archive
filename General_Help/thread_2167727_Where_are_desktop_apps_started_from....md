---
title: "Where are desktop apps started from..."
date: 2013-08-14
forum: General Help
---

### Post by mtmigs on 2013-08-14
I recently had to recreate a user on Ubuntu 10.03 and now the applets are gone. That includes the network manager applet. Where can find the file(s) that contain the startup applets?

---

### Post by agillator on 2013-08-14
First, are you talking about Ubuntu 10.04? There was no 10.03 that I know of. And if you are really running a 10 point something, I would urge you to update to something newer. I believe 12.04 was a long term support (LTS) version. Then, as far as the applets are concerned I assume you are talking about the launchers on the panel. Most of those are installed by right clicking on the panel itself, then opening the 'panel' menu and clicking on 'Add new items'. That brings up a dialog with many of the items on it. If what you are looking for is not there, click on 'Launcher' and then the "Add" button. A generic symbol will appear at the end of the panel. Right click it, click properties and then the '+' button. Enter the command to start the program, close all, move the symbol to where you want it. 

As far as where a program or applet is, there are several possibilities. First see if there is a man page for the program ( man <program name>). Then tru whereis or locate. If that doesn't turn up anything try the more general 'find / -name "<part of the name with any wildcards to identify the file>"'. To get specifics on running these, check their man pages, e.g. man whereis. You can also check a few directories directly: /bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin, usr/share, etc. 

I hope I understood your question and that this helps.

---

### Post by mtmigs on 2013-08-14
You are correct it is 10.04 not 3. I have upgraded one computer to 12.04 and I hate the unity interface (use of lower case is intentional). There was a reason I started using Ubuntu. I hated windows because they kept putting more and more layers of nonsense hiding where everything really was located. That is what unity does. I hate looking through hundreds of applications for the one not on the side bar. If I wanted that type of side bar I would buy a Mac. The one computer I upgraded to 12.04 I then eventually converted to gnome. But it still is not as easy to use as 10.04's pull down menus.

Sorry but you did not understand my question either. I know where to find the applications. What I wanted to know is where in the .??* control user control files can I locate what applets should be loaded after I login to Ubuntu. There are lots of configuration directories such as ".gconf" ".local" ".nautilus" ... Where can I find the one that contains the parameters to load applets?

---

### Post by Bucky Ball on 2013-08-15
*Thread moved to **General Help**.*

Issues possibly due to the fact you are running an unsupported release. It is also a security risk if it is online. Upgrade to the latests LTS if you want a longer support release (five years now), Ubuntu 12.04 LTS.

---

### Post by agillator on 2013-08-18
If you don't like Unity, and many including me do not, there are many other options. Personally I like and use xubntu - ubuntu with xfce instead of unity. There are others - lubuntu, kubuntu, edubuntu, . . . . You might also look at Solydx and Solydk. So don't get hung up on Unity. There are too many other options to waste the time on that.

As to your original question, I guess someone else will have to help you since I don't use Unity and you are apparently talking about something specific to Unity. Really, look at the other options. There are enough I suspect you will find one you like.

---


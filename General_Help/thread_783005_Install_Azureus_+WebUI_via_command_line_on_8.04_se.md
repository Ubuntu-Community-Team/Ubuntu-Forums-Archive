---
title: "Install Azureus +WebUI via command line on 8.04 server"
date: 2008-05-05
forum: General Help
---

### Post by antifaithstl on 2008-05-05
I've searched the forums w/o finding anything related to my issue.  I have server 8.04 installed w/ all updates.
I'd like to install & run Azureus and the WebUI via the command line.  I know I can install Azureus using:
> sudo apt-get install azureus
but I need to know how to run it via the command line & install the WebUI.
Thanks alot.

---

### Post by Rhuidean on 2008-05-07
This is quite simple.
1. install azureus
sudo apt-get install azureus

2. start azureus
applications -> Internet -> Azureus

3. complete setup wizard. the answer are dependant on your personal setup. 

4. from inside azureus - plugins -> Installation Wizard

5. use "by list from sourceforge.net"

6. find "Html Web UI" or something like that. i have it installed already so i cant see the actual listing. complete the install by clicking finish.

7. Restart Azureus.

8. Tools -> Options. Under Plugins -> HTML Web UI. You will need to configure a port for the website to use. As well as to open this port in your firewall if you wish to access the web UI from outside. You can reed the FAQ on azureus's website on how to do this.

The Monk

---

### Post by djdan00 on 2008-05-11
Thats how to install it in the GUI
Im after the same, would like to install it on ubuntu server so via command line with a web gui.

---

### Post by flaggh on 2008-05-11
All you need to do is copy the plugin to the plugins folder.  Probably something like .Azureus/plugins/webui would be the appropriate place.  You can start the Azureus daemon from the command line by typing
```
java -jar Azureus2-XXX.jar --ui=console
```
All this information can be found on the Azureus Wiki
[http://azureuswiki.com/index.php/Console_UI]("http://azureuswiki.com/index.php/Console_UI")

---

### Post by antifaithstl on 2008-05-13
Cool.  Thanks for the answers.  However, I've given up on using server edition.  It's only my home NAS so I'll just use the GUI.
Thanks again!

---


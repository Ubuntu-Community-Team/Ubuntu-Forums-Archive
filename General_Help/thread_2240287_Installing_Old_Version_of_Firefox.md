---
title: "Installing Old Version of Firefox"
date: 2014-08-19
forum: General Help
---

### Post by Quarkrad on 2014-08-19
Just completed _clean_ install of 14.04 from 12.10 - all has gone well apart from firefox.  Once new OS installed, like many times before, I copied **extentions** and **firefox** from my backup disc to ~/.mozilla - but firefox will not run, it freezes at the opening page with the text transferring data from [www.google.co.uk](www.google.co.uk).... at the bottom of the page.  My first thoughts were that my backup was from a different version of firefox (I cannot remember what version I was running under 12.10) so I completely removed firefox and installed firefox 28 using the commands:

tar xvf ~/Downloads/firefox-28.0.tar.bz2
sudo mv firefox/ /opt/firefox28
sudo ln -s /opt/firefox28/firefox /usr/bin/firefox

or varients of from various web pages.  I do get the symbolic link in usr/bin but either as a user or sudo I cannot get firefox to launch.  One thing, I have read that x64 version of firefox is a 'pain' to install manually so I downloaded the 32bit version to install on my 64bit  machine - I do not believe this should be a problem.  My wife has an extensive list of bookmarks so I'm under presure to at least get firefox working. Any help appreciated.

---

### Post by claracc on 2014-08-19
I suggest to remove the firefox 28 you have installed and install by software center or synaptic firefox 31 (the one in the repositories for your 14.04 ubuntu, if your system is 64 bits, 64 bits one). 

Then copy your add-ons and bookmarks, then disable all the add-ons and try to launch firefox,  go enabling the add-ons one by one till find the responsible for the malfunction, remove it.

It is a security risk to launch firefox as root.

---

### Post by Quarkrad on 2014-08-19
Afraid I cheated by reinstalling the whole thing - was under pressure to get pc up and running.

---


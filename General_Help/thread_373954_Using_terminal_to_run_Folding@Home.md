---
title: "Using terminal to run Folding@Home?"
date: 2007-03-01
forum: General Help
---

### Post by NeilBlanchard on 2007-03-01
Greetings,

I am trying to run Folding@Home, and it needs to run in a terminal.  How do I open a particular folder in the terminal, or how do I navigate to the folder after it is started?

On other distros, there was an option in the File Browser to Open in Terminal, but if it is there in Ubuntu, I missed it.

TIA

Neil

---

### Post by AlcoJaguar on 2007-03-01
If I understand your question correctly this link should help you.
[http://www.reallylinux.com/docs/basic.shtml]("http://www.reallylinux.com/docs/basic.shtml")

---

### Post by NeilBlanchard on 2007-03-01
Hello,

I figured it out -- I was not getting the path correct.  cd /home/neil/F@H 

Also, I had to install some 32bit libraries in order to run Folding@Home -- the client is 32bit, but the core (that does the Folding) is 64bit.

[Folding@Home 64bit Linux Forum]("http://forum.folding-community.org/ftopic17223.html")

After that, the standard 'chmod +x fah5' and then './fah5' get the client running!

Now, if only the Stanford servers would let it download the FahCore_a1.exe....

---


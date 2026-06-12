---
title: "update killed xorg and need help with envy to get drivers"
date: 2007-02-10
forum: General Help
---

### Post by searayman on 2007-02-10
i did an update and it killed my xorg and i need to get my nvidia drivers workign again! can somone write me a tutorial on how to use envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

i need to download it, install it nad run it all from terminal, and i am no tth ebest atterminal so need soem help. ALso if you could host the envy file yourself and shorten the website adress i have to type, i would aprecaite it a lot because i am on two different computers and can not copy and paste.

---

### Post by syxbit on 2007-02-10
there are instructions on the site.
but this is all you do
get the envy.deb file
run it in GUI by double click it (I changed my video driver to "nv" to get DL and run this
basically you edit your xorg.conf by typing this in the terminal
nano /etc/X11/xorg.conf
then change the bit "nvidia" to "nv"
then type
startx
you should be in.
after you run envy.deb, click CTRL-ALT-F1
type "nano /etc/X11/xorg.conf" and change back to "nvidia"
then type "envy" and choose install nvidia

If getting  gui doesn't work for you, you can install elinks, or links2 to browse from the terminal

---

### Post by Repent on 2007-02-10
Go here follow the instructions, it's easy and fast. 

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by Repent on 2007-02-10
lol....It worked so well I Bookmarked the page. :guitar:

[http://www.ubuntuforums.org/showthread.php?t=358107&highlight=nVIDIA+drivers](http://www.ubuntuforums.org/showthread.php?t=358107&highlight=nVIDIA+drivers)

---


---
title: "trying to install skypeforlinux-64.deb"
date: 2017-10-12
forum: General Help
---

### Post by seekertom on 2017-10-12
I dl skypeforlinux-64.deb into my /home/tom/Downloads folder. from ms site, beta?
I opened a terminal.
sudo apt -get update
sudo apt -get upgrade
   because attempt to do skype said dependancies probs, stuff needed but not here...

sudo dpkg -i skypeforlinux-64.deb
   lots of things happened, more than before I did update/upgrade.
   seemed to terminate without error.

now, where do I go to get it and use it?
I connected my camera, went to ubuntu software, located cheese app, launched and cam works ok.
Looked in ubuntu software, searched, no skype.

so, if I did the sudo stuff correctly, where is the skypeforlinux-64 app located, and how to I launch it?
or.... if I didn't actually install it, what did I do wrong, what do I do to make it right...?
thanks, st
(instructions I got from askubuntu....)

:confused:

Got it, thanks. used gdebi, it did its magic, but had to reboot pc to see skype in installed software.

called my own cell, worked both directions. But a call to Scotland and she could see me but not hear. On my side, see and hear both ok.
Unsure if I did everything right, was a quickie call, so no time to dig deeper. Will try it long distance another time. But for now, I'd say it's working.

Thanks for the help, folks!!!

---

### Post by deadflowr on 2017-10-12
What version of Ubuntu?
And what was the dpkg output?

---

### Post by ajgreeny on 2017-10-12
Install **gdebi** first then simply right click on the downloaded skype .deb file and choose to open it with gdebi; that will sort out all the dependencies needed and install them and you should then be able to find skype in the dash or menu if using a DE with menu system.

---


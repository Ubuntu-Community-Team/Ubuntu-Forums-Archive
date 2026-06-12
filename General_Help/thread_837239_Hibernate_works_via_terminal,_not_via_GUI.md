---
title: "Hibernate works via terminal, not via GUI"
date: 2008-06-22
forum: General Help
---

### Post by barkerben on 2008-06-22
Hi - 
Firstly apologies for 3 questions in one post, but I think they are all related, so here goes:

I am having some issues with hibernation on my Ubuntu Hardy PC:

If I run the ./hibernate.sh script (via sudo) directly, it works fine. However, if I try to run it by clicking on the GUI (Gnome) shutdown->Hibernate buttons, I get a flashing cursor in the top left of the screen and nothing else. Is the fact that I have to use sudo via the terminal to get this to work significant?

I have a CF card plugged into my card reader, and I have also noticed that while the hibernate resume succeeds, for some reason the card is also read and my default image viewer software loads. This does not happen when starting up from shutdown state

Finally, I have a tiny script that runs at startup that enables wake on Lan.This means that when I shutdown the PC I can wake it remotely...but It seems that when hibernating, the network card is powered down, so is unable to detect the Magic Packets for resumption... Any thoughts?
Cheers,

Ben

---

### Post by heronr1 on 2012-11-22
Hi,

I just found this topic, and hopefully my answer ist stisfying. ^^

When using icons from the menu usually small scripts are run before, which may f.e. recognize if hibernation is activated or something else.

Since Ubuntu 10.04 (?, not sure about) hibernation is deactivated from the start.

U can enable it via: [http://askubuntu.com/questions/147877/laptop-locks-screen-instead-of-hibernates](http://askubuntu.com/questions/147877/laptop-locks-screen-instead-of-hibernates)

Which is the hibernation command U R running? 
maybe, when clicking on the icon, the running script isn't reached?

---

### Post by wildmanne39 on 2012-11-22
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---


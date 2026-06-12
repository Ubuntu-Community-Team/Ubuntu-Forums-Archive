---
title: "print cartridge indicator"
date: 2015-02-22
forum: General Help
---

### Post by jackobi on 2015-02-22
Hello Everyone
Can anyone give me advice. I have an Epson D92 printer which uses four separate ink cartridges. when my wife uses it on her Windows machine there is an ink cartridge level indicator which warns you that a cartridge is empty. When I use it on my linux Machine ( Xubuntu 14.04 ) the printer works fine but when a cartridge runs empty the printer just stops and I have no idea which one to change and I end up changing all four which is a waste. 
Does anyone know of a program for Xubuntu which will give a ink level indication.
Many thanks in advance for any help given.

---

### Post by ajgreeny on 2015-02-22
I suggest you have a look at mtink.

It may take a while to get it running as it requires you to be a member of one group (can't remember which) that you will not be in by default, and I don't think the installer adds you, so keep a close watch when you install it, and it should eventually work for you.

When I had Epson printers it was the only way I found to show the ink levels graphically, though I think it could be done in command line with escputil.

---

### Post by Mark Phelps on 2015-02-22
Open up a terminal and type this:
> sudo adduser $USER lp

Where $USER = your username

---

### Post by jackobi on 2015-02-23
Hello Guys and sorry for the late reply.
Mark 
I have installed Mtink from symaptic and also ran the command as you said but my printer is not on the list of printers so I selected "other printer" but all i get is an error message suggesting that the printer is not switched on or it is out of paper but I am using the printer just now so that is not the case.








[IMG]http://i.imgur.com/FXzvoLg.png[/IMG]

---


---
title: "clamav"
date: 2007-04-03
forum: General Help
---

### Post by garymc1 on 2007-04-03
hi I have installed clamav by going in to the terminal and using the command
apt-get install clamav
it said that it is installed but i cant find the program listed in the applications menu so i can run it ???

---

### Post by dannyboy79 on 2007-04-03
here is something even better. this will add clamav to the right click menu within nautilus. ([http://doc.gwos.org/index.php/ClamAV_Nautilus](http://doc.gwos.org/index.php/ClamAV_Nautilus))

 if you use kubuntu or don't want to do that, then simply add a menu item using alacarte menu editor ([http://www.linux.com/article.pl?sid=06/09/12/1933236)](http://www.linux.com/article.pl?sid=06/09/12/1933236)). the command you will want to add when editing the menu and adding an item will be gksudo clamav.


you could always forget about the menu and simply run it from the command line using the same thing. gksudo clamav

---

### Post by Sammi on 2007-04-03
I found mine in Applications -> System Tools -> AntiVirus in the top panel.

I need to do this command to launch it manually:
gksu clamtk

---


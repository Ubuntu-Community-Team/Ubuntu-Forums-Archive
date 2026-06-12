---
title: "ubuntu 12.04 can't do nothing...."
date: 2013-02-03
forum: General Help
---

### Post by Mascarade on 2013-02-03
Hi eceryone!

I install ubuntu 12.04 yesterday and it was a succefull installation...
I made all the update....

i kill the unity process by following this guide 

[http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html](http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html)

and everything was fine! After that i install some program, everything fine..!!...

Now i was just rebooting and after this reboot everything going wrong!!

Like if a got a web browser open (or whatever the windows that is open) if i want to minimise it, the window stay there on the maximise form and the minimise form..??
If a go to place and select the folder home (or anyone) the desktop screen (it black) twitch on the color of the bran new desktop color after an installation...??..and nothing open.....
when i click somewhere i see what i want but i can't do nothing and it stay open...
and i can't make a right click on the desktop nothing happen....

i just don't know why this big bug happen??.......

if someone want to help me :)

Thanks
Louis

---

### Post by ajgreeny on 2013-02-03
I don't know for sure, but it sounds as if the removal of unity and then running deborphan has removed other required packages from your system.

There is really little if any need to remove unity just to be able to run another desktop, and it may be that it is less dangerous to leave it well alone.  Therefore I recommend that you run ```
sudo apt-get install --reinstall ubuntu-desktop
``` to make sure you get back everything that is needed.

Then you can get whatever DE you want to use instead of unity;
gnome-shell, xfce or xubuntu-desktop, kde or kubuntu-desktop, lxde or lubuntu-desktop, or even classic-gnome, (just like the gnome 2 of previous ubuntu versions, see [PreciseGnomeClassicTweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")).  The last of those would be my preference if I stayed with gnome, but I think xubuntu is probably going to be my port of safety when 10.04 Lucid loses support in April.

---

### Post by mjitkop on 2013-02-03
It's a very good thing that Ubuntu 12.04 can't do nothing. This means that it can do things! You used a double negation with "can't" and "nothing" but I think you meant "can't do anything" or "can do nothing." ;)

I'm teasing. :biggrin:

I hope that ajgreeny's reply will help you. :popcorn:

---

### Post by Mascarade on 2013-02-05
Thanks for the advise :)

But i was doing a stupid mistake in my setting...:D
In the gnome advance setting i was disabling the " Have file manager handle the desktop" to no.......
But for removing unity i didn't see nothing wrong.. all work fine ;)

Thank again for your help, i appreciate !!! :)

---


---
title: "Help...  Added new GDM and system now hangs..."
date: 2008-06-27
forum: General Help
---

### Post by rudy.elgato on 2008-06-27
Hi,

I need a little help, as soon as possible please.  I added a new GDM login screen using System -> Administration -> Login Window, and then added the *.tar.gz.  I then logged out of my system, but now I never get back to the login window.  All I get is the small spinning, busy icon.  I've previously added several other GDM login windows in exactly the same manner, and have not had any problem with any of those *.tar.gz.  The *.tar.gz I'm having problems with was downloaded from [http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883](http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883).  The download there is actually a *.zip file.  Within that zip file are 2 *.tar.gz files, one for the blue screen, the other for the brown screen.  I tried the *.tar.gz for the brown screen.

I've booted up my system right now with the 8.04 LiveCD.  I think I should be able to "fix" what needs to be fixed from here, shouldn't I?

Any help is tremendously appreciated.

Thanks...

---

### Post by rudy.elgato on 2008-06-27
FYI...  Not sure if it was the proper way to fix, but I've figured out a way to take care of this problem.

What I ended up doing during the LiveCD session, open up a terminal and:

- mount the system disk
$ sudo mkdir /media/sda1
$ sudo mount /dev/sda1 /media/sda1

- change the "bad" theme back to the good default Human theme
$ cd /etc/gdm
$ sudo vi gdm.conf-custom
the name of the bad theme was/is nUbuntu-Human.  so all I did was change this to Human.

Exited the LiveCD session, and my system booted properly back to the default Human GDM login theme.

So...  beware of that very good looking nUbuntu-Human GDM login theme posted out there on gnome-look.org (it's actually on deviant art).  It's a very nice looking, dark screen, which is what I was looking for, but it definitely caused me grief.  Not a comfortable feeling when your system can't reach the login screen.

---


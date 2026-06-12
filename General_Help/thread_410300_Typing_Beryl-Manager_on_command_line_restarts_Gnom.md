---
title: "Typing Beryl-Manager on command line restarts Gnome"
date: 2007-04-15
forum: General Help
---

### Post by FastZ on 2007-04-15
Everytime I type "beryl-manager" at the command line and hit enter, Gnome restarts and I have to log in again.  Have any ideas about what might be causing that?

---

### Post by Happy_Man on 2007-04-15
That happens for several reasons. Could you please provide a link to the howto you used to install Beryl? Your video card model too, please.

---

### Post by FastZ on 2007-04-16
I dont remember which how-to I used to get it going.  Beryl has been running on my machine since late last year and this is the first time I've come across this problem.  Each time I type that in the command line, and hit enter, GDM restarts.  I have an nVidia gForce 440MX I think for my video card.  I made no changes whatsoever to my Beryl Installation.  Just all of a sudden, I rebooted and then when I logged back in, and tried to start Beryl up, I run into this problem.  I'm using the SVN version of beryl.  Beryl --version brings up Beryl-core 0.3.0-svn if that helps any.  Was the nVidia driver updated or something?

---

### Post by beerorkid on 2007-04-17
I had this happen and updating the nvidia driver fixed it for me.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I tried everything I could think of for hours then I figured what the heck will try envy, joy.

---

### Post by FastZ on 2007-04-17
Well, got a problem here as well.  I sudo apt-get install envy and it's showing my envy script is up to date so I run sudo envy and BAM!  GDM crashes...  Maybe I'll just do a solid install of Fiesty and redo all of the Beryl installation on there.  I dunno.  Thanks for the help guys.

---

### Post by beerorkid on 2007-04-17
I have not tried envy in the GUI.  although I hear it now will let you do that.

I just do a crtl alt F2 login and run it there.

---


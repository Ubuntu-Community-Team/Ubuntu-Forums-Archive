---
title: "installed kubuntu-desktop, jittery login window ensues"
date: 2007-08-21
forum: General Help
---

### Post by Rippy on 2007-08-21
I'm a gnome user but I thought I'd give kde another try. So I installed kubuntu-desktop with aptitude, and the installation went fine.

Now it starts up with a kubuntu splash, which I didn't intend but that's fine by me cause I prefer how it looks.

The problem is, if I log out of gnome (I have set to autologin) to change sessions into kde, after maybe 5 to 10 seconds after reaching the login screen, the screen goes insane. It's hard to describe, but it looks like a TV station when you're getting bad reception: lots of jittery horizontal tearing, a slightly offset ghost image, etc.

The next time I tried switching the session to kde really fast (since it still lets me enter my username and pass after it goes insane), but the problem still persisted even after KDE was fully loaded.

It also does this if I go to the login window and then log back into gnome, but if I just let it autologin then it works fine.

Anyone know why this might be? Is there something I need to do other than installing kubuntu-desktop?


Thanks!

---

### Post by ajgreeny on 2007-08-21
Just out of interest try using kdm instead of gdm as your desktop manager to see if it makes a difference.  I can't quite see why it should, both work fine on my machine, but then so do both desktop environments, which is not so in your case.
In terminal type:-
sudo dpkg-reconfigure gdm
This will offer you the choice of which to use, so give it a whorl, and see if anything changes.  You can easily change back again with the same command.

---

### Post by arist0tle on 2007-08-21
stick with gnome....it's less cluttered

---

### Post by damansandhu on 2007-08-21
kde is fine i am using it with no problems.

---

### Post by Rippy on 2007-08-21
Oddly enough, kdm fixed it. I'm just going to leave it like this to avoid breaking it again, hah.

Well, thanks. Gonna go through all these kubuntu menus and get seriously customized :)

---


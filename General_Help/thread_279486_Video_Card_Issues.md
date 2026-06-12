---
title: "Video Card Issues"
date: 2006-10-18
forum: General Help
---

### Post by oscabat on 2006-10-18
I have a Radeon 9550 and ever since I tried to update the drivers, I have had a hell of a time.  The drivers I tried to update to from the ATI website made my game crash (Americas Army, by the way).  I read the installation guide from ATI, and it said that they were only supported by Fedora and something else, but no technical Ubuntu support. So I changed to the ones through the apt-get (I'm not sure what I did now, but I read it on some thread in here).  They worked perfectly in the game, but they keep showing weird things normally, such as this:
[IMG]http://img.photobucket.com/albums/v625/oscabat/random/Screenshot.png[/IMG]

What drivers do I get, and how exactly do I install them?  Because my terminal knowledge is VERY limited.

Thanks.

Edit: I switched back to the old Xorg drivers with
> sudo dpkg-reconfigure xserver-xorg
and it works now.

---

### Post by pay on 2006-10-18
I normaly use the proprierty drivers (fglrx) for games. Heres a nice guide 
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---


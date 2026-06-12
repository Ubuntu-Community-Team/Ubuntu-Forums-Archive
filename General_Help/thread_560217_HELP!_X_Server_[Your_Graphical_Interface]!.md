---
title: "HELP! X Server [Your Graphical Interface]!?"
date: 2007-09-26
forum: General Help
---

### Post by Madmoose on 2007-09-26
Hello, 

The other day I got a new video card, and I put it in my box. I had and ATI, but I switched to a Nvidia. When I powered on after installing my new card everything seemed to be ok, but when the UBUNTU loading screen finished instead of opening Ubuntu it went to a DOS looking screen and said something like "Could not load your x sever [Your Graphical interface] would you like to go here to diagnose the problem?"

Can someone help me fix this, or do I have to do a whole new ununtu intall? I really don't want to loose my data or better my wifes... Me + lost wife's data = X.X R.I.P

Help! 

Thanks 

Moose.

---

### Post by forestpixie on 2007-09-26
you need to reconfigure X server

```
sudo dpkg-reconfigure xserver-xorg
```

choose vesa I think when it comes to graphics card,that should at least get you in

then you need to install the nvidia driver - either try the restricted driver manager in system > admin or alternatively try [envy]("http://albertomilone.com/nvidia_scripts1.html")

hope that helps

---

### Post by Madmoose on 2007-09-26
This is why I love Ubuntu. I always get fast help within minutes and 90% of the time it's right. I'll give that a try. 


Keep you posted. 

Thanks

---

### Post by forestpixie on 2007-09-26
> and 90% of the time it's right

I hope it works then would hate to disappoint :)

---

### Post by Madmoose on 2007-09-26
Hey, 

Thanks! Worked perfectly. Though, it started asking me things way beyond just the vesa thing. If all else fails keep pushing enter. :lolflag:

---

### Post by forestpixie on 2007-09-26
> If all else fails keep pushing enter

that's ok but ... how many 'Ubuntu has deleted my windows threads' have you seen :D

glad I could help

---

### Post by cattleeyes on 2007-10-20
I'm having this exact problem!
And am now cornered into a coffeeshop on wifi on a friend's computer to try to fix the problem.

I've spent a great deal of time going through the 
sudo dpkg-reconfigure xserver-xorg various options (though I haven't tried setting it to VESA, which I'll do when I get home), but every time, it tells me that it is going to overwrite possibly modified information but does not overwrite anything.

I'm more or less left without internet right now, but am wondering if there's anything else I can do.

Restarting GDM without fixing this problem first doesn't seem to help.

Thanks!

---


---
title: "Won't Give Me Boot Options"
date: 2007-06-11
forum: General Help
---

### Post by tux_rox on 2007-06-11
I wanted to try out Wubi, so I downloaded it, clicked through the options, pressed the "Finish" button, rebooted, and...

Went right back into Windoze 2000.

I have no options to boot into Ubuntu or Windoze.

Possible problems that I see:

1)  Windoze 2000 - too old for Wubi?
2)  10 gig hard drive with only 4 gigs free (before installing)

Please help - I really want to see this work.

---

### Post by CrazyGuy123 on 2007-06-11
4 gig is a bit low for wubi.

Were you logged in as administrator when it installed so it could add an item to the boot menu?

I don't think this has been tested on windows 2000, and while it should theoreticly work, there might be something wrong with it.  If I'm correct in saying it hasn't been tested on w2k, I have a copy of w2k and I could try it and see if I can figure out what's wrong.

---

### Post by ago on 2007-06-13
What version of wubi did you use? What is in your boot.ini? Can you try the latest minefield?

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by abn91c on 2007-06-13
check your windows 2k hardware profile, set the boot time to 10 or 15 seconds just in case, like the other post said 4 gigs is squeezing ubuntu on your drive, my dual boot with winxp took about 3.5 gig, make sure you defrag windows 2k also

---

### Post by tux_rox on 2007-06-14
Thanks for the responses - I'm getting excited, but it's still not working.

Ago:  used the version with the shiny silver "DOWNLOAD" button on the website - I'll try the minefield next.

abn91c:  it says - "Display lists of operating systems for:{30 seconds} in the control panel - is that what you're referring to?  Since I only have a 10 gig hard drive, I really can't squeeze much more than 4 out, but I'm doing my best.  And, yes, I defragged right before I downloaded (since I've downloaded it twice now, one with admin privileges and one w/o, *now* there's probably more junk I need to clean).

Look, the reason I want Wubi is because I want to be able to delete Ubuntu if necessary.  This is an on-loan computer (hence Windoze 2000), so I don't want to mess with the partitions and bootloaders if I don't have to.  So now that I've finally found a perfect solution other than running the Live Cd on a computer with 128 mb of RAM (imagine a mouse so slow, it takes about 60 seconds to get from one screen corner to the other), I really want this to work.

EDIT:  Sorry Ago, I forgot to answer:  how do you get to the boot.ini?  And what am I looking at/for when I get to it?

---

### Post by abn91c on 2007-06-14
yes i was referring to the 30 seconds timer there, try adjusting, see what happens

---

### Post by ago on 2007-06-15
> **tux_rox said:**
> 

EDIT:  Sorry Ago, I forgot to answer:  how do you get to the boot.ini?  And what am I looking at/for when I get to it?

Try the latest minefield first. Boot.ini is in c:\boot.ini, it may be hidden, there should be a c:\XXXldr="Ubuntu" entry in there.

---

### Post by tux_rox on 2007-06-15
I downloaded the minefield you showed me, Ago, and it... worked perfectly.  Ubuntu is now up and running sucessfully.  I still haven't found the boot.ini, but whatever, it's working now.

I'm not sure if I did something differently or it was the minefield, but nontheless, I am ecstatic.  Wubi is everything I ever hoped for with Ubuntu and more.  It even recognized all of my documents from my Windows "partition"!

Now the only thing that isn't working is the internet, but even when I did the Live CD, that wasn't working, so I'm monkeying around with Ndiswrapper right now.  (But that's a topic for another thread...)

Thanks for your help!!!\\:D/

---


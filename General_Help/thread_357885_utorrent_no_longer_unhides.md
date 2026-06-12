---
title: "utorrent no longer unhides"
date: 2007-02-10
forum: General Help
---

### Post by klep on 2007-02-10
hello, 

recently, when i start utorrent via wine the icon in the top right tray appears and hovering over it shows that everything is downloasding and uploading, but right clicking on it and clicking show doesnt do anything. it always used to but now it just doesnt do a thing. 


Anyone got any suggestions on how i can rectify this?

cheers,

---

### Post by Doug11 on 2007-02-10
I don't right click on mine. I just double click the icon and it hides and unhides, if this is what you are talking aobut.

---

### Post by klep on 2007-02-10
> **Doug11 said:**
> I don't right click on mine. I just double click the icon and it hides and unhides, if this is what you are talking aobut.

hello, 

thanks for the reply. I've always right clicked but regardless of that doubleclicking on the icon doesn't unhide it either.

---

### Post by fiftynine on 2007-02-18
> **klep said:**
> hello, 

recently, when i start utorrent via wine the icon in the top right tray appears and hovering over it shows that everything is downloasding and uploading, but right clicking on it and clicking show doesnt do anything. it always used to but now it just doesnt do a thing. 

cheers,

I've wrestled with this problem few times. I can offer no easy workaround nor solution, but by reinstalling wine I've always got µ to work.

But hey, I'm still a windows user too, so this reinstalling-thing is a natural move for me [IMG]http://i9.tinypic.com/2luxvr7.gif[/IMG]

---

### Post by toast_king on 2007-02-19
> **fiftynine said:**
> I've wrestled with this problem few times. I can offer no easy workaround nor solution, but by reinstalling wine I've always got µ to work.

But hey, I'm still a windows user too, so this reinstalling-thing is a natural move for me [IMG]http://i9.tinypic.com/2luxvr7.gif[/IMG]


I had to do the same as you, after reinstalling it worked perfectly.

Also, SA EMOTICON.

---

### Post by fiftynine on 2007-02-19
> **toast_king said:**
> I had to do the same as you, after reinstalling it worked perfectly.

What wine version do you run? Mine's 0.9.31. Maybe it's version-specific problem and µ works well with older wine versions, as some people dont have any probs with this setup.

µ did this again yesterday, so if anyone has any tips I'd be more than grateful to try them out as I'm pretty sure I'm going to face this problem again soon.

> 
Also, SA EMOTICON.

:awesome: is simply so.. awesome. I knew that someone would notice ;)

---

### Post by SmiLey497 on 2007-02-19
i just go in the .wine folder and delete all the utorrent data, than it works fine after that just gotta reconfigure it

---

### Post by fiftynine on 2007-02-19
> **SmiLey497 said:**
> i just go in the .wine folder and delete all the utorrent data, than it works fine after that just gotta reconfigure it

I tried that before and it didnt help.

---

### Post by oranguman on 2007-03-08
here's the thing: this is the most awfully-supported bug ever. :)

the best thing to do that i've found so far is just to workaround it. 

1. Get rid of utorrent

2. Reinstall it from the standalone in Wine

3. HERE'S THE RUB:   DO NOT minimize the program before doing the following. 

        A. Set the program not to minimize to the "system tray" (in linux that's "notification area"), but instead to the "Window List" area of the bar. 

there are specific instructions on how to do this here: [http://www.securenet.net/members/jeanpelo/linux_guide.html](http://www.securenet.net/members/jeanpelo/linux_guide.html)

but it's pretty easy. More difficult is letting go of that prime menu-bar real estate!



EDIT:   found this at the Wine Buglist. 

RE: Not Showing Window At All
by HeWhoWalks on Sunday March 4th 2007, 22:22
Found the solution.

Delete settings.dat from the uTorrent application data folder. In my case, this was:

/home/username/.wine/drive_c/windows/profiles/username/Application Data/uTorrent

Good luck :)


FURTHER EDIT:  this works for me; I think it is just the equivalent of reinstallation. With the settings corrected as above, utorrent will go to the desktop (in the form of a non-transparent, always-on-top icon over a blue box that says "utorrent") instead of inhabiting the notification area, which is buggy. I'm a happy camper, even though this is fairly ugly, it's much better than not seeing the P2P at all..!

---

### Post by Darko Beta on 2007-03-08
I had this same problem, and got frustrated enough to quit using utorrent and try Deluge.  I would highly recommend it--I have had a great experience with the program.  Any time you can find the Linux alternative so you don't have to run wine it's a great thing.  (Now if I could only find a Picasa alternative I'm happy with...)

---

### Post by darkdays on 2007-05-02
Just had this problem and cleaning the Application Data/utorrent folder fixed it! Thanks!

Used Deluge but switched to utorrent as I found Deluge lacking in bandwidth management and it has no priority support. Hoping that it evolves to the point when it suits my needs as I'd much rather run a native client than one through wine with all it's horrors. Also some private trackers for unknown reasons seem to have banned Deluge.

---

### Post by ninjamonkey26 on 2008-02-01
oranguman's solution worked!!!!!!

---


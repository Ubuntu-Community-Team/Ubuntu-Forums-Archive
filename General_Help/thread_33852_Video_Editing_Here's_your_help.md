---
title: "Video Editing: Here's your help"
date: 2005-05-12
forum: General Help
---

### Post by gratefulfrog on 2005-05-12
Dear Ubuntu friends,

I've been fighting through the installation of a Ubuntu based DV editing platform on an AMD64 and at last can provide all with a little howto: [http://gratefulfrog.net/HowToDvd.html](http://gratefulfrog.net/HowToDvd.html) 

There you will see how I have managed to setup the tools, some of their known bugs, as well as the process that I use to take DV footage on a camescope and make it into a DVD that can be played on a TV by means of a normal living-room DVD-player.

I describe as best I can how to set-up and use the following tools:
[list]
[*]kino
[*]dvgrab
[*]cinelerra
[*]ffmpeg
[*]mplex
[*]dvd-styler
[*]dvd-slideshow
[*]mplayer
[/list]

The use of **checkinstall** and **dpkg** is also mentioned and might interest newbies!

I hope that this will help some poor soul so that she/he doesn't have to go through months of wandering the net before being able to make a DVD masterpiece!

 :)

---

### Post by Mr Wonka on 2005-05-12
I really very interested in getting Cinelerra up and running. But, for the life of me I can't get it to compile. How did you deal with it? You instructions on that point aren't very comprehensive. Where do you get the SRC code from? The links to the CVS site only provide the compiled .deb packages which AFAIK are useless.

I've got all the dev libraries installed but it's bombing out on a load of calls to the XF86 headers. Ubuntu runs xorg so of course they don't exist, I don't need to be told that. What did you do to get around this?

This is really frustrating. I need this software to edit and composite my 3d renderings. It was a pain on Gentoo but at least I could get it working.

Thanks for any help.

Mr Wonka

---

### Post by fsman on 2005-05-12
I got cinelerra working very easily in hoary.

just do the following..

Download the binary rpm from their site [http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)
then 
sudo alien cinelerraxxxx.rpm
sudo dpkg -i cinelerraxxx.deb

that's it

---

### Post by gratefulfrog on 2005-05-13
Compiling all depends on what librairies you have installed, and what platform architecture you use.

I am running Hoary 64bit on an amd64 processor. 

The sources are available at the repository I mentioned on my HowTo web page. 

However, I downloaded the cinelerra sources from heroinewarrior and compiled them by carefully following the instructions. I had no message about XF86 when I built it. However, there were 1-2 syntax errors in the Makefile that I had to fix manually. It is not clear to me if these were really errors or something to do with the way my system was set up.

If you need more help, tell me about your platform and the errors you get and I'll try to help.  If you want real expert help, since I'm only new to this, you should ask your questions on the #cinelerra channel of the freenode IRC. There, you will find experts who can and will help (that's how I made it, too!)

Good luck,
Gratefulfrog :grin:

---

### Post by noerej on 2005-06-29
I got cinelerra working using the method fsman suggested. Very helpful post!!!

---

### Post by cross5 on 2005-07-21
[QUOTE=gratefulfrog]Dear Ubuntu friends,

I've been fighting through the installation of a Ubuntu based DV editing platform on an AMD64 and at last can provide all with a little howto: [http://gratefulfrog.net/HowToDvd.html](http://gratefulfrog.net/HowToDvd.html) 

There you will see how I have managed to setup the tools, some of their known bugs, as well as the process that I use to take DV footage on a camescope and make it into a DVD that can be played on a TV by means of a normal living-room DVD-player.

I describe as best I can how to set-up and use the following tools:
[list]
[*]kino
[*]dvgrab
[*]cinelerra
[*]ffmpeg
[*]mplex
[*]dvd-styler
[*]dvd-slideshow
[*]mplayer
[/list]

The use of **checkinstall** and **dpkg** is also mentioned and might interest newbies!

I hope that this will help some poor soul so that she/he doesn't have to go through months of wandering the net before being able to make a DVD masterpiece!

 :)[/QUOTE]


Link doesn't work - could you fix it please? or email it to me?

I REALLY need help with this - thanks!  :)

---

### Post by Gouchi on 2005-07-26
For video editing, you can try [Pitivi](http://www.pitivi.org) gnome video editor based on the GStreamer framework.  ;-)

---

### Post by gratefulfrog on 2005-08-03
[QUOTE=cross5]Link doesn't work - could you fix it please? or email it to me?

I REALLY need help with this - thanks!  :)[/QUOTE]

Sorry for the delay in replying... don't know why that link fails... try simply:
[http://gratefulfrog.net](http://gratefulfrog.net) 

and follow the embedded links.

another great source of info is the cinelerra IRC channel!
Good luck & let me know if any more help is required!

---


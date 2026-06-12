---
title: "Building a multimedia box"
date: 2006-07-10
forum: General Help
---

### Post by ubuntukid on 2006-07-10
I wasn´t really sure were this post bellonged so I put it here.

I want to build a small linux box to connect to a set of speakers and act live a jukebox. The computer will work as a sort of server as there will be no screen connected to it. I want to be able to play mp3 files, cd´s, m3u and real audio streams like what the bbc uses. This server will have an internett based interface. So if the computer is currently playing a song I can log onto a webpage using the internett and using the nettpage, change to a different song or radio station. The reason I want to do it like this is because I´ll be able to use my Nintendo DS as a remote controll once Opera is released in Europe. The internett connection will be WiFi based and so I´ll be using a WiFi card. Now because there will be no screen connected to the box I wont need a GUI so it will all be terminal based. 

So here comes my question. Is Ubuntu suited for this task and can anyone tell me where to go to get more info.

Also will I be able to access the Ubuntu terminal from my Mac? I see my dad logging onto his computers terminal at work from his home computer all the time. If I can do this then once the operatingsystem has been installed I wont need a screen anymore.

---

### Post by reacocard on 2006-07-10
to access the terminal remotely, use ssh.

---

### Post by jenred on 2006-07-10
Have you taken a look at freevo?

[http://freevo.sourceforge.net/index.html]("http://freevo.sourceforge.net/index.html")

Instructions for installing on Ubuntu

[http://freevo.sourceforge.net/cgi-bin/doc/FreevoAptUbuntu]("http://freevo.sourceforge.net/cgi-bin/doc/FreevoAptUbuntu")

---

### Post by hanzomon4 on 2006-07-10
> The computer will work as a sort of server as there will be no screen connected to it. I want to be able to play mp3 files, cd´s, m3u and real audio streams like what the bbc uses.

I have no experince with using linux as server, but when it comes to playing mp3 or some other non-free codecs its easy to get set up (just download some files). When it comes to streaming media I had  a hard time getting it to work. 
This was just my experience... but any way I got it working with the mplayer-plugin from the package manager.. It was more work then it needed to be, and I would suggest compiling  the latest mplayer-plugin (3.25?) from source.. 
Use [this howto]("http://ubuntuforums.org/showthread.php?t=179694&highlight=mplayer-plugin") for instructions on compiling the plugin..
Okay thats my 2 cents. ;)

---

### Post by briguy on 2006-07-10
Check this out - I think this is what you're looking for: [http://devices.natetrue.com/musicap/](http://devices.natetrue.com/musicap/)

---


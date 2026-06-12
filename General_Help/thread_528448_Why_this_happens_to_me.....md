---
title: "Why this happens to me...."
date: 2007-08-17
forum: General Help
---

### Post by telovoyagarcar on 2007-08-17
I can't believe how shitty my experiences with Linux have ALWAYS been. It is hard to believe that this only happens to ME.

I will write a long review with a STEP by STEP, about how one can install Ubuntu and start having problems with basic stuff like playing MP3 and videos. I got those notes at home, and i took them while in the process of reinstalling from scratch a copy of Ubuntu. Obviously i ended with a system not able to do the basic stuff that the average person needs to do.

Right now i am in a friend's house, trying to find a solution for her old Athlon XP 1.6Ghz with 512MB of ram. cuz it has been running slow lately.

I used Wubi and installed Xubuntu, as it is supposed to work better on these older machines.

All she does with a computer is web, email, music, pictures, spreadsheet stuff and printing.

I just spent 3 hours (she has a 256kb connection) downloading, installing and configuring Xubuntu.

This is what i ended up with:

1. The tool bar and task bar on top and bottom disappeared so now i can't "fix" or launch anything. 
2. No MP3 (i followed this guide: [http://www.harecoded.com/2006/02/17/how-to-play-mp3-with-ubuntu/](http://www.harecoded.com/2006/02/17/how-to-play-mp3-with-ubuntu/))
3. Amarok crashes, can't play ****.
4. Xine is not able to play MP3 after installing all those packages in the tutorial.

So now like everyone else i have to do research and spend more time fixing something that should work out of the box, or at least be SIMPLE to make it work.

My rant is cause of the hundreds of reviews i see every day in digg.com and other sites, about how good, stable, simple, reliable and specially "better than windows xp - vista", Ubuntu is as a desktop option.

Please stop lying to the people and start writing about the reality about Linux as a Desktop station: "As soon as you start configuring it, it becomes NOT user friendly, time consuming, more dificult than windows or OSX, UNSTABLE, ARCHAIC, CLUNKY, NOT COMPATIBLE, etc"

YES, i know you can make it work after wasting hours asking in forums and playing with commands in a shell. But again, that is not how Ubuntu is being described to be in most reviews out there.


Now flame me if you want.

And if you don't, at least try to save all the time i wasted today with this, and tell me how do i make XFCE to show me again the top bar and taskbar + how to make it work so it will play some music.
Thank you for that.
The only TRUE thing about Ubuntu and Linux in general, is how good, helpful and nice the community is, and what a great NETWORKING tool linux can be. And that is my own experience.
Now.. as a Desktop ... IT SUCKS!!

---

### Post by cee-jay on 2007-08-17
telo:

I can REALLY relate!  I'm actually a decent advocate for Ubuntu, but you really have to install EasyUbuntu or something like that to make it do stuff like MP3 playback, play commercial DVDs, etc.  Just Google it.  Otherwise, an Ubuntu-based distro might be a good option.  Linux Mint is one such distro that does most of that stuff by default.

About your menubar/taskbar/whatever, one thing I remember about XFCE is that a right-click on the Desktop will get you the system menu!  From there, you should be able to find settings in a submenu for those preferences.  You might just try to add Gnome and see how it compares performance-wise, if it's more usable for you.

I'm sure others will have much better answers for you, but this post just caught my eye, and I was remembering some of my own adventures.  I think you're right about it's level of user-friendliness so far...

---

### Post by p_quarles on 2007-08-17
My guess is that the reason it always happens to you is that you're going about it all wrong. 

1) Wubi is *not *a good alternative to installing Linux on a separate partition using its native ext3 filesystem. 
2) Amarok is a KDE application. Find a media player that uses the Xfce libraries.
3) The tutorial you linked to is more than a year old, and contains outdated information. For (much) better instructions on getting and installing media codecs, see the Ubuntu user documentation:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Hope this helps.

---

### Post by HermanAB on 2007-08-17
Well, if you want easy to use wizards that will configure anything and everything, then Ubuntu is probably not the right distribution for you - look at Mandriva instead.

Regarding your user desktop bluez - create a new user, copy the data over, then delete the old user.  A more elegant solution is to look at the skeleton directory and delete the directories in the home directory that correspond to /etc/skel, then copy the stuff from /etc/skel.  This is what the new user creation does - it uses skel to set things up.

Hope that helps!

Cheers,

Herman

---

### Post by HermanAB on 2007-08-17
BTW, I have to concur with a previous poster - if you wish to configure Ubuntu, then you have to use the Ubuntu documentation, not stuff off some random web site.  

I installed a laptop for my son yesterday and the Ubuntu multi-media configuration worked perfectly: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

That is from the second sticky note in the multi-media forum.

---

### Post by strabes on 2007-08-18
How to play any media file in ubuntu:```
sudo apt-get install ubuntu-restricted-extras
```

You should be able to run something like ```
xfce4-panel
```to get the panels to show up. I'm not sure since I don't use xfce.

Use programs that are designed for xfce or gnome while using xubuntu. KDE apps will take forever to start up on the kind of system you mentioned especially if no KDE libs are loaded on bootup.

---

### Post by V3lier on 2007-08-18
Well it truly sucks that you have such bad luck. I am running everything on my computer perfectly. Well, I truly can't say perfectly because I do have to search around to fix problems and such but 95% of that is because I keep tweaking things around because I'm always trying to make things run faster and such but I easily made MP3s work and the installation was quick and painless. I hope you find ways to make things work for you.:KS

---


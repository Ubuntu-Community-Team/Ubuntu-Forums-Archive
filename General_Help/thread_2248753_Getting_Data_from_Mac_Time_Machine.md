---
title: "Getting Data from Mac Time Machine"
date: 2014-10-16
forum: General Help
---

### Post by Tim_Johnson on 2014-10-16
One of my computers is currently a Mac Mini. If this computer were to fail, it is highly likely that I would replace it with a
linux-based machine. I run backups for the mini daily using Time Machine. The backups are written to an external USB 
drive. Does anyone know if there would be any issues transferring user data from the Time Machine storage to the new linux box?
thanks
tim

---

### Post by nerdtron on 2014-10-17
Time Machine really has a nice GUI, and pretty solid backup. Apple really made it quite good. The closest thing I see in Linux is Back in Time. The GUI is not very pretty and it could be a little hard to setup. You can give it a try.

Then again regarding restoring your backups from Time Machine, do you mean you want read the Backups created by Time Machine and restore them in Linux? I'm not sure if this is possible, I don't have a Mac to test but I have the impression that these backups are designed to be restored only on a Mac rather any other OS.

---

### Post by Tim_Johnson on 2014-10-17
I can read the Time Machine storage from Midnight Commander on my Mac. When time permits me (probably tomorrow), I will attach the external Time Machine drive to a Linux box and see if
linux can read it. Barring a formal translation policy, if linux can read the Time Machine drive, than one could simply copy. I will post back when I get to it.
thanks for the reply 
cheers
tim

---

### Post by coffeecat on 2014-10-17
> **Tim_Johnson said:**
> Does anyone know if there would be any issues transferring user data from the Time Machine storage to the new linux box?

Yep. Headaches, irritation and exasperation.

Have a look at this post:

[http://ubuntuforums.org/showthread.php?t=2193764&p=12874113&viewfull=1#post12874113](http://ubuntuforums.org/showthread.php?t=2193764&p=12874113&viewfull=1#post12874113)

Fortunately, the script in the third link is a life saver, or at least it was when I ran a simulation about a year ago. 

Rather you than me. :wink:

**Edit**:

> **Tim_Johnson said:**
> When time permits me (probably tomorrow), I will attach the external Time Machine drive to a Linux box and see if
linux can read it.

It can't. In a word (or four): *hard links to directories*, which Linux doesn't support. It's all in the links in the linked post. Good luck!

Oh, and - *Thread moved to **General Help**.* It's not really an Installation and Upgrades topic.

---

### Post by Tim_Johnson on 2014-10-17
Yeah, coffecat, I just hooked up to a linux box and you are right. I've take a quick look at [http://ubuntuforums.org/showthread.p...1#post12874113]("http://ubuntuforums.org/showthread.php?t=2193764&p=12874113&viewfull=1#post12874113") and
will pursue that further shortly. 
Thanks - a little foresight can prevent a lot of back peddling.
cheers
tim

---

### Post by Tim_Johnson on 2014-10-18
Good thread. Thanks to all who replied. 
cheers
tim

---


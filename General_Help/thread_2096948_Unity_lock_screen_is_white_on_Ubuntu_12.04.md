---
title: "Unity lock screen is white on Ubuntu 12.04"
date: 2012-12-21
forum: General Help
---

### Post by kedmond on 2012-12-21
I've asked this question before ([http://askubuntu.com/questions/193827/white-lock-screen-in-gnome-3-4](http://askubuntu.com/questions/193827/white-lock-screen-in-gnome-3-4)) but no one seems to know the correct answer.

The Ubuntu 12.04 lock screen is supposed to look like this: [http://cloudfront.omgubuntu.co.uk/wp-content/uploads/2012/02/new-lightdm-lockscreen-500x351.jpg](http://cloudfront.omgubuntu.co.uk/wp-content/uploads/2012/02/new-lightdm-lockscreen-500x351.jpg)

However, my lock screen is just white. When I begin typing my password, a window like this appears: [http://complete-concrete-concise.com/wp-content/uploads/2012/04/ubuntu-12.04-how-to-lock-your-screen-1.jpg](http://complete-concrete-concise.com/wp-content/uploads/2012/04/ubuntu-12.04-how-to-lock-your-screen-1.jpg)

The white screen is unacceptable for my workplace. And I am not going to install xscreensaver as a workaround. How do I get the Unity Greeter to handle my lockscreen, as Ubuntu 12.04 intended?

Thanks.

---

### Post by Complete Concrete Concise on 2012-12-27
This appears to be an outstanding bug with the unity / lightdm greeter.
 
You probably know that yourself from reading this bug report: 
[https://bugs.launchpad.net/ayatana-design/+bug/878836](https://bugs.launchpad.net/ayatana-design/+bug/878836)
 
I suspect there is ideological (as well as probably technical) issues in implementing it the way we would expect it to be handled - as this quote from that report indicates:
 
*"I was told that the next version of lightdm does the locking instead of the indicator. This still breaks with other DMs such as gdm, kdm, etc."*
 
The second comment in that report indicates the bug / feature is of status: **Won't fix**
 
This later report seems to indicate that the earliest such a feature might appear is in 13.04:
[https://blueprints.launchpad.net/ubuntu/+spec/topic-quantal-desktop-greeter-lockscreen](https://blueprints.launchpad.net/ubuntu/+spec/topic-quantal-desktop-greeter-lockscreen)
 
I think the fundamental problem is that Linux is a command line driven OS and all the GUI niceties are just hacks on top of the command line. 
 
It is too bad, because it would be nice to have a more consistent / uniform look and feel.

---

### Post by zombifier25 on 2012-12-27
The feature first appeared in 11.10 testing, but was later dropped (temporarily) because it causes problems to NVIDIA users. From what I'm seeing, they're working on it.

(then again, EVERYTHING cause problems to NVIDIA users)

---

### Post by raelgc on 2013-04-10
Disabled VSync on Unity. I don't know how to do it, cause I use KDE. But I have a NVIDIA card, and I read in other posts that disabling will work. And it worked for me with KDE.

---


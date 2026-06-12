---
title: "Wordpress incompatibility?"
date: 2013-11-23
forum: General Help
---

### Post by mikeebean on 2013-11-23
My wife and I have been building and editing websites in Wordpress; she uses a Mac and I use Ubuntu 12.04. Until now I've had no problems using Wordpress with Ubuntu.

On our current project, the website and its admin pages just won't load consistently in Ubuntu in either Chrome or Firefox. They work fine on both her Mac and my Vista partition in every browser.

However, in Ubuntu, the website and admin pages either take a long time to load or fail to load at all. When I am actually able to access the site, Wordpress constantly gives me a warning: "Connection lost. Saving has been disabled until you&#8217;re reconnected. We&#8217;re backing up this post in your browser, just in case." It's so maddeningly unreliable and I've had to resort Vista to do any real work.

I'm hoping someone might have some suggestions which will allow me to stick with Ubuntu for this project? Thanks!

---

### Post by mastablasta on 2013-11-23
where is the site you are building located? on your home server?

---

### Post by mikeebean on 2013-11-24
Hi Mastablasta-

The site is on 1&1 Linux hosting, and isn't on our home server.

Michael

---

### Post by coffeecat on 2013-11-24
Until about a year ago, I was administering a small Wordpress website hosted on paid (Linux) hosting and I encountered no problems administering it from my Ubuntu system. The only times I accessed the Wordpress site from Windows or MacOS was to check that it looked OK in those operating systems. 

I don't believe this is an Ubuntu issue specifically. I suggest you check your internet connectivity from Ubuntu and also see if there are any browser settings or addons different from your browsers in Windows and MacOS that might be causing this.

Having said that, googling 'wordpress "Connection lost. Saving has been disabled until you&#8217;re reconnected. We&#8217;re backing up this post in your browser, just in case" ' comes up with some interesting hits that show you are not alone and that suggest the problem may be related to certain Wordpress plugins:

[http://wordpress.org/support/topic/error-message-connection-lost-saving-has-been-disabled-until-reconnected](http://wordpress.org/support/topic/error-message-connection-lost-saving-has-been-disabled-until-reconnected)

[http://wordpress.org/support/topic/36-update-error](http://wordpress.org/support/topic/36-update-error)

[http://wordpress.org/support/topic/connection-lost](http://wordpress.org/support/topic/connection-lost)

Of course, that doesn't explain why you don't see this in the other 2 operating systems, but those links may give you a lead.

---

### Post by mikeebean on 2013-11-29
Thanks for the links, coffeecat. I never really found a solution, and didn't have time to mess with it. Hopefully it's some sort of glitch in WordPress that will get ironed out. It sounds like a lot of people have had issues on all OSes with the most recent WP update. In the meantime I'm reminded that I still need to keep Windows around, just in case.

---

### Post by mastablasta on 2013-11-29
i would try it on local server and see what happens. you can use turnkey wordpress image and just put it in virtualbox then access it from browser. 

i knwo about a few sites that for some reason i can't access form windows and can form linux. no idea why. can't even ping them from from windows.

it could also be you have a setting enabled in linux that is nto supported by your host. though i am not sure what that could be.

---

### Post by mikeebean on 2013-11-30
If it happens again, I'll try that. Hopefully this is a rare occurrence, however!

---


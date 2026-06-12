---
title: "Looking for PunchClock software"
date: 2008-05-04
forum: General Help
---

### Post by NickWilsdon on 2008-05-04
Hi,

We're trying to move our office from XP to Ubuntu. One of the applications we rely on is a punchclock application. It lets everyone here punch in and out of work and records all their hours. This is especially useful for our part or flexible time employees. It lets us view all the hours at the end of the month for payday. That's pretty much the functionality - nothing too complex.  

I've tried running PunchClock Pro (our software) through wine but I get an error. Run-time error '9': Subscript out of range. I've updated the wine DB with this report. 

Has anyone here heard of a Linux equivalent for this software? (can be paid). 

Thanks for your help

---

### Post by garfonzo on 2008-05-04
Hey there,

Just out of curiosity, how did the old system work? Did people carry cards and swipe in and out or was there an actual computer were people type in their name and "punch" in and out? The only experience I have with punch cards is when I used one at work. We each had a credit card style ID card which we swiped in and out to start and stop out shifts.

---

### Post by NickWilsdon on 2008-05-04
Hi Garfonzo

I don't want to linkdrop here but the software is called "PunchClock Pro/LionClock Pro" - if you search on Google with that it is the first result (Lionclock.com)

There aren't any cards involved, each terminal has a login box. Everyone who works here has a password and username, they can just login with that information and click the large 'in' or 'out' buttons to record their hours. 

They can also login to see how many hours they have done or get a print out. Our accounting person then checks these hours at the end of the month when doing the pay. It's a very useful tool as it cuts down on office administration. It not only logs hours for part time/flexible employees, it records overtime from your full timers too. 

The functionality is pretty basic though. You have one 'server' install and several 'client' installs. The server records the information, so just needs a connection over the local network. We put in the local IP of that machine (192.168.XXX.XXX) on the client copies. The server is just recording usernames and in/out messages. It will allow the administrator to adjust the records if the employee has forgotten to punch out at the end of the day (but makes a notation on the records, saying they have been manually amended).   

Anyway, I'll keep looking for some replacement software. I guess we could try running this inside a virtual Windows install but it would be good not to need that.

---

### Post by garfonzo on 2008-05-04
Interesting. I would imagine that this kind of setup could be mimicked with a website. Given that it only has to be basic "In" or "Out" functionality, you could set up a web page in full screen mode. With the help of a touchscreen, an employee could select their name from a list, enter their password, and then click In or Out.

The button press (punching in our out) could trigger a CGI script which writes data to a file. The file, a log file really, would be tracking all the punch ins and outs of all employees. Then, on the server side, another script could walk through the punch in/out script and figure out the hours each employee has worked.

 You could go a bit further and add user specific functionality like checking how many hours they've worked, their upcoming schedule, and other stuff. With a website, all sorts of fun stuff could be displayed.

Just an idea.

Of course, you'd need someone who knows how to program all of this :)

Edit: By the way, I checked out that software and it looks pretty slick. I'm more of a 'program it yourself' type of person though :)

---

### Post by Go_Bucks on 2008-05-04
Our company uses Clicktime ([http://www.clicktime.com](http://www.clicktime.com)). It has A LOT of functionality to it. It is a paid service... I am not sure how much it costs.

---

### Post by NickWilsdon on 2008-05-07
Thanks for the feedback guys. I'm beginning to think changing to a a web based option maybe the best way forward. This project "TimeClock" looks worth a try (ClickTime looks excellent but runs at $10-12/month per employee)-

[http://freshmeat.net/projects/timeclock/](http://freshmeat.net/projects/timeclock/) 

I'm also maintaining the Wine entry for the PunchClock/LionClock program so I may get some progress there by submitting the errors. 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7211](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7211)

If someone comes along looking for the same thing, check that page for progress.

---


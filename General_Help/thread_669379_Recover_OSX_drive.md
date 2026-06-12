---
title: "Recover OSX drive?"
date: 2008-01-16
forum: General Help
---

### Post by qsjcraig on 2008-01-16
Hello everyone,

I'm new to Linux and have a question regarding data recovery.

I have two Lacie D2 (pieces of junk) FW drives that have died on me (my buddy lost one too around the same time) Neither of them have mounted on my Mac for weeks.  Today, I took them both out of their enclosures and put them inside a PC running Ubuntu.  One of them mounted right away (data is currently being moved to our network at work)  the other drive mounts for a split second then vanishes...over and over again.  It is showing that there is about 239G of "something" on it, which I'm hoping is a good sign.

Is there anything I can do to try and get the data off the second drive?  I do not have money for data recovery, so I'm hoping for any and all suggestions.

Thank you very much for your time,
Craig

---

### Post by aysiu on 2008-01-16
> **qsjcraig said:**
> Hello everyone,

I'm new to Linux and have a question regarding data recovery.

I have two Lacie D2 (pieces of junk) FW drives that have died on me (my buddy lost one too around the same time) Neither of them have mounted on my Mac for weeks.  Today, I took them both out of their enclosures and put them inside a PC running Ubuntu.  One of them mounted right away (data is currently being moved to our network at work)  the other drive mounts for a split second then vanishes...over and over again.  It is showing that there is about 239G of "something" on it, which I'm hoping is a good sign.

Is there anything I can do to try and get the data off the second drive?  I do not have money for data recovery, so I'm hoping for any and all suggestions.

Thank you very much for your time,
Craig
I believe *ddrescue* or *dd_rescue* can help with even dead hard drives, but I don't know all the details of how it works (I've used it only on live hard drives).

---

### Post by Drakkenfyre on 2008-01-16
This isn't going to be a comprehensive answer, or even necessarily a useful one, but in a similar situation I did use dd with the commands to make it fill in unreadable bits with zeros--something that's been simplified with ddrescue.

However, I'm not confident that ddrescue will work in this instance, as you do have to be able to sustain a mount for it to work. However, FYI, ddrescue's page is here:
[http://www.gnu.org/software/ddrescue/ddrescue.html]("http://www.gnu.org/software/ddrescue/ddrescue.html")

Just to save yourself potentially a huge headache, I'd personally swap the cable. It's rarely ever the cause of problems, but if it is, you'll waste a lot of time. Of course, if it's the same cable you used with the other drive, I guess it works.

If this were me, here's what I'd so, and I'd appreciate some thoughts on whether this is the right action at this point, or if it's too early for this:

I'd take it out of the enclosure and plug it into a computer directly. If it's a 2.5" IDE drive, you can buy a little adapter for under $10 CAD. This will tell you if it's a problem with something in the enclosure, or with the drive itself. Thoughts?

---

### Post by tgalati4 on 2008-01-17
Years ago I had a couple of identical Quantum "Fireball" drives die at work.  I was able to take a working disk controller out of one and put it in the other and recover data.  One of your LaCie drives may have a controller problem that allows you to see the drive then heats up and dies.  By swapping controllers with the other drive, you may be able to grab some data off the drive.

I have a D2 as well, but it only sees a few backup images a year.  What kind of service were these drives used for?  Recording music perhaps?

---

### Post by az on 2008-01-17
> **qsjcraig said:**
>  the other drive mounts for a split second then vanishes...over and over again.  It is showing that there is about 239G of "something" on it, which I'm hoping is a good sign.

Go into the system log tool and post the output of /var/log/messages when you plug in the drive.


> **qsjcraig said:**
> 
Is there anything I can do to try and get the data off the second drive?  I do not have money for data recovery, so I'm hoping for any and all suggestions.

Thank you very much for your time,
Craig

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

### Post by Drakkenfyre on 2008-01-20
> **az said:**
> Go into the system log tool and post the output of /var/log/messages when you plug in the drive.




Very good idea. We can guess all we want, but any kernel messages we could get would help.

Also, I was a dork in that I didn't see that Craig had already taken the drives out of the enclosures. Well, while I agree with tgalati4 that swapping controllers might be what you'd have to do (though obviously an action of last resort), I'm curious: tgalati4, was there any soldering involved when you swapped controller boards? Or are there ribbon connectors or what? Thanks!

---


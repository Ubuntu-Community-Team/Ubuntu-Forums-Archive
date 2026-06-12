---
title: "how to install packages without internet connection"
date: 2006-08-21
forum: General Help
---

### Post by krmane on 2006-08-21
hello I am Krishnakant from India.
I have just started to use ubuntu.
I havbe one question on version 6.06 update 1.
I have a couple of computers where internet connection is not working and will be disconnected for next 2 days because of a major technical problem.
now my problem is that I am a visually handicap person and want to use gnopernicus on ubuntu.
as I said above I don't have internet connection and I can't wait for 2 more days.
I already downloaded gnopernicus .deb package and festival deb package from the ubuntu web packages web site.
I want to know how I can install it when internet is not there.
I heard that if internet connection is not there, I will have to take care of the dependencies myself.
is there a way to create an artificial reposetory on a new blank cd and install the packages needed without connecting the to internet?
and yes, what dependencies should I download for nopernicus to work?
thanks.

---

### Post by marianom on 2006-08-21
If you can access Synaptic and check gnopernicus spec, in the second tab "Dependencies" they're all required packages there. 
I think you should download'em on the CD and in the proper order given in "Dependencies" install them in the other machines, finally installing gnopernicus.

---

### Post by krmane on 2006-08-21
> **marianom said:**
> If you can access Synaptic and check gnopernicus spec, in the second tab "Dependencies" they're all required packages there. 
I am new to ubuntu and can't figure it out.
actually I have to tell a sited person to do it for me so I must know in which menu and what option do I need to choose to install nopernicus or any software?
where is the Synaptic utility?
I think you should download'em on the CD and in the proper order given in "Dependencies" install them in the other machines, finally installing gnopernicus.
how do I keep in order?  I mean if I collect them in a folder and then burn it on a cd what order can I gurenty?

---

### Post by Fass on 2006-08-21
> **krmane said:**
> how do I keep in order?  I mean if I collect them in a folder and then burn it on a cd what order can I gurenty?

If you put all the dependencies (that you lack - you only have to deal with the ones you don't already have installed) in the same directory, then you will be able to install all the packages with a simple "sudo dpkg -i *.deb" while in that directory. That way there is no "order" to keep track of.

---


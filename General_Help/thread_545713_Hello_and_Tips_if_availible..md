---
title: "Hello and Tips if availible."
date: 2007-09-07
forum: General Help
---

### Post by Allenwr on 2007-09-07
This is my 1st time on the forums and I just want to say hi to everyone and make a decent impression.

Anyhow, so I have a dell PowerEdge 4400 currently running Windows Server 2000. And I am going to be making the switch tonight over to Ubuntu 7.04 Server 7.04 Server Edition. My basic question is are there going to be any difficulties with installing that I might need to deal with? I have not used Linux in a couple of years and last time I did, it was Ubuntu, I am really out of practice and as stated I am looking for any advice/ideas that may help me make the change as smoothly as possible.

Thank you,
Allen

---

### Post by mtn on 2007-09-08
Hey Allen,

My initial response would be just do it and post back if you have trouble! But that is just because I love the feeling of freeing a new machine. It probably took me 3-6 months getting used to Ubuntu when I first switched a couple of years ago. Just figuring out all the little things that are new/different ways of doing things.  Anyway, apart from just getting on with doing the right thing...

I guess you have tested it with a live CD to make sure that the wireless (all the hardware including printers etc) work correctly? If anything does not work "out-of-the-box" would be worth doing some research just to make sure you don't have any show stoppers on your hands.

Apart from that I usually put the home folder on a separate partition, install all the updates and then (I probably should not say this!) I install Automatix and get to work installing all the extra stuff that I want on the machine - Flash, Google Earth, Thunderbird 2 etc etc. Using Automatix is very naughty (I am told) and you can install all the stuff without it, but it is convenient!

Are you planning to get Beryl running? If so you might want to check you video hardware is compatible.

Hope this helps. Just go for it. 

Yours

---

### Post by strabes on 2007-09-08
If you want to play MP3s and other proprietary media formats, install the ubuntu-restricted-extras package.

Use VLC as your video player.

Don't be afraid of the terminal.

Easytag is a great mp3 tagging program. It even supports renaming files from their tags.

Suspend and hibernate are iffy at best.

If you have an ATI card, buy an nvidia right now. Actually, ATI is supposed to release decent linux drivers in October, but talk is cheap.

If you have a broadcom wireless card, just search for the model number on these forums and someone will have it working. I had to compile ndiswrapper from source to get a couple friends' bcm4318 cards working. There are plenty of howtos, and some of them actually have a native linux driver now.

Everything else I can think of is pretty subjective and up to the user.

---

### Post by Allenwr on 2007-09-08
Thanks for the replies a lot of the software you have mentioned seems to be directed more towards a PC though, and I am actually doing a server instead and hopefully I will not need all of that. And I have not tested with a live CD, should I? Otherwise I am going to dive head first in a couple mins.

---

### Post by bikeboy on 2007-09-08
The LiveCD is a desktop thing. The server install has no GUI (were you expecting this?) to make it more lightweight etc.

---

### Post by Allenwr on 2007-09-08
Yea, I heard there was a GUI, but if there isn't where might I find one? Because I am not terminal fluent in Linux.

Edit:

Actually if I have Ubuntu on a PC with GUI, could I use that to remote into my server and thus making it simple for me to do what I need to do?

---

### Post by bikeboy on 2007-09-08
You can do GUI forwarding from your normal machine to your server (haven't tried it myself), or you could install the normal version on your server until you're more used to it, then disable the GUI later.

You will need to do some things with the terminal either way, try looking for some specific guides on help.ubuntu.com or [www.howtoforge.com](www.howtoforge.com) when you need help. From Ubuntu 7.10 onwards (about 2 months away) there will be an easier system called ebox. But in the meantime, it will be good practice learning to use the server by logging in and using the terminal, that's how I learnt.

[https://wiki.ubuntu.com/EboxSpec](https://wiki.ubuntu.com/EboxSpec)
[http://ebox-platform.com/](http://ebox-platform.com/)

---

### Post by avik on 2007-09-08
Since you say you're not so experienced with the command line, I suggest just using the LiveCD to install a desktop package.  Then, get the proper programs as you need them.

> Actually if I have Ubuntu on a PC with GUI, could I use that to remote into my server and thus making it simple for me to do what I need to do?

That works too.

---

### Post by Allenwr on 2007-09-08
If you guys haven't noticed, I am trying to do this as smartly as possible, I know I am going to need to dive in head first at one point, but till then...

Ok, here's a scenario I wanna run by you guys, lets assume I format my drives and install Linux Server 7.04, and its terminal only: Will it auto detect a hardwire LAN preset up? Or are there a few simple command lines to do?
But something tells me that at one point, I remember something network related in the Linux installer, am I correct, or is that only certain Linux distributions?

Now, the next question is partially based on the answer to the previous network related query.

Do I A) Install a GUI or B) I should I use Linux Ubuntu from my PC and do a type of remote access in?



And I really appreciate the help from you guys, it is far better then expected. And as always, "Think before you leap."

---

### Post by avik on 2007-09-08
> **Allenwr said:**
> Ok, here's a scenario I wanna run by you guys, lets assume I format my drives and install Linux Server 7.04, and its terminal only: Will it auto detect a hardwire LAN preset up? Or are there a few simple command lines to do?

It should, but it depends on the hardware.  It usually works, but some hardware requires extra setup.

> **Allenwr said:**
> Do I A) Install a GUI or B) I should I use Linux Ubuntu from my PC and do a type of remote access in?

If you have two computers, install a server on one, and a desktop on the other.  Make sure you have a computer with working internet access around (even if that means dual-booting) just in case networking doesn't work.  That way you won't be stuck.

With one computer, just install the desktop and install the server programs later.

---

### Post by Allenwr on 2007-09-08
I may, but I am after server power (gaming related), thats why. I was thinking that server would have less stuff with it resulting in an increase of productivity. Last question, does a remote desktop capability come with Ubuntu? But something tells me I need to find it.

---

### Post by avik on 2007-09-09
> I may, but I am after server power (gaming related), thats why. I was thinking that server would have less stuff with it resulting in an increase of productivity.

If it's a game server, even Ubuntu server will have extra packages for your needs.  Ubuntu server makes it easy to do things like run a web server, etc.

I'm just trying to make sure you have a means of accessing online help; that way you won't be stuck.

> Last question, does a remote desktop capability come with Ubuntu? But something tells me I need to find it.

Yes, if you're using the desktop version.  I also believe ssh (a "remote command line," if you will) comes installed on either version, though I could be wrong.  Still, it takes literally one step to install it.

---

### Post by Soarer on 2007-09-09
You could install the server version, and then run Webmin ([www.webmin.com](www.webmin.com)) on 'top'. This is a web-based GUI which enables you to control & configure your server from a browser on your desktop system.

Still plenty of learning to do, though :)

---


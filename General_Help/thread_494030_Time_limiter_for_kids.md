---
title: "Time limiter for kids?"
date: 2007-07-06
forum: General Help
---

### Post by naubusan on 2007-07-06
Is there any available?
Want to make weekly schedule when one can use the computer.

---

### Post by MCSE_Crossover on 2007-07-06
A piece of paper and a sharpie for the calendar? Along with maybe a digital clock or a kitchen timer that will "ding" when their time is up?

Just an idea :)

---

### Post by Wiebelhaus on 2007-07-06
I just yell at them , kinda like my dad did.

---

### Post by EvilMarshmallow on 2007-07-06
Gotta agree... the best solution is not technology, but making your rules clear and enforcing them personally.

That said,  I read once on another forum about a guy who used cron to replace his child's host file at a given time (kid was always IMing and on MySpace, never did much of anything else.  He redirected the host IP for the IM Protocol and MySpace.com to 127.0.0.1 at a certain time every day, and then put it back each morning so that the kid could play up until a predetermined time each day.  That would work until your kids get good at using the computer...

---

### Post by naubusan on 2007-07-06
I don't have kids. This is my friends question.
I just can't stand those dwarfs.
Funniest and easiest thing to do is just beat them.

---

### Post by mbeierl on 2007-07-06
iptables (part of the kernel) can do filtering by userid.  So you could have something that restricts internet access by time of day for specific userids.  But nothing stops them from hogging the computer playing local games.

Except for a cron job that kills the X session of specific usernames by time of day...

---

### Post by rusty4r on 2007-08-07
I read a thread about something that would lock the keyboard and mouse after specified amount of time. I would like to find that thread again.

---

### Post by cogadh on 2007-08-07
The forum does have a search function built in. Try it.

---

### Post by rusty4r on 2007-08-07
I found it at [http://ubuntuforums.org/showthread.php?p=2332006#post2332006]("http://ubuntuforums.org/showthread.php?p=2332006#post2332006")

And I tried several times cogadh, but it was a matter of finding the right keywords because this thread was several months ago and you get alot of returns on your searches

---

### Post by ertrules22 on 2007-08-07
My parents use a timer on my home computer (it runs Vista, sorry!).  I find that they use the excues that because I was just on the computer all day at work, I can't get on and play a game for an hour at home.  Also, my mom still says that even though the computer only times for an hour, I am on it FOREVER... yeah right!  Well, personally, screw timers.  If they are on the computer learning how to do something that will benefit them, let them be on, and if they just worked all day, let them play for an hour!  Holy crap!  We don't need to limit everything!
That's my opinion anyway...
:KS

---

### Post by L9d on 2007-10-12
I have a simple bash script that I wrote and run in the background on my system.
It limits the amount of daily time each of my kids are logged on. I've been using variations of it for about 6 years now and it works quite well with my 5 boys. 
I would be happy share with anyone that is interested. 
It is not a package but I can tell you how to set up the script in the init.d and rc scripts and the tracking/log files in the var directory so it loads automatically if you are interested.

---

### Post by rusty4r on 2007-10-12
I am interested, L9d

---


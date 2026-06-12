---
title: "reloading scripts to the server"
date: 2013-02-21
forum: General Help
---

### Post by taylorpIII on 2013-02-21
Greetings!  I am new to this forum so I hope I'm in the right place.  I'm here at the office and yesterday the server went down.  Now we have a few scripts that are not running.  I work in IT and people are looking to me to fix this.  How do I get down scripts back up and running on the server.  

-If it means anything, the scripts were built in Perl. 

Thx!

-Paul

P.S. If this isn't the appropriate area for server questions, then please direct me to the right place.

---

### Post by TheFu on 2013-02-21
Sorry, but it is hard to help based on the information provided.  A server "going down" is not good under any situation, so "scripts not running" is probably just the beginning of the issues. The root problem could be trivial or huge.

We need some troubleshooting information to even begin to help.
* which OS? which version?
* is storage full?
* what do the log files show? Any warnings? Errors?
* which programs run on the system?
* what sort of hardware is involved?

I'd strongly suggest that you engage a Linux professional to help the company resolve the issue efficiently.  PM me if you like and I'll try to help you ask a better question with relevant details.

If this were a home system, we could spend the next 2 weeks troubleshooting here, teaching you stuff, but since this is a work server, I suspect you don't have that luxury of time.

---

### Post by CharlesA on 2013-02-21
> **TheFu said:**
> I'd strongly suggest that you engage a Linux professional to help the company resolve the issue efficiently.

I'm all for community help, but if this is a time sensitive thing (which it sure sounds like) and having a down server is never a good thing, especially at work. Hiring a Linux professional would be the best option as they would be able to actually look at the hardware and software and determine the problem.

There are a ton of knowledgeable members here, but since this is likely a time sensitive matter, it would be best to actually get someone to look at it in person, even if the help costs a bit.

With that being said, for someone in IT, you sure didn't provide much information for this crashed server. Start with what TheFu suggested but these might help shed some light on the problem.

Check the system loads
What was running when the server crashed?
What sort of scripts are not working (all you said is they were Perl scripts)?
Where there any updates prior to the crash?

---

### Post by taylorpIII on 2013-02-21
This is a small business and I help out with IT.  I am not a linux programmer.  The business has an outside contractor that backs up everything we do here.  When the server went down, they had it back up and running within a few hours.  They handle the big stuff not the small stuff.  

This is an online based business.  Most of the scripts are working just fine, but there are a few that are not running.  These scripts have to do with orders being placed, Ebay, Buy, Amazon, etc. 

They scripts are located in a directory called "/usr/lib/cgi-bin".  The business is running smoothly, so I guess the problem has been solved.  One lady came out and said so and so's script stopped running can you fix it?  I guess it would a matter of going into the terminal and reloading it, but I don't know how.  That is basically what I was inquiring about.

---

### Post by CharlesA on 2013-02-21
Well, you probably run them like any other script, unless they were meant to be called via PHP or another server side language. If that was the case, you would need to figure out what the problem is before being able to fix it.

---

### Post by TheFu on 2013-02-21
> **CharlesA said:**
> Well, you probably run them like any other script, unless they were meant to be called via PHP or another server side language. If that was the case, you would need to figure out what the problem is before being able to fix it.

I am a perl monger and haven't got a real clue what he needed/needs based on the info provided.

For all we know, they've just been hacked and don't realize it.
Or it could be absolutely nothing.
Or all the orders could be sent to the wrong place.
Can't tell.
In 3 minutes, the problem could happen again and not recover.

"script" can mean anything.  There are thousands of "scripts" on any Linux computer.  "Perl script" does narrow it down a bunch. Now it is just hundreds of scripts.

Hopefully, it is nothing, but they really, really need to get their normal experts to look at it sooner than later.

This is frustrating. I'd really like to help, but can't.  It sorta reminds me of the days when I used to think that rebooting a PC actually fixed anything.  That still works with "that other OS", but not all that often with Linux.

---

### Post by prodigy_ on 2013-02-21
> **TheFu said:**
> It sorta reminds me of the days when I used to think that rebooting a PC actually fixed anything.
Rebooting a PC can fix many things... or make them worse... depending on the state the PC is in prior to reboot.

---

OK, on topic now: just how small the business is? On forums you can get some guidelines and some advice but companies generally want a guarantee that everything works and naturally that requires knowledge and time investment that cost money. 

If it's not urgent, I'd suggest you start learning Perl. Reading and fixing code is usually easier than designing and writing it from scratch. Though Perl code might prove quite obscure and difficult to read if it's poorly written.

Still, try it. Just don't experiment on your production systems. There's a good chance in a couple of weeks you'll be able to understand what's happening on your server much better than now.

---

### Post by CharlesA on 2013-02-21
> **TheFu said:**
> For all we know, they've just been hacked and don't realize it.
Or it could be absolutely nothing.
Or all the orders could be sent to the wrong place.
Can't tell.
In 3 minutes, the problem could happen again and not recover.

Indeed. We don't have enough info to even narrow down the issue. That is a huge issue since this is a commerce site, too. If they think it was just a hiccup or software issue and they had their sales db or something else accessed and didn't know it, it could be very bad for their business.

> "script" can mean anything.  There are thousands of "scripts" on any Linux computer.  "Perl script" does narrow it down a bunch. Now it is just hundreds of scripts.

Hopefully, it is nothing, but they really, really need to get their normal experts to look at it sooner than later.

Yep. It is still practically impossible to know what happened without looking at logs and/or the script or scripts that weren't running.

> This is frustrating. I'd really like to help, but can't.  It sorta reminds me of the days when I used to think that rebooting a PC actually fixed anything.  That still works with "that other OS", but not all that often with Linux.

> **prodigy_ said:**
> If it's not urgent, I'd suggest you start learning Perl. Reading and fixing code is usually easier than designing and writing it from scratch. Though Perl code might prove quite obscure and difficult to read if it's poorly written.

Still, try it. Just don't experiment on your production systems. There's a good chance in a couple of weeks you'll be able to understand what's happening on your server much better than now.

Huge +1 to that. Once you learn a bit about something, it makes it easier to deal with.

---

### Post by Habitual on 2013-02-21
As usual, What do the logs say?

---


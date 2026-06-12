---
title: "Simple Invoicing Software?"
date: 2007-06-17
forum: General Help
---

### Post by michaelzap on 2007-06-17
Hello -

I'm just looking for a simple invoicing program to replace Instant Invoice (which I used on XP before migrating to Ubuntu). Anyone have any suggestions? This seems like such a basic and necessary application for a lot of small businesses and independent contractors, but I've been searching and searching and I can't find anything at all.

Thanks in advance for your replies.

---

### Post by xhilyn on 2007-06-17
Hiya. I realise it's probably not what you want but have you looked at GnuCash. It's a complete Accounts programme so may not be what you need. I only use it for my home accounts but it is designed for small bussines and it's really quite good. Just a thought.

---

### Post by michaelzap on 2007-06-17
I think that GnuCash is more complex than what I'm looking for, but I actually haven't been able to test it out to see because no matter how I try to install it I always get missing or conflicting library errors and I've never been able to get it to install.

---

### Post by xhilyn on 2007-06-17
Oh thats a shame. I'm way too much of a nooby to Ubuntu myself to be able to help you there. I just installed it using Synaptic Package Manager and it just worked,  which I guess was just lucky.

---

### Post by michaelzap on 2007-06-17
OK. I finally did get GnuCash to install properly by reinstalling the build-essential package from the CD. It does seem a bit more complex than I'd like to use for my invoicing, however (I don't want/need to set up accounts and all that, and I don't need any other accounting functions).

Thanks for the suggestion, though.

Anyone know of a simple invoicing program for Ubuntu?

---

### Post by Beernut on 2007-06-17
Don't know if this is too simple for what you are looking for but it uses just Openoffice.

[http://software.newsforge.com/software/05/09/01/152212.shtml?tid=152&tid=93](http://software.newsforge.com/software/05/09/01/152212.shtml?tid=152&tid=93)

TinyERP looks interesting also check it out here.  [http://www.tinyerp.org/](http://www.tinyerp.org/)

---

### Post by michaelzap on 2007-06-17
That's not bad, actually. I was looking for something plug-and-play, but this method has more flexibility than a standard program would. I may give this a shot while still looking for other options.

---

### Post by michaelzap on 2007-11-01
* BUMP! *

I still haven't found a satisfactory application to do what I need. I'm back to running Instant Invoice via Wine, which works OK but is not ideal (it's slightly buggy this way, and I'd prefer to use native software). Anyone else have another suggestion for a simple invoicing program?

Several times in the past I've given up looking for just the right software when it seemed like it didn't exist, and then I come across a forum post that points me to just the thing...

---

### Post by Berethorn on 2008-01-13
I'm needing the exact same thing right now, and I also have found nothing. GnuCash seems to lack the ability to email invoices direct from the program.  :(

---

### Post by Phrawm48 on 2008-01-25
I'm still exploring all its features, but the [SIZE=4][COLOR=RoyalBlue]**GnoTime Tracking Tool**[/COLOR][/SIZE], available in the Feisty repositories, seems to come reasonably close to fulfiling my need for a package that allows me to track time and generate invoices for that time...

Cheers & hope this helps
Ric
SFO

---

### Post by HermanAB on 2008-01-25
While you are at it, look at SQL-Ledger: [http://www.sql-ledger.org/](http://www.sql-ledger.org/)
and kmymoney.

Cheers,

Herman

---

### Post by michaelzap on 2008-01-25
GnoTime is cool (and I probably should use it to see how much I'm undercharging my clients), but most of the invoices that I generate are not based on hours worked but flat rates per project. Since it's totally time-based, it doesn't work well for me. I'd really like to find something more like Instant Invoice but for Linux.

---

### Post by Phrawm48 on 2008-01-25
[I]Since it's totally time-based, it doesn't work well for me. I'd really like to find something more like Instant Invoice but for Linux.
[/I]
I'm certainly no expert, and haven't used *GnoTime* long enough to have become any sort of advocate for it, but I think if you look at either a *Project*'s settings or a time *Interval* settings you'll find flat rate as a billing choice...(?)

Cheers & hope this helps,
Ric
SFO

---

### Post by Phrawm48 on 2008-01-25
> **HermanAB said:**
> While you are at it, look at SQL-Ledger: [http://www.sql-ledger.org/](http://www.sql-ledger.org/)and kmymoney. 

Thanks, but my peek at *sql-ledger*, which was admittedly very superficial, led me to conclude that it was a for-pay subscription offering(?)  The demos I found on the product's Web site were prominently identified as being function-impaired, and only sample documentation appeared to be available for free(?)

Moreover, after installing something called *sql-ledge*r from the Feisty repositories I couldn't figure out how to get the thing started, etc.

So I used Synaptic to completely remove *sql-ledger* and will wait until there's more, and more readily obtainable, information about it than currently seems to be the case.

Until that time, *GnoTime* seems to meet my needs...

Cheers & thanks,
Ric
SFO

---

### Post by michaelzap on 2008-01-25
> **Phrawm48 said:**
> [I]Since it's totally time-based, it doesn't work well for me. I'd really like to find something more like Instant Invoice but for Linux.
[/I]
I'm certainly no expert, and haven't used *GnoTime* long enough to have become any sort of advocate for it, but I think if you look at either a *Project*'s settings or a time *Interval* settings you'll find flat rate as a billing choice...(?)

Cheers & hope this helps,
Ric
SFO

Hmm... You're right. It took me a while to figure out how to get a line item to show up on anivoce with a flat fee, but it definitely can be done once you know how.

It still seems more like a timeclock than a list of invoices, but maybe I could make it work for me with a little bit more effort.

It hasn't convinced me to switch from Instant Invoice via Wine yet, though...

---


---
title: "Thinking about setting up a webserver"
date: 2007-05-20
forum: General Help
---

### Post by M$LOL on 2007-05-20
I'm thinking about setting up a webserver with the following specs:

Intel Pentium III 800Mhz
256MB RAM
20gig HDD
Some old AGP graphics card (64MB AFAIK)

These are all old components I have had lying around for a while.

I have a few questions.
1) My internet connection speed is 1MB/s. Is that fast enough to run a webserver?
2) Do I need to be worried about electricity consumption? I mean, it's going to be running 24/7, so is that a factor?
3) Should I go for the server edition of 6.06LTS or 7.04?
4) Security, I notice with my current installation of Apache on my desktop PC, there would be a load of configuring to be done if I was actually going to use it as a live webserver. Do I need to be worried about that for a dedicated server? 
5) Is there anything else I need to know before I start?

---

### Post by rich.bradshaw on 2007-05-20
sudo apt-get install apache2

then files are in /var/www that are online.

Try it... newest servers probably best if it's only for home use. If in business, LTS is probably better as less likely to have bugs.

I didn't do any  config before using mine, but I'm foolhardy like that!

---

### Post by M$LOL on 2007-05-20
Yeah, that's what I have on my desktop, but I don't want to leave that online all the time, hence the dedicated server. Another thing I'm curious about is a domain name, do I just specify an IP I want to use with my new server?

Thanks.

---


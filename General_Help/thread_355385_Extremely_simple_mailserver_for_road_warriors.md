---
title: "Extremely simple mailserver for road warriors"
date: 2007-02-07
forum: General Help
---

### Post by pauljwells on 2007-02-07
This is aimed at people who find themselves working from hotels or using other wifi hotspots, and finding that they can't send email because they can't access their home ISP mail server or whatever.

There is a lot of information out there about setting up postfix as an email server with all sorts of gizmos, but all I wanted was to have a simple mail server to be able to send mail directly from my laptop without neding to go through an ISP mail server.

Turns out to be very easy.

install postfix and procmail using synaptic

accept the defaults in the debconf setup for postfix

in your mail client set the outgoing server to 'localhost' on port 25

and you're done!

I came across this when I found there was a shareware app for mac OSX called 'Postfix Enabler'  which does this with a nice brushed metal GUI. I just worked out what it was doing and 'translated' the idea into Ubuntu...

Hope this is useful

---

### Post by dcstar on 2007-02-07
> **pauljwells said:**
> This is aimed at people who find themselves working from hotels or using other wifi hotspots, and finding that they can't send email because they can't access their home ISP mail server or whatever.
......
accept the defaults in the debconf setup for postfix

in your mail client set the outgoing server to 'localhost' on port 25

and you're done!
......

Not necessarily, there are a lot of mail servers that will not accept mail from a "localhost" system name, or a non-valid domain (as Spam prevention measures).

You will probably have to "tweak" the postfix config to use a different host name, and also put in a real domain.

---

### Post by pauljwells on 2007-02-07
Well, maybe. I've not had any problems so far, it just gives me an extra option and the idea was *not* to have to rely on any external domains etc

Mails sent this way don't show 'localhost' as the originating address, they show the address of whichever account I've selected when composing the mail.

I'm no expert on this, clearly, but this setup does seem to do what I expected and what I wanted.

---


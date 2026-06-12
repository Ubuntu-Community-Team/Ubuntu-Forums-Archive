---
title: "Basic Postfix?"
date: 2006-10-24
forum: General Help
---

### Post by hurrrtin on 2006-10-24
Does anyone know of a howto or guide on how to make a small mail server using postfix? I have tried a couple, and most of the ones I find want to setup some really elaborate schemes. I really only need it to support pop, smtp, and basic authentication. Maybe 3 or 4 accounts. Thanks for your help :)

---

### Post by kidders on 2006-10-24
Hi there,

Are you really sure you want POP?! There's not much to setting up postfix ... just install it and tweak your main.cf to your liking, and it should work for you straigh away. Many HOWTOs include stuff about spam & virus protection, but you can maybe ignore all that and just concentrate on the recommendations for configuring postfix (main.cf) itself.

---

### Post by hurrrtin on 2006-10-25
why not POP?

---

### Post by kidders on 2006-10-25
POP is an archaism from the early days of email, that people tend not to use any more ... unless of course there's a specific reason they need/want to. If you want, you could consider IMAP, which is a much more complete mail management protocol. I often use courier-imap-ssl.

There *are* some very good reasons for using POP, for instance...
[LIST]
[*]IMAP often becomes impractical if you are serving several million users with limited resources.
[*]Certain (dumb) devices, such as old mobile phones, won't talk IMAP, or don't support doing it securely.
[*]You really do not want people leaving mail on your server for extended periods.
[/LIST]
POP has *serious* flaws though, so I would avoid it if possible.

In terms of postfix, the most important thing to check is that your config doesn't let spammers use you as a launch-pad for DoS attacks, or other nasties. You should check this manually to be _100% sure_. If possible, you could even get a friend to do it for you, from outside your LAN... **Your mail server should reject mail that is both from & to non-local users.** I forgot to mention this before :-? 

There are a few other things to watch, but this is perhaps the most important.

---

### Post by TerryHowe on 2006-10-25
I'm looking for the same thing and I've been struggling with the authentication. for POP, IMAP and SMTP.  Whatever on POP being an anachronism, I want to run it.  Postfix is a lot nicer to config than sendmail, that is about all I've found out so far.

The most useful site I've found so far are

[http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour](http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour)

One hour my arse!

And this was pretty good on saslauthd, but I don't have it tied together yet.

[http://linux.about.com/od/ubusrv_doc/a/ubusg29t06.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg29t06.htm)

Simple PAM authentication would be fine with the old passwd and shadow file.  Any help out there?

---

### Post by viniosity on 2006-11-18
> **TerryHowe said:**
> 
The most useful site I've found so far are

[http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour](http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour)

One hour my arse!



I actually have it down to about 25 minutes now that the files are ready and just need to be unzipped.  I thought I was being generous with an hour.. ;)  Anyway, glad you found it helpful!

---


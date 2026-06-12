---
title: "Evolution IMAP doesn't mark read until exit (Gmail and others)"
date: 2007-11-02
forum: General Help
---

### Post by nbcthreat on 2007-11-02
Evolution's IMAP implementation doesn't mark read (and similar actions) until exiting the program. The effects Gmail and others like fastmail.

Many moons ago this problem seemed to be solved by using IMAPrev4 as the server type in Evolution. 

[http://ubuntuforums.org/showthread.php?t=24927](http://ubuntuforums.org/showthread.php?t=24927)

This option is no longer available in Evolution. The impact is that when IMAP (Gmail and others) messages are marked as read in evolution, that action is not immediately passed to the server. If you leave evolution open on multiple PCs none of your messages will be marked as read on the server, disabling a primary advantage of IMAP over POP.

Is there any way to make Evolution mark messages read real-time like it's done in Thunderbird? I'd just use Thunderbird, but I like the speed and integration of the latest version of Evolution in Ubuntu.

---

### Post by dcstar on 2007-11-02
> **nbcthreat said:**
> Evolution's IMAP implementation doesn't mark read (and similar actions) until exiting the program. The effects Gmail and others like fastmail.

Many moons ago this problem seemed to be solved by using IMAPrev4 as the server type in Evolution. 

[http://ubuntuforums.org/showthread.php?t=24927](http://ubuntuforums.org/showthread.php?t=24927)

This option is no longer available in Evolution. The impact is that when IMAP (Gmail and others) messages are marked as read in evolution, that action is not immediately passed to the server. If you leave evolution open on multiple PCs none of your messages will be marked as read on the server, disabling a primary advantage of IMAP over POP.

Is there any way to make Evolution mark messages read real-time like it's done in Thunderbird? I'd just use Thunderbird, but I like the speed and integration of the latest version of Evolution in Ubuntu.

Isn't there an option in IMAP account preferences to have immediate syncing (or whatever)?

---

### Post by nbcthreat on 2007-11-02
> **dcstar said:**
> Isn't there an option in IMAP account preferences to have immediate syncing (or whatever)?

Alas, all that does is synchronize the messages to your local hard drive.

---

### Post by malixor on 2007-11-09
I am frustrated with this same problem. Since Gmail added IMAP, I migrated Evolution and my Blackberry from POP to IMAP but there is no synching of read messages. Any solution or workaround or patch in the works? If this is a "feature", then I might as well move to Thunderbird.

---

### Post by nchase on 2007-12-11
I am annoyed by this problem too, but Thunderbird appears to have something like a memory leak on my system so I feel a bit stuck. Has anyone checked for bug reports on Launchpad?

---

### Post by nbcthreat on 2008-03-17
Bump. Any progress on this front? Folks playing with Hardy Heron, has this been fixed? Seems like a pretty major issue.

---

### Post by sephiros9883 on 2008-04-11
Yes, you can fix this behavior by going on your account preferences -> receiving options -> check "automatically synchronize remote mail locally" 

It should work with gmail. with hardy heron

---

### Post by _poiuyt_ on 2008-04-14
> Yes, you can fix this behavior by going on your account preferences -> receiving options -> check "automatically synchronize remote mail locally"

It should work with gmail. with hardy heron

You're wrong! :)
This doesn't fix the behavior but instead masks it. Actually, this option *downloads* the emails from your IMAP server to your workstation, which is not what you may want from an IMAP server.

Evolution is a selfish application: it considers it's alone in its world! Evolution should be committing the changes to the IMAP server every time something changes there like the other IMAP clients do (and I think like the rfc specifies it).

Evolution developers should fix this behavior...

---

### Post by kiddo on 2008-05-01
[http://bugzilla.gnome.org/show_bug.cgi?id=317755](http://bugzilla.gnome.org/show_bug.cgi?id=317755)

and possible duplicates:
[http://bugzilla.gnome.org/show_bug.cgi?id=321608](http://bugzilla.gnome.org/show_bug.cgi?id=321608)
[http://bugzilla.gnome.org/show_bug.cgi?id=433816](http://bugzilla.gnome.org/show_bug.cgi?id=433816)
[http://bugzilla.gnome.org/show_bug.cgi?id=459041](http://bugzilla.gnome.org/show_bug.cgi?id=459041)

---

### Post by QuintinvR on 2008-05-03
This seems related to an issue with evolution (my version 2.22 hardy heron) not synching upstream with google calendar.

I have the imap issue as well.

I looked through the bug reports that are listed and this looks like an old issue. Why has this not been resolved?

---

### Post by tom-ubuntu on 2008-06-02
Any news regarding this topic?

My GF and myself are having this issue aswell. Very annoying...

---

### Post by Nergar on 2008-06-03
I think I'll try thunderbird out, it is really annoying and what's worse, a lot of times I read my mail and close evolution for the day just to find out the next day that maybe 10% of the messages I read the day before weren't flagged as read mail.

If I could just get my google calendar to sync with the ubuntu calendar using thundebrid...

---

### Post by gsgleason on 2008-07-19
I just thought that I would dig this up to say this is still an issue in evolution in ubuntu 8.04.1

---


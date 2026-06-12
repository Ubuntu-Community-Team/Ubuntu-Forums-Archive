---
title: "Enabling rlogind on Ubuntu (14.04) desktop?"
date: 2015-03-26
forum: General Help
---

### Post by Ronald_F._Guilmett on 2015-03-26
Sorry.  This is kind-of a newbie question, I know, but I googled around awhile and could not find any good clear answer.

I have a couple of boxes on my local network that are well and truly behind a firewall.  One runs FreeBSD and (as of recently) the other one is running Ubuntu 14.04 desktop.  I need/want to be able to rlogin from the FreeBSD box to the Ubuntu box.  I know, I know.  Everybody is going to say "Just use ssh!", but I prefer not to.  It is unnecessarly complicated to set up for my purposes, and I don't need that level of security.  So I just want to enable rlogind and rshd on the Ubuntu box.  What are the exact steps necessary to do that?

(Note:  I have already done "apt-get install rsh-redone-server" and that seemed to work OK.  But I am guessing that I will also need to diddle some config file(s) for something like {x}inetd, no?  One online source told me to go fiddle some file underneath the /etc/xinetd.d directory, but there does not seem to be any such directory on my Ubuntu box. :-(

An additional follow-up question:   May I safely assume that rsh-redone-server should be used in preference to rsh-server these days?  Which one is considered the more stable of the two?

---

### Post by Ronald_F._Guilmett on 2015-03-26
Sorry.  Following up on myself... I need to say "***NEVERMIND***"

Just for laughs, I just tried to rlogin to my Ubuntu box and was totally shocked when it just simply worked.

I'm not kidding.  You could have knocked me over with a feather!  This was just totally surprising to me.

I am accustomed to FreeBSD where the presence of the rlogind/rshd executables is most definitely ***not*** sufficient to enable these servers, and where you most certainly ***do ***have to manually diddle /etc/inetd.conf before the relevant services are actually enabled.

Humm... I guess this raises a different sort of question... On the Ubuntu box, if, hypothetically, someday I want to ***disable ***rlogind and rshd, then what config file(s) would I need to diddle in order to do that?  (This will be educational for me.)

---


---
title: "Log all firewall traffic on desktop pc"
date: 2008-02-03
forum: General Help
---

### Post by Irihapeti on 2008-02-03
Yesterday I was researching a technical question, Googled it, clicked on one of the options and promptly got redirected to one of those "your computer is infected with spyware" sites. (By the way, you know you are going round in circles when the first item on the list is one of your own posts on the same topic!)

Now, of course, I was running Ubuntu, and I was using NoScript with Firefox 2.0.0.11, and the text on the site was all about needing to download an ActiveX control (which I know is for Windows and IE) and I didn't click on anything. So I doubt that anything's happened. But it's got me thinking. More so since I got an error this morning on startup that required a manual fsck. (Probably unrelated, but all the same...)

I'd like to have the option of logging everything that goes through (and gets stopped by) the firewall. That is, 

(1) packets that are dropped from outside 
(2) packets that get through from outside, and 
(3) packets that get through from the inside.    Maybe also
(4) packets that get dropped from the inside

And I'd like them to be logged to a separate file, instead of cluttering up syslog, kernel.log and messages.

Thus far, I've tried the following: 
Firestarter - logs type (1) only, to the above 3 files.
Guarddog - logs type (3) only, to the same files
ulogd - is supposed to divert the firewall log traffic to a separate file or database, but I can't get it to work.

By the way, I'm not running Apache or anything like that, and I'm on a dialup.

So - has anyone done anything like this?

---

### Post by Irihapeti on 2008-02-06
Yes, I eventually got what I wanted. It involved reading up on iptables and ulog, and doing some editing of guarddog's /etc/rc.firewall by hand. Very interesting, though rather time-consuming.

---


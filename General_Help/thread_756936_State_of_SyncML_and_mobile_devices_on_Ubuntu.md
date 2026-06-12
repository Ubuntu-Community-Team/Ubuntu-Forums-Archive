---
title: "State of SyncML and mobile devices on Ubuntu"
date: 2008-04-16
forum: General Help
---

### Post by Levander on 2008-04-16
I know there are a bunch of projects aiming to syncing mobile devices to Linux.  I've been searching Ubuntu Forums and there are several threads.  Thing is, they are all HOWTO's and the like.  I just need to know what software to use, and how "production ready" the software is.  

What I've just tried, and failed to do is use Funambol.  I want to sync my RAZR V3xx (which is supposed to be able to synch through SyncML) contacts with Thunderbird, initially.  I fail on that install pretty quickly.  I run the install, and then "sudo sh funambol.sh start" and try to open [http://localhost:8080/funambol](http://localhost:8080/funambol) in Firefox.  I get the "Firefox can not connect to this web site" message.  I looked around in the output of 'lsof -u' and it doesn't even look like funambol has any ports open.

I'm not the only one having this problem, and the funambol mailing list didn't even respond to it:

[http://sourceforge.net/mailarchive/message.php?msg_id=1203350430.13766.4.camel%40ruddha](http://sourceforge.net/mailarchive/message.php?msg_id=1203350430.13766.4.camel%40ruddha)

Are there any other packages besides Funambol that I should be looking into to synch my RAZR V3xx?  I've heard of opensync, but have also heard it's not ready for primetime.

My V3xx is GPMS (not CDMA).  So, I can't use any CDMA specific tools.

I guess I might switch to evolution if that is the only way, but don't want to.

I'm using Gutsy now, but am definitely interested in if this situation has gotten any better in Hardy.

I'm not interested in Windows Mobile, please keep that stuff out of this thread.

---


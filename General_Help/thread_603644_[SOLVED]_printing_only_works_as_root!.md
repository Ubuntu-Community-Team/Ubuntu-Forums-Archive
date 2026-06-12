---
title: "[SOLVED] printing only works as root!"
date: 2007-11-05
forum: General Help
---

### Post by phonky on 2007-11-05
Hi

Hope somebody can help, I'm getting mad at this...

I'm in an educational institution, everybody using Windows/Mac, I'm the only
on Linux, ubuntu gutsy.

I'd like to promote linux among the students, but I have this problem: I can't print....
That's a show-stopper for people new to linux.

I was using feisty before, and strangely enough I could print.
After long hours of debugging I found that when I start a process as root I can print! 

Well, at least the test page, and from firefox. Using eog with an image gives me an error on the printer, but at least the job arrives there...This might be something about queue type?
But one thing after the other...:-\"

In short, for example ```
sudo firefox myfile.html
``` --> I CAN PRINT
```
firefox myfile.html
``` --> I CANNOT PRINT (and cups tells me the job completed successfully, but no prints on the printer and no log....).

:confused:

To make things more complicated, I print over the network on a Canon iR 3100C,
via TCP/IP 9100, and we need job accounting activated to be able to print. Which
I have, otherwise I coulnd't print as root, obviously....I have the correct driver installed.

Any ideas? Guys, you would really help me quite a bit - and possibly inspire on or the other student to switch to ubuntu...:guitar:

---

### Post by phonky on 2007-11-08
This is a canon specific issue.

But at least I can print as my user now. 
But it costed me quite some sweat and time, I got it only by chance.

However, I can't print properly from all applications. If I want to print a jpg image from eog, for example, the printer reports an error. Any ideas? Is this a filter issue?

When I installed the canon drivers for my printer I got from another website
[http://forums.linux-foundation.org/read.php?25,3466](http://forums.linux-foundation.org/read.php?25,3466) 
a tool has been installed:

/usr/local/bin/cnjatool

with this I can configure job accounting for my user and then I can print. without this, only
root was able to print, because I discovered also this tool

/usr/local/bin/cngplp

with which I could configure the printer. That ran only for root though!

I don't know if I missed the documentation somewhere, but it seems this is all undocumented stuff, which is quite bad in my opinion...

---

### Post by soxs on 2007-11-08
i am not so familiar with cups... I do not have any printer atm..
sry, can not help you :-/

EDIT:
Did you allready search on launchpad.net for this bug?

---


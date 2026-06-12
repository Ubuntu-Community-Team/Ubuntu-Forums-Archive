---
title: "X crashes when I look at this webpage"
date: 2006-09-10
forum: General Help
---

### Post by zeus77 on 2006-09-10
When I look at [this [ubuntuforums.org]]("http://ubuntuforums.org/showthread.php?t=180647&page=16") paticular web page my whole machine hangs, and X dies.  Sometimes it kicks me back to the login screen, other times it completely hangs.  But it's definitely repeatable.  I'm running Gnome/Firefox with nvidia drivers (none of that Compiz/Xgl stuff).  Could someone with a similar setup please try just viewing that page (which is ironically just another forum post on this msg board) and letting me know the results?  You have to scroll down all the way to the bottom (and occasionally, I need to scoll back up, then back down once).  

This is bizarre... Dapper has been my primary OS for months, and I've never had a problem till now.

Thanks.


EDIT: This is a previously known [bug]("https://launchpad.net/distros/ubuntu/+bug/46034").  Sorry for posting needlessly...

---

### Post by gborzi on 2006-09-10
My setup is like yours (gnome+firefox+nvidia drivers, no xgl), so I opened that page with firefox. No problems at all.
Did you try to redirect firefox output to a file ?
> firefox &> error.firefox

---

### Post by zeus77 on 2006-09-10
Thanks, I'll give that a try.  Just to check: were you able to scroll down, and then back up successfully?  I can load the page fine... it's the scrolling that kills it.

---

### Post by gborzi on 2006-09-10
Yes, I scrolled the page down and up a few times, while crossing my fingers. Nothing happened.

---

### Post by raffytaffy on 2006-09-10
jesus...my whole OS crashed...what the hell is on that page..had to reboot computer...this is tottally bad

---

### Post by zeus77 on 2006-09-10
just talked with a couple people on IRC who were also able to reproduce the problem.  i guess i'll file a bug report. 

i'm trying to track down what it is about that page.  i disabled Javascript, and it still crashes.  tried loading it with Firefox for Windoze, and there were no problems...

---

### Post by tommcd on 2006-09-10
> **gborzi said:**
> My setup is like yours (gnome+firefox+nvidia drivers, no xgl), so I opened that page with firefox. No problems at all.
Did you try to redirect firefox output to a file ?
Yup, I can load the file, but scrolling crashes X! Weird!
Gborzi, how do you direct FF output to a file? Do you just type: firefox &> error.firefox in terminal?

---

### Post by tommcd on 2006-09-10
Yes, that is how you do it! I just did that, and X crashed again! But the error.firefox file is empty.

---

### Post by MacMan on 2006-09-10
> **tommcd said:**
> I just did that, and X crashed again!

FYI, that page killed my Xorg server, too.

No useful infos in /var/log/Xorg.0.log, nor in dmesg.

I have an Acer laptop with a AMD64 3000+ processor and a NVidia video chipset. I use Kubuntu 6.06 with kernel 2.6.15-26-k7.

That URL kills Xorg when viewed with Firefox, doesn't harm Konqueror.

The problem seems to be the very long text line in the first post in the page. There's a bug filed in Launchpad at this URL: [https://launchpad.net/distros/ubuntu/+bug/57914](https://launchpad.net/distros/ubuntu/+bug/57914) (Bug #57914)

I'm posting there, too: I hope they can do something about it.

*Edit*: I've found more infos browsing around. This seem to be a bug in the nvidia driver. A post in their forum suggests to turn off Hardware Acceleration in order to avoid it. See here: [http://www.nvnews.net/vbulletin/showthread.php?t=76493](http://www.nvnews.net/vbulletin/showthread.php?t=76493)

Ciao.
-- 
Mac

---

### Post by mejy on 2006-09-10
Although I don't get this error, I've noticed something strange about the source code of the page and have a troubleshooting ideas.

When viewing the source code of the page, for some reason the text inside the second code tag is not actually visible, but when you ctrl + f to find it, blank space is selected.

However, if you save the page to disk it is visible again.  This doesn't occur on any other pages that I know of.

If you save the page to disk the text is visible in the source code.

This seems to be an exploitable bug to me, and the source code is not visible on OS X either.  Perhaps this should be reported to Mozilla?

---

### Post by zeus77 on 2006-09-10
I just realized that this might be the same as [this bug]("https://launchpad.net/distros/ubuntu/+bug/46034").  If so, sorry for this needless, redundant thread.

Supposed to be fixed in an upcoming version of the nvidia driver...

---


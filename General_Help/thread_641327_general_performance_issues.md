---
title: "general performance issues"
date: 2007-12-15
forum: General Help
---

### Post by gammyhand on 2007-12-15
My computer spec is a64 3200+ with 1gb ram and radeon 9800 pro. The performance is diabolical compared to the last time I tried ubuntu (5.04). It takes about 5 seconds to load a link to my d: drive off the desktop (it is a NTFS formatted drive) and even simple app opening or opening an mp3/mpg file take a long time. What can I do to fix this?

Firefox performance is not great (scrolling is slow!) even though I have disabled ipv6 lookups.

Thanks.

---

### Post by gammyhand on 2007-12-16
I have done a bit more diagnosis.

Firefox scrolling causes processor usege to rocket and scrolling with mouse is very slow.

I can no longer play any mpg/avi/wmv files which played before I started installing software (think installing envy was the point they stopped).

Would tweak ubuntu do anything?

I am using amarok. Is this a massive resource hog?

I have desktop cube and desktop cube rotate turned on (with radeon 9800 pro). Some of the 3d effects have started juddering and XP could handle much more complex smoothly.

I know ubuntu should run quicker than this so what's going on? How do I diagnose what is making my machine shudder?

Memory use is:

user mem: 352.7 of 1011.4mb and used swap is 0.0 of 4.7gb - surely it should be using something?

My media drive reports as fuseblk (think that means ntfs formatting which it is) but that shouldn't matter as it's not the system drive.

Anything for it other than a re-install and monitor what I am installing to see when it starts slowing down again? Although it wasn't great from the beginning.

Spec is in the first post.

---

### Post by gammyhand on 2007-12-16
I had no idea this was such a rare problem!

---

### Post by Ashrael on 2007-12-16
I do not think your problem is rare..have you tried to look at your memory usage? firefox seems to have a memory hole somewhere, there are more posts about this problem.  And YES amarok is a massive resource hog! Make sure it doesn't load at startup, and check your memory usage... And about the swap not being used...get used to it! :lolflag: It only gets used when it's needed (hardly ever), unlike in windows! Did you install from scratch or did you upgrade from feisty?

Give us some output! dmesg, kernel log, syslog etc... Feed me Seymour!

"Wer ein Schöpfer sein will im Guten und Bösen, des musz ein Vernichter erst sein, und Werthe zerbrechen. Also gehört das höchste Böse zur höchsten Güte: diese aber ist die Schöpferische" *Friedrich Nietsze*

---

### Post by gammyhand on 2007-12-16
Thanks for the reply. I don't know how to get outputs sorry, what do I do?. It was a clean install. Just re-installed and starting again.

What would you recommend over amarok? It claims to only use 5% processing power on system monitor.

---

### Post by Ashrael on 2007-12-16
Hi, 

well you open up a terminal,  Applications/Accessories/Terminal.

type dmesg, for instance.. copy and paste the results in your reply.
For the log files, they are located usually in /var/log/....

you can open them and copy paste the results, if interesting..you know with errors...or warnings..

paste them in your next reply, and we'll see.

---

### Post by gammyhand on 2007-12-16
Thanks. I just reformatted and things seem a bit more healthy this time. Will give it an hour or two (and get everything installed again) and report back.

---

### Post by Ashrael on 2007-12-16
is cool...

---


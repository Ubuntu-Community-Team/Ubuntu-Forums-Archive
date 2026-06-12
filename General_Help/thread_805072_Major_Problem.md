---
title: "Major Problem"
date: 2008-05-23
forum: General Help
---

### Post by scottuss on 2008-05-23
Hi everyone. Not sure if this is the right place to post this as it seems to be with any Linux distro (although I really want to use Ubuntu!)

Basically whenever I run Ubuntu (or any other distro) on my laptop, after a few minutes I get a total white screen and I can do nothing but hard reset.

It can be upto an hour before it does it then BAM white screen of death!

I thought it was compiz or drivers to I used both non-restricted and restricted drivers, still happening. I tried compiz on and off, still happening. 

I installed PC-BSD (and Vista before that) and that works fine, no white screens so it's obviously something to do with the actual Linux Kernel.

Anyone got any ideas?

Thanks in advance!

---

### Post by m_kk on 2008-05-23
I had same problem with compiz. I solved it by replacing the xorg.conf file with my old one (hope you have yours backed up).

Here is what i did

press ctr+alt+f7 to enter terminal session.

login to terminal session and replace the xorg.conf file with the old one (eg sudo cp /path-to-old-conf /etc/X11/xorg.conf)

press ctr+alt+backspace to restart x server. 

Hope this will help.

---

### Post by Toadmund on 2008-05-23
If that fails you can check out post #28 here:
[http://ubuntuforums.org/showthread.php?t=420888&page=3]("http://ubuntuforums.org/showthread.php?t=420888&page=3")

---

### Post by scottuss on 2008-05-23
Toadmund you're a legend!

That thread had some information about something called PowerNow on my CPU that could be causing it. I'm not 100% sure yet but I think (fingers crossed) that the work-around on there has solved my problem!

Cheers buddy!

:guitar:

---

### Post by Toadmund on 2008-05-24
Hope that helps you, it was a major PITA for me.

---


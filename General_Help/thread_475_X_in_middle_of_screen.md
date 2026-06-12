---
title: "X in middle of screen"
date: 2004-10-13
forum: General Help
---

### Post by Geekboy on 2004-10-13
There's a X in the middle of my screen.  It looks like X-windows cursor. It's driving me crazy and seems to be the only issue I have with this Distro. How can I get rid of it.  Thanks.  :D

---

### Post by ubuntu-geek on 2004-10-13
This might solve it for you..

[http://lists.ubuntu.com/archives/ubuntu-users/2004-September/002102.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-September/002102.html)

---

### Post by Geekboy on 2004-10-13
It's still there.  I added Option" SWCursor on" to my XF86Config-4.  There was already a Device option listed.

I do notice that when I use some programs it does go away.  Very strange.

---

### Post by swirven on 2004-10-14
I have had the same problem. For me when I launch an application and then just click on the title bar it goes away.

---

### Post by daniels on 2004-10-14
The problem is generally solved by the SWCursor hack, but if you let us know exactly what video chipset you're using (output of lspci is handy), then we can solve the *real* problem. :)

---

### Post by Geekboy on 2004-10-14
I'm using a S3 Savage4.  It is also listed in my XF86Config-4.  If you need anymore info let me know.

---

### Post by cresonic on 2004-11-02
This is an old tread, so I asume the problem is solved,but I thought this was in order (I hate unfinished threads):

I had the same problem after installing ubuntu on my laptop.
The solution given in this thread:

[http://www.ubuntuforums.org/showthread.php?t=3018](http://www.ubuntuforums.org/showthread.php?t=3018)

... solved my problem.

(Actually the solution is given here: [http://www.ubuntulinux.org/support/documentation/faq/hwcursor](http://www.ubuntulinux.org/support/documentation/faq/hwcursor) )

---


---
title: "Freshly installed Xubuntu 14.04 &amp; 15.04 freeze"
date: 2015-08-08
forum: General Help
---

### Post by juanito2 on 2015-08-08
A year ago I bought a Lenovo B590 and installed Xubuntu 14.04. It worked like a charm.
Recently I got a ssd, put it in and installed the 15.04 on it. It worked very well. But during my configurating and installing of programs I noticed that the system froze completely when I accessed the so-called „file system“ within Thunar. So I installed 14.04 again. But the problem remained. I thought that it might have to do with the ssd, so I put back in the hdd I had used before and installed 14.04.3 on it. But all still freezes whenever I try to browse within Thunar through the file system (share, bin, media ...).
Freezing in my case means the following: the mouse stops to move, the music loops, the system doesn't respond to keyboard input. All left to do is a hard reset.

What can I do?

This is my first post here, and the info in this forum has already helped me on many occasions. Thank you for that.

---

### Post by kerry_s on 2015-08-08
the music loops ? have ya tried without the music ? lol

please give your specs. cpu,ram,graphics

---

### Post by juanito2 on 2015-08-08
Yes, it happens with and without music.

 I came a bit closer to the reason, I guess. I wondered why I never encountered this problem before during this last year, so I installed xubuntu 14.04 again but this time the oldest release.
It didn't freeze again even though I tried to trigger it.
Now I am going to update to the latest kernel and see what happens.

My specs are:

[TABLE]
[TR]
[TD="class: field"]Processor[/TD]
[TD="class: value"]2x Intel(R) Pentium(R) CPU 2020M @ 2.40GHz[/TD]
[/TR]
[TR]
[TD="class: field"]Memory[/TD]
[TD="class: value"]3656MB (517MB used)[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[/TR]
[/TABLE]
Intel Corporation 3rd Gen Core processor Graphics Controller

[TABLE]
[TR]
[/TR]
[/TABLE]

---

### Post by juanito2 on 2015-08-11
After days of trying this and that, I used Timeshift to create snapshots of my system before every update. That way I found out which package caused the constant freezing. It wasn't shipped with 14.04 but became later a part of it through updates. It seems to be part of 15.04.

[B]bcmwl-kernel-source Version 6.30.223.248+bdcom-0ubuntu0.1
[/B]
This is what caused my trouble. The driver of my network-card.

---


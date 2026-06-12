---
title: "Ubuntu 23.04 (Lunar) - Clicking Title Bars on Java apps doesnt Bring it to Foreground"
date: 2023-04-23
forum: General Help
---

### Post by denismc on 2023-04-23
So i have Ubuntu running in a VM.  I upgraded 20.04LTS to 22.04LTS, then to 22.10.  Everything has been working perfectly.

But as soon as i upgraded to 23.04 i noticed that all existing java apps and including running test code, that has a window frame with a title bar, when you click said title bar, to bring it to the foreground (assuming its behind another window), the app will continue to stay behind.  It's as if the app is not receiving any mouse event from the system when clicking the app's title bar.  I can click and drag the window just fine.  If i click on any other part that isnt the title bar, then the window gets focus and brings it to the foreground.

I've tested this out in Java 8, 13, 17, 20, and 21ea.  It's definitely not a java problem.  It's as if 23.04 is doing something different that is breaking the behavior of java apps.  No clue.

Is this a bug in 23.04 seeing as how this problem doesn't occur on any prior Ubuntu versions i tried?

---

### Post by yktoo on 2023-04-24
[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/2013216](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/2013216)

---

### Post by denismc on 2023-04-24
> **yktoo said:**
> [https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/2013216](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/2013216)

Thank you very much!

---

### Post by yktoo on 2023-05-19
This should reportedly be fixed in Gnome 44.1, which will [probably]("https://discourse.ubuntu.com/t/gnome-44-1/35647") be released towards end of May 2023.

---


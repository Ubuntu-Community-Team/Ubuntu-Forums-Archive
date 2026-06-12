---
title: "System and applications hogging up RAM after returning from suspend mode"
date: 2018-11-18
forum: General Help
---

### Post by gottaslay on 2018-11-18
[COLOR=#242729][FONT=Arial]I leave my PC on a lot when I leave and therefore learnt to use sleep/suspend mode. In Ubuntu 18.10 I've noticed that a lot of the applications running after returning from suspend mode have doubled and some tripled in their ram usage! Gnome-shell being a great example at a whopping 3.5GBs of ram usage. Chromium jumps up to multiple gigabytes and spotify goes up to a one whole gigabyte. How can i possibly troubleshoot this or at least make the effect not as bad?[/FONT][/COLOR]

---

### Post by TheFu on 2018-11-18
If you are a C/C++ programmer, then you can run the programs inside a memory management validation tool in debug mode to see if there are any lost pointers or unfreed memory areas.  For everyone else, capturing data that proves the claims in a way that each project team can use would be the first step, followed by reporting the issue to each project team.

And proving that it is specific to 18.10 only would be helpful.  I would test on 18.04 and 16.04 with Gnome3 DE to prove it didn't happen with those stacks.  There was a fairly bad memory leak in Gnome3 for 17.10.  I thought they'd fixed almost all of it by 18.04. [https://www.omgubuntu.co.uk/2018/03/gnome-shell-has-a-memory-leak-and-it-might-not-be-fixed-for-ubuntu-18-04-lts](https://www.omgubuntu.co.uk/2018/03/gnome-shell-has-a-memory-leak-and-it-might-not-be-fixed-for-ubuntu-18-04-lts)

---


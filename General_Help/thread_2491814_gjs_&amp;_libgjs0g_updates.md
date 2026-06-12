---
title: "gjs &amp; libgjs0g updates ?"
date: 2023-10-21
forum: General Help
---

### Post by sussexlad on 2023-10-21
Is it right that these two updates are still being kept back and if so, out of interest, why are they applied if not ready to be installed? Thanks.

---

### Post by MAFoElffen on 2023-10-21
The official reasoning for that is:
> 
If the dependencies have changed on one of the packages you currently have installed so that a new package must be installed to perform the upgrade, then that will be listed as "kept-back".

So it's like saying these updates need to be done but are pending on other things (that are not ready yet) to be in place first. It's like a kind of status warning that it's going to happen. LOL

---

### Post by sussexlad on 2023-10-22
Thanks for that. It was just that they've been hanging around for so long!

---

### Post by ian-weisser on 2023-10-22
gjs is in 22.04 is paused due to Phased Updates.

When the problem(s) are fixed, then update will continue.
Nothing is wrong. It's a feature to protect you from updates with bugs.

Reference: [https://ubuntu-archive-team.ubuntu.com/phased-updates.html](https://ubuntu-archive-team.ubuntu.com/phased-updates.html)

---

### Post by sussexlad on 2023-11-09
It was just that it's been hanging about for so long now,  I wondered if I'd missed something! Ta.

---

### Post by sussexlad on 2023-12-05
Can someone just confirm that these two are still outstanding? Thanks.

---

### Post by ian-weisser on 2023-12-05
See for yourself

```
apt policy <package_name>
```

Run for each package in question.

---

### Post by sussexlad on 2023-12-06
Thanks for that. I've learnt something new!

---

### Post by michael351 on 2024-01-04
For several months now gjs and libgjs0g have been held back and show "zero" percent phasing:

Policy
Please enter a name: gjs
gjs:
  [PHP]Installed: 1.72.2-0ubuntu2
  Candidate: 1.72.4-0ubuntu0.22.04.1
  Version table:
     1.72.4-0ubuntu0.22.04.1 500 (phased 0%)
        500 http://mirror.team-cymru.com/ubuntu jammy-updates/main amd64 Packages
 *** 1.72.2-0ubuntu2 100
        100 /var/lib/dpkg/status
     1.72.0-1 500
        500 http://mirror.team-cymru.com/ubuntu jammy/main amd64 Packages[/PHP]

I use Gnome desktop and wonder if there is some sort of problem with why these packages are not installing normally.

---

### Post by ian-weisser on 2024-01-04
They are not installing because they are phasing.

Something was indeed wrong...but not with your system. One or more problems with the upgraded packages was discovered, so the upgraded packages were temporarily reverted (phased 0%).

This usually means that the upgrade is still intended to happen, just delayed.

This is GOOD news: You didn't get a broken upgrade.

---


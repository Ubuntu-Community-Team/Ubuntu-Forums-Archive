---
title: "Fix for Heron firefox fonts"
date: 2008-05-04
forum: General Help
---

### Post by eap1935 on 2008-05-04
Default Firefox fonts were unreadable on my LCD monitor. Really terrible for small fonts with everything squished up together. I found that using synaptic to install msttcorefonts and x-ttcidfont-conf (already installed? - can't recall) helped a lot. Reconfigure fonts for X in a terminal with:

sudo dpkg-reconfigure x-ttcidfont-conf

I hope this helps someone else waste less time than I did finding a solution.

I'd really like to know what the Hardy Heron project managers were thinking when they let this slide. Surely this came up as an issue. This will certainly drive away new users.

---


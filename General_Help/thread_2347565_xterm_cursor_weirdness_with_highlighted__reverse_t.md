---
title: "xterm cursor weirdness with highlighted / reverse text"
date: 2016-12-26
forum: General Help
---

### Post by whitehat2k9 on 2016-12-26
This is a weird one. When opening an xterm on my Ubuntu 16.04.1 system, the cursor disappears whenever it's moved over highlighted / reversed text. It remains the same color as the foreground and completely blocks out the character it's on top of. See [https://imgur.com/a/wsmRN](https://imgur.com/a/wsmRN) for examples. On my CentOS 7 system which comes with a slightly older version of xterm (295 vs 322 on Ubuntu), the cursor color inverts properly. So far I've noticed this happening in alpine and vim; in bash/tcsh the cursor seems to work fine. The built-in terminal app and urxvt do not exhibit this problem at all.

Any ideas on how to fix this?

---


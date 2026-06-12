---
title: "aterm charset issues"
date: 2005-08-20
forum: General Help
---

### Post by skela on 2005-08-20
Certain things in aterm are a bit odd. Symbols like ' and - when reading manual pages and the likes show up has completely different symbols, like A with symbols on top.

Anybody know if I can fix this either by setting LANG settings, or writing something in my .Xresources file?

---

### Post by matthias_k on 2005-08-20
Are you non-US? I am, and I had similar problems, here's how I fixed it:

1.  Install the xfonts-transcoded packages (this gives you the means to display German umlauts and such).
2.  Edit your ~/.Xdefaults such that you supply a font string for aterm (or any other X app) which takes into account your locale. Since I'm living in Germany, that's what I did:
```

aterm*font: -misc-fixed-medium-r-*-*-*-120-100-100-*-*-iso10646-*

```
Just note the last portion, which sets the encoding.

Maybe this works for you, too. Don't forget to `xrdb -merge ~/.Xdefaults` or restart X.

Regards,
Matthias

---

### Post by skela on 2005-08-28
hey thx alot

---

### Post by matthias_k on 2005-09-01
No problem.

You may also want to try `dpkg-reconfigure console-data`

---

### Post by electronpusher on 2007-05-16
I live in the U.S. and I'm having the same problem- also when I try to run Midnight Commander in an aterm I get REALLY weird results- all the line drawing characters have "mutated"! Any advice for me- since I don't know German?

---

### Post by matthias_k on 2007-05-16
Since Ubuntu runs on Unicode by default, I'd recommend against using aterm. Use a unicode-capable terminal emulator instead, such as urxvt, the unicode version of rxvt. With urxvt your problems should be gone without further hassle.

---


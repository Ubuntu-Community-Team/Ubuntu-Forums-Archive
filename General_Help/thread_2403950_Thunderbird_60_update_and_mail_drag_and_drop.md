---
title: "Thunderbird 60 update and mail drag and drop"
date: 2018-10-18
forum: General Help
---

### Post by mikeymikec on 2018-10-18
I've been using Lubuntu and Thunderbird for a few months and I'm pretty sure I didn't have this problem before the update to version 60.  I also see this problem on an install I've just done of v60 on my test VM of the same version of Lubuntu as I primarily use:

Dragging and dropping mail looks different to what it used to, and it's kind of problematic because the graphics for indicating that I'm dragging and dropping constitute a long line on the same level horizontally as the pointer, making it impossible to see which folder I'm aiming at (especially if I d+d multiple mails).

I wondered what the graphic looked like with the older version so I downgraded TB on my test VM:

```
apt-cache show thunderbird | grep Version
sudo apt-get install thunderbird=1:52.7.0+build1-0ubuntu1
```

I'm slightly puzzled now because while the different graphic (which looks like a piece of paper diagonally right and below the pointer) is an improvement that allows me to aim properly, I don't think that's what it was on my own OS before the update! :)

Is this a situation like when I needed to install some gtk support stuff for LibreOffice so the UI fonts weren't terrible, or is this a thunderbird 60 ubuntu issue?

---

### Post by walts48 on 2018-10-18
See [https://bugzilla.mozilla.org/show_bug.cgi?id=1491261](https://bugzilla.mozilla.org/show_bug.cgi?id=1491261)

---

### Post by mikeymikec on 2018-10-18
thanks, I've subscribed to that bug report.

---

### Post by walts48 on 2018-10-19
There is a workaround in [https://bugzilla.mozilla.org/show_bug.cgi?id=1491261#c9](https://bugzilla.mozilla.org/show_bug.cgi?id=1491261#c9)

---


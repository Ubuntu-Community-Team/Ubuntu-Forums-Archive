---
title: "Firefox 3b5 keeps closing"
date: 2008-04-24
forum: General Help
---

### Post by MozBlue on 2008-04-24
Hi, running firefox 3b5 on Ubuntu 8.04 and the firefox window keeps closing for no appearent.

Only changes have been to install Flash 9

Any one know if this is an issue or of a way to stop this?

---

### Post by sizzam on 2008-05-28
You are probably running into a known issue with Flash 9 and PulseAudio.

I was having the same problem with Flash videos (YouTube mostly for me) crashing Firefox.  There is an open bug ticket for this here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

I corrected the problem for myself with steps gleaned from the bug ticket, details are in this post:

[http://ubuntuforums.org/showpost.php?p=5057137&postcount=5](http://ubuntuforums.org/showpost.php?p=5057137&postcount=5)

I have been crash-free since performing these steps.

---

### Post by michelux on 2008-05-28
I had the same problem with FF3B5.
The way I solved this problem was by upgrading Firefox to RC1, and now all is working fine again.

I used this instruction to upgrade:
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)

---


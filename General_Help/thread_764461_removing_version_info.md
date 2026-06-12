---
title: "removing version info"
date: 2008-04-23
forum: General Help
---

### Post by coolsinister on 2008-04-23
i have installed ubuntu7.10 desktop on my pc.
Now when i open terminal tty1 "ubuntu7.10" is displayed there as the very first line and then in the second line the command prompt is there. How can i remove this ubuntu7.10 from the first line and replace it with my own name.
Plz reply as soon as possible.

---

### Post by munkyeetr on 2008-04-24
**NOTE: I do not know if there are any hidden ramifications from making this change!** but if you edit the file **/etc/issue** you can change it. A reboot was required on my machine when I tried.

There is also the file **/etc/issue.net** which I believe will affect tty prompts for remote users in the same way.

Also, if you are interested, the file **/etc/motd** holds the text (message of the day) which appears after you have logged into a tty terminal.

---


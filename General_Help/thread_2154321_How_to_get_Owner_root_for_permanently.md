---
title: "How to get Owner root for permanently?"
date: 2013-06-14
forum: General Help
---

### Post by Tjkhan on 2013-06-14
In some places I can not paste files. In properties, it says Owner: root and I am not the owner, so I cannot change these permissions. How to get Owner root for permanently? [not for short time] What I have to do?

[ATTACH=CONFIG]243803[/ATTACH]

Thank you.

---

### Post by coffeecat on 2013-06-14
First, I think you need to read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It doesn't answer your question specifically, but does tell you what you need to know about the root account and how to gain root privileges temporarily. Please do not ask how to gain root privileges permanently - this is bad and unsafe practice.

But to your specific point. Why are you trying to change permissions on the root-owned /opt folder? Trying to change permissions on anything owned by root in a system folder, or a system folder, is a bad idea and might break your system. If you tell us exactly what you are trying to achieve with /opt, the someone can advise you how to go about it.

If the problem is simply that you want to copy/move files into /opt, then changing permissions on the /opt folder is not the way to go about it. The link above will help but, again, tell us what you are trying to do and someone will be able to help.

---

### Post by Tjkhan on 2013-06-14
Thanks for your quick answer. I just wanted to move lamp to opt. Thats all. any other way?

---

### Post by Tjkhan on 2013-06-14
got it by "gksudo nautilus". Thanks bro for making aware about opt. Thanks again

---


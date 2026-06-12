---
title: "Proxy Setting Dependent on Network"
date: 2007-09-06
forum: General Help
---

### Post by charbo on 2007-09-06
Hi,

I have a laptop with Feisty Fawn.
This is a work computer, but I sometimes use it at home as well.

At work, all internet connection has to go through proxy server, at home it doesn't.
So, I only need to use proxy setting when the computer is connected to the work network.  Unfortunately, I have to input the setting manually.

Is it possible to have the system automatically use a certain proxy setting depending on which network it is connected to?  In other words, does Feisty provide easy means to achieve this automatic switching of proxy setting dependent on the network it is connected to?

Not that I know how, but I can think of writing a daemon that checks the network connection every so often, and depending on the result rewriting the environment variable for http_proxy, but that is too complicated for me at this point.

If any of you know an easy solution, I really appreciate it.

Thank you for your attention,

Sadanori

---


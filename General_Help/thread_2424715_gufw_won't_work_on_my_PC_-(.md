---
title: "gufw won't work on my PC :-("
date: 2019-08-13
forum: General Help
---

### Post by hmiersch on 2019-08-13
Hi. 
I recently installed gufw on my PC (19.04, been using it for a while) but gufw REFUSES to work. When I launch it, I get the window asking me to enter the admin password which I do, and when I press return, that window disappears, and that's it. No gufw window, no error message, no nothing. I've checked out other forums, but so far nothing has convinced gufw to work.  How can I make it work?

Weirdly enough, gufw works ok on my MacBook pro (also 19.04, new install). Hmm...

---

### Post by norobro on 2019-08-13
I had this problem, also. Post #6 in the following link fixed it on my machine. [https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1592380](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1592380)

I found that page by running gufw from the command line and entering the last error output into a search engine: ```
/usr/bin/gufw-pkexec: line 13:  5115 Segmentation fault      (core dumped) python3 ${LOCATIONS[${i}]} $1
```

HTH

---

### Post by hmiersch on 2019-08-15
> **norobro said:**
> I had this problem, also. Post #6 in the following link fixed it on my machine. [https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1592380](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1592380)   i did that, and gufw showed me its window. so far so good. but the next time i started up, the old problem was back. apparently this solution is NOT permanent. is there a way to make it permanent?

---

### Post by norobro on 2019-08-15
One solution is to put the following statement in ~/.bashrc ```
xhost +si:localuser:root > /dev/null
```Don't know if there are any security implications though.

---

### Post by Rubi1200 on 2019-08-15
If you are logging in using Wayland, try switching to an Xorg session and see if the problem persists:
[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

### Post by hmiersch on 2019-08-19
> **norobro said:**
> One solution is to put the following statement in ~/.bashrc ```
xhost +si:localuser:root > /dev/null
```Don't know if there are any security implications though.  i tried that, but it didn't work :-(

---

### Post by hmiersch on 2019-08-24
> **hmiersch said:**
> i tried that, but it didn't work :-(  so, can anyone help me?

---

### Post by TheFu on 2019-08-24
Open a terminal.
run 
**sudo -H gufw**
Does it work?  Always remember the -H option, otherwise, it can be bad.
If not, what are the errors show?
In the meantime, you can use ufw or iptables.

---


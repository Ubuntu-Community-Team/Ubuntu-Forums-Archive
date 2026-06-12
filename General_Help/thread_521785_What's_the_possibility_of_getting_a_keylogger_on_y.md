---
title: "What's the possibility of getting a keylogger on your system?"
date: 2007-08-09
forum: General Help
---

### Post by Ub1476 on 2007-08-09
Hello, I would just like to know what the chances are of getting a keylogger/virus on your Linux system, which is in fact created for Linux as well (not Windows)?

Also, if there are possibilities, what kind of websites do this keyloggers happen to come from? And, will they only come to my system if I download a .deb package (or compile myself), or can they somehow sneak into my system without me knowing it? And what people create virus for Linux? Some sort of Linux haters or just people who wants a challenge?

I'm usually just browsing around at common Ubuntu places like Gnome-Look, or newspapers etc (with other words used by normal public humans).

I would like to have an answer from a veteran here, not just a guy who has used Linux for two months, and heard rumors (as I have as well).:-#

Thanks!

---

### Post by Ub1476 on 2007-08-09
.

---

### Post by hikaricore on 2007-08-09
Keyloggers and other such malicious applications are always possible when dealing with untrusted sources and random debian/ubuntu packages.
However chances are unless you or someone with access to your computer intentionally installs a keylogger you probably won't ever get one.  ^_^

Plus running Linux, you can easily see all running process with top, htop, ps; among other system utilities.
Unlike ***dows based system NO processes (or a very very select few) are hidden from you ever.

---

### Post by HermanAB on 2007-08-09
Don't worry about it.

I repair one or two hacked servers per year.  These are web servers which invariably gets hacked because some idiot defined a 4 character password.  I have never had a Unix desktop system hacked and I've been using Unix since about 1985.

Cheers,

Herman

---

### Post by Ub1476 on 2007-08-09
Thanks you for your both reply:D

I guess Synaptic is doing it's good work with most packages anyway.

---

### Post by HermanAB on 2007-08-09
The important things are:
a. Use long passwords.  Either 9 character random passwords or very long strings (like nursery rhymes).
b. Do not use an important password on an insecure protocol.  Insecure protocols include FTP, IMAP and POP.  These things send the username and password in plain text.
c. Do not run insecure protocols on a public server without paying a lot of attention to locking it down to specific IP addresses.  For example NFS and SMB.
d. Do not allow root login to SSH.
e. Apply net filter rate limiting to vulnerable protocols to prevent exhaustive password attacks. For example FTP and SSH.
f. Do not run a daemon if you do not need it.
g. In Perl scripts, use taint checks.
h. Do not put executable Apache scripts all over the place, keep them in cgi-bin.
i. Use public key encryption wherever possible.
j. Use iptables and tcpwrappers.
k. Ensure that anonymous FTP is read only.

Cheers,

Herman

---

### Post by Chappy7777 on 2007-08-11
> **HermanAB said:**
> The important things are:
a. Use long passwords.  Either 9 character random passwords or very long strings (like nursery rhymes).cheers,
Herman
=====================================
Herman, my head is hanging. I have a 4 letter password that is used for login and any time I need to do something in admin (unless it's only been a few minutes since I last typed it in).

Can you please tell me how to change my login/admin password?

Make it as ez as possible as I am fairly new at this.

---

### Post by wirelessmonkey on 2007-08-11
In a terminal type "passwd"

you will be asked to input your current password and your new password.  Tada!

---

### Post by hikaricore on 2007-08-12
> **wirelessmonkey said:**
> In a terminal type "passwd"

you will be asked to input your current password and your new password.  Tada!

This will also reflect on your "sudo" password, so there is no need to change anything else after doing it.  ^_^

If you for any reason have a root account active with an insecure password, you will need to login to it and do the same.

---


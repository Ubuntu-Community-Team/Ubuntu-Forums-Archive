---
title: "[SOLVED] Ubuntu 7.10 Security"
date: 2008-01-30
forum: General Help
---

### Post by sfink16 on 2008-01-30
Hello all,

I'm looking for security information on the Ubuntu 7.10 install I recently performed.  I reviewed the link below but it has limited information:

[http://ubuntuforums.org/showthread.php?t=234119](http://ubuntuforums.org/showthread.php?t=234119)

I'm familiar that one entry to a Linux system is through rootkit.  My Fedora 7 installation allowed me to add rootkit hunter.  How do I, or should I, install it on the Ubuntu OS?  

Other then keeping up to date with security patches, are there any other necessities such as firewalls and virus protections that I should install?

Steve

---

### Post by p_quarles on 2008-01-30
A lot of the basics of Linux security are discussed here:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

A home use desktop installation of Ubuntu is very secure. Your can certainly install rkhunter, build firewall rules, and harden the system, but it's not really necessary unless you are running any public services. Virus scanning is completely unnecessary, as there are no viruses currently circulating (the few there have been wouldn't do much damage, in any case, and they have been fully patched against). 

In my opinion, the biggest security hole in a Linux system is the web browser, but this is not currently a significant threat. Just be wary of phishing scams and so forth. 

And, of course, be careful whenever you do anything with root privileges. No operating system is secure against an attacker that tricks you into doing something you shouldn't.

---

### Post by sfink16 on 2008-01-30
Thanks p-quales, that's a great link, extremely informative!  Who would've thought to look in a Server thread/post for desktop answers as well.

---


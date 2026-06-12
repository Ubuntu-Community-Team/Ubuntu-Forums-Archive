---
title: "How immune is Linux to viruses ans spy ware?"
date: 2007-11-03
forum: General Help
---

### Post by MR.UNOWEN on 2007-11-03
I've been reading some threads about Viruses and Ubuntu and there's a few questions that came up.

1. "There are about 40 viruses for Linux"...  so are these viruses the kind that you have to be a complete idiot to install them on Ubuntu or of those viruses, can any install or run just by visiting a web site?
2. Wine seems to be semi immune, but it seems if you do a complete removal of Wine the /.wine still stays there. So if I were to need to start a fresh install of Wine what is sudo command to remove the whole director, or do I have to go file by file and folder by folder?

---

### Post by Zorael on 2007-11-03
(warning: bias)

As far as I understand, the viruses that did emerge gained "root" access to the system through security vulnerabilities - and these were promptly fixed shortly afterwards.

See, in a normal Linux session, you are just a user - you can run programs, write to your home folder, and save temporary files in /tmp. However, you *cannot* install programs, you *cannot* mess up system configuration files, only your own. This means that malign code - such as viruses or trojans - can't either. You need superuser or root privileges for that, which you only have when you start a command with sudo, gksu, kdesu or equavilent. Basically, when it asks for your password to proceed.

In a normal Windows session, you are an Administrator - you always have root privileges, by default. You can make a "user" account, but that's an opt-in feature.

To remember is that a virus is not some magical piece of software that can do things other programs can't; they're code, just like any media player.

This also means that a virus can hose your home folder, but your whole system? That would take your cooperation; possible through social engineering, I guess. :>

But sure, if you give root privileges to something, it can go and mess stuff up. It just takes much more effort than "accidently" clicking an attachment in Outlook, "happening" to visit the wrong page in Internet Explorer, etc. Windows, for all its good points, is a wreck when it comes to security, and I chuckle whenever I read articles on how important anti-virus software is "for PCs", and how they equate personal computers with Windows.


As for .wine in your home folder, it only contains your Wine settings and no libraries or executables (as far as I know). You may delete it if you wish, I guess. But looking at Wine from a virus perspective; sure, it could infect your Windows programs, but that's probably as far as it could go. Wine programs don't get root privileges either. They're run under the Wine layer, and the process has as much permissions as you as a user do.

---

### Post by Zorael on 2007-11-03
As an addition, if you only install software provided through the official Canonical-supported repositories, you are very, very safe.

If you download precompiled copies of "Free Linux Messenger, Get Friends Today:):):)" from random.suspicious.website.com, you're not as safe.

---

### Post by mahousaru on 2007-11-03
Using a computer is like having s*x, good practices go a long way.  Linux is built around the idea of multi users so the idea of maintaining a good level of security just too keep known users separated is fundamental, never mind unknown users.  If the system is well maintained; for example patched*, services not exposed willy nilly, sensible passwords etc, then the rest of it is up to the user being careful.  Even though something might only affect the user's space, it still would be disastrous if a confidential document in their home directory was accessed.  Unfortunately the OS can only provide a certain amount of immunity the rest is up to the user.

You can think of wine as a sandbox as long as you don't run it as root.  Then it can only damage areas you have rights to.

*Patching is of the utmost importance, for example lets say you run wu-ftpd as a normal user.  If it is of an older version (can't remember the numbers), then it can be subjected to a buffer over flow attack which will grant the attacker a root shell, even though the process was running as non root.  

The most important thing about security is to not think of single silver bullet, but to think of layers that are constantly decaying/changing and the final layer is the user.

---

### Post by Chymera on 2007-11-03
remember how much effort it took to install smth as trivial as xmms some years ago, when .debs and other self-installing packages were unheard of?.... thats the exact amount of effort you'd need to install a virus, if you are willing to go through that much trouble just so you can say that linux has security issues, be my guest! :P

---


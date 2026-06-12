---
title: "Recovering From a Compromised System"
date: 2007-12-06
forum: General Help
---

### Post by futureal on 2007-12-06
Hi,

I have a small server running at my house that I use for local web development and to host my own Subversion repository. I was rummaging through it today and came across some odd stuff in /var/www, namely a cgi.php file and a unixcod.tar.gz archive that looked like some type of port scanner.

I took a look in /etc/passwd and sure enough, somebody had added an account, a new home dir, and all sorts of scanning/attacking scripts. Looks like my box may have been used in some sort of a flooding attack among other things.

This is all running edgy.

As for what was running on the machine when it was compromised:

Apache 2
MySQL
Samba
Subversion
JIRA
OpenSSH (sshd)

Nothing else abnormal that I can think of. I assume they got in via ssh somehow but I am very curious as to how that happened or what I can do to prevent it in the future.

I haven't touched anything else on the box yet; what should I do next? I have some basic sysadmin skills (enough to get myself in trouble, apparently) but I am eager to learn how to defeat this and to restore my system.

I've found entries for this user in /etc/passwd, /etc/shadow, /etc/group and the dir in /home with a variety of hacker-ish tools.

If anybody can provide any insight, that'd be great. Or even point me to a FAQ or something if there is one related to Ubuntu, I didn't see one.

Thanks!

---

### Post by Vadi on 2007-12-06
Uh oh :(

I did some Googling, here's a linky: ([click]("http://www.ducea.com/2006/07/17/how-to-restore-a-hacked-linux-server/"))

And I was planning on setting up a server of my own too. If you'll find any good tips on how to protect it, share!

---

### Post by g2g591 on 2007-12-06
well I have to say the best thing to do is to just reinstall, this time with a different password (different username would help even more) . But if you can't afford to reinstall, add a new user, dellete the old and hacker added users, and install either (both is probabily better) chkrootkit or rkhunter and run them .

---

### Post by futureal on 2007-12-06
I have done some more digging on the stuff they uploaded, and have some theories as to how they got in and what happened.

First, the hacker left a messy trail, did not delete logs, and generally did not do much to cover his tracks. This tells me it is just some hobbyist and/or kid or whoever who was just looking for a safe place to scan from. He created a user called 'execut' and a /home/execut dir to live in. From there he uploaded a variety of port scanning and flooding tools.

One of the tools was a simple brute force ssh scanner, basically looping through a set of dictionary files and testing the passwords against common logins like root, mysql, ftp, and so on.

I originally set up this box around Christmas of last year, and recall that for the first couple weeks I had an empty install sitting there, and had used a rather generic word as an sudoer's password before locking the system down. Looking back through his .bash_history (which he also failed to remove) and comparing dates, it looks like he first logged on all the way back when my system was created, way back in January of '07, and had only been on a few times since, and each time just to execute a series of scans.

My guess is, given the appearance that this attacker really didn't have many skills beyond what you can easily read on IRC or Usenet, that he just bruteforced my system via ssh and logged right in untouched, set up his account, and because I didn't have any monitoring on this system (I rarely use it outside of svn) I never noticed.

Goes to show the importance of picking a strong password, for one, and for doing some regular monitoring of basic things.

I am reading through the link you posted and some others and seeing what else I can do to disinfect the box, though at this point I may rsync my svn repo to another box and then re-bang this one with feisty.

Thanks. :)

---

### Post by dbott67 on 2007-12-06
You may also want to install [DenyHosts]("http://ubuntuforums.org/showthread.php?t=450853") (check my sig below for details).

-Dave

---


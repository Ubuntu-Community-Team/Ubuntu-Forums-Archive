---
title: "Win Domain Ubu machine needs Admin rights and zsh for one domain user"
date: 2013-09-26
forum: General Help
---

### Post by jamesisin on 2013-09-26
I have built our first Ubuntu machine on our domain here at work.  It is a domain member and I've added a couple of domain groups and the primary domain user to the sudoers file.  Trouble is not everything uses sudo for elevation.

Software center only acknowledges accounts marked as Administrator.  Normally if you go into Users you can change the drop-down from Standard to Administrator.  However, for domain users that isn't a drop-down.  It's just the word Standard.  How can I change that?

[S]Also, this user prefers zsh which is now installed in /usr/bin/zsh.  Normally chsh would manage this but since the user is a domain user they don't have an entry in the usual location.  I can see they are set to use bash by using getent passwd | grep USERNAME.  How can I change that?[/S]

That's it.  Other than those two items ([S]and configuring Empathy to connect to our Cisco Jabber server[/S]) all is well.

Thanks in advance for your help.

(For Jabber I switched to Pidgin which worked.  Not sure why Empathy isn't.)

---

### Post by jamesisin on 2013-09-26
Ok, I found this and was able to sort out how to fix the LikeWise zsh problem:

[http://ubuntuforums.org/showthread.php?t=1560440](http://ubuntuforums.org/showthread.php?t=1560440)

(Note: Ignore the paths in the explanation; LW does not live under /opt/.  I just used the commands as they were (somewhere) in my path.)

---

### Post by jamesisin on 2013-09-30
Anyone have a clue on the Software Center authentication problem?

---


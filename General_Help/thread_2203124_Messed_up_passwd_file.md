---
title: "Messed up passwd file"
date: 2014-02-01
forum: General Help
---

### Post by NorthBridge4839 on 2014-02-01
I was trying to change my default shell and I went to the passwd file like a tard. I messed something up and now I can't log into my main user account or the root account. There's still the old temp file in /etc/passwd~ that holds the unbroken passwd file BUT... I don't have anything that can move it back to /etc/passwd to make everything work. I have kernel 3.11.0 and a bunch of web shells (r57,c99, and c100) but that kernel is too up to date to use any root exploits I've found. The shell user is www-data and I'm not sure what permissions it has. Is there any way for a non-root user to fix the password file? Or a way I could get it to default to the old passwd file or something? Or some way I could gain root so that I could just move it myself?

It's really crappy because this is my server at home that's 150 miles away. I could fix it easily if I was there but all I have is this web shell.

---

### Post by TheFu on 2014-02-01
Boot off any live CD, mount the partition with /etc on it, use root to move "good" version file in to the correct filename.
With physical access and NO encryption, any Linux box can be owned from a flash drive or boot CD or .. 

You can also use the chroot command after you get a root shell in the livecd version and run **passwd {userid}** to change the password for any user of the system.

Physical access means total control.

---

### Post by PotatoHead007 on 2014-02-01
Also, without the LiveCD, just go into recovery mode from grub. Select root(drops into root terminal), and run the **passwd {userid} **command like TheFu said.

---

### Post by Dave_L on 2014-02-02
TheFu &  PotatoHead007: He needs to fix this problem remotely, without physical access.

---

### Post by TheFu on 2014-02-02
> **Dave_L said:**
> TheFu &  PotatoHead007: He needs to fix this problem remotely, without physical access.

I cannot post how to hack a box remotely. Nexxus toolkit?
Today is Sunday ... long drive?

I do appreciate the [Idiocracy]("http://www.imdb.com/title/tt0387808/") reference.

In the future, setting up an ssh-key-only remote access account that is root-equiv might be a good idea.  I do backups using the 2nd account, as an example. This doesn't help with the current issue.

---

### Post by PotatoHead007 on 2014-02-02
> **Dave_L said:**
> TheFu &  PotatoHead007: He needs to fix this problem remotely, without physical access.

Woah ok..... that is different. Especially if the PC in question is not online. I have no idea how to do this, but if the PC is in a network, you should be able to do it with some help.

---

### Post by NorthBridge4839 on 2014-02-02
I talked my dad through helping me enable root login to allow me to change the passwd file back. Turns out the root login wasn't working because it wasn't enabled. Just got him to turn enablerootlogin to yes in the sshd and restart the service. Boom, edit the passwd file and we're back in buisness.

---

### Post by Dave_L on 2014-02-02
It's good to hear you resolved the problem.

How to mark your thread as SOLVED
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


---
title: "auto sudo after login"
date: 2013-11-12
forum: General Help
---

### Post by SeaKing on 2013-11-12
Hi,

my intention is to create personalized root accounts, which  means, I have one or more users which should have dedicated user  accounts (because of ssh key) but behave as a root user. 
What I already did is:
-create a dedicated group linux_admins
-create a user and made them member of this group
-modified /etc/sudoers : ```
%linux_admins ALL = (ALL) NOPASSWD: ALL
```
-added ```
sudo su
``` to the end of /etc/bash.bashrc (no ~/.bashrc)

The  result was: when I logged in I gained instant root privileges but when I  was logging out via CTL+D the session wasn't quit but I logged of root  und became the "normal" user.

So is there an other, maybe better way, to orginize such "personalized root accounts"?

---

### Post by deadflowr on 2013-11-12
> [COLOR=#000000]The result was: when I logged in I gained instant root privileges but when I was logging out via CTL+D the session wasn't quit but I logged of root und became the "normal" user.[/COLOR]

You logged in as a normal user, you switched to root quickly thereafter.
All you did with crtl +D was exit the root session.
But you were still logged in as the normal user.

What you'd want is to somehow kill the normal users session.

---

### Post by Lars Noodén on 2013-11-12
One way to get it so that ctrl-d or exit drops you from root and logs out would be to use exec.

```

exec sudo su -l

```

exec is one of the [Builtins](http://manpages.ubuntu.com/manpages/trusty/en/man1/sh.1posix.html) in dash and bash.

---

### Post by jamesisin on 2013-11-12
It might help to describe your goal, help us understand why you (or anyone) would want to automatically engage root privs for multiple users.  This seems like a dangerous prospect.

---

### Post by aromo2 on 2013-11-12
Without understanding the reason behind your question and ASSUMING THAT SECURITY IS NOT AN ISSUE, I dare to suggest to make all users members of the root group.

That way there is no need to sudo and each user would have its own history (as opposed to a shared root's history if everybody did sudo).

---

### Post by SeaKing on 2013-11-12
> ASSUMING THAT SECURITY IS NOT AN ISSUE

Why should it not be an issue?
If I have 5 different people loggin in with "ssh root@host", I have serveral problems e.g. who is currently logged in? root - but "which" root or who was logged in when something happend? root - but "which" root. Thinking of no root login via ssh. And the overall idea of this is all about laziness ;) If I use an administrative account (I barely need "normal user rights" or have just service user with no login shell) and I log in, it's more efficient to be root instead of gaining root right first. And yes seperated bash histories is an issue, but currently I unfortunately did not bare this in mind.

---

### Post by jamesisin on 2013-11-12
Never log in as root.  That in and of itself is a security concern.  This is why sudo exists in the first place.  I never sign into any of my Ubuntu systems as root.

---

### Post by SeaKing on 2013-11-13
Thats my intention ;)
So to make it clear what's my aim:
-a dedicated admin group -> to make no real use of the traditional root account
-if one of the members loggs inthey should be "auto promoted" to root -> no sudo -i or sudo su -l
-maintain a bash_history for each user e.b. /root/.bash_history-username

---

### Post by JKyleOKC on 2013-11-13
Looks as if you have a LOT of rewriting to do, starting with the shell programs, then the file systems, and finally going into the kernel. Your second and third goals, as listed, are simply not possible with existing system software.

If you do this, please make sure your system is never connected to the internet. We don't need more volunteers for the netbot army. You're perfectly free to set up your own system any way you desire, but please do not inflict the result on the rest of us!

---

### Post by coffeecat on 2013-11-13
Wise words, as always, from  JkyleOKC:

> **JKyleOKC said:**
> If you do this, please make sure your system is never connected to the internet. We don't need more volunteers for the netbot army. You're perfectly free to set up your own system any way you desire, but please do not inflict the result on the rest of us!

@SeaKing, the most significant thing you've said is:

> **SeaKing said:**
>  And the overall idea of this is all about laziness ;)

My duty is to consider the very many inexperienced Ubuntu users, both forum members and unregistered guests, who use these forums as an information resource and who might be tempted to unwittingly wreck their systems on the basis of things posted to a thread such as this.

Although our line in the sand is different from what you are trying to achieve &#8211; in fact what you are trying to achieve might be considered even more imprudent &#8211; you need to understand the principles by which we moderate threads about root access:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

A side issue is that sudo su itself has the potential to cause problems, which is explained here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I'll leave it to you to find the recommended way of starting a root shell &#8211; reading through that wiki page might be useful to you.

I'll end with one personal thought which does not represent forum policy, although I suspect other forum staff members might agree with me. If you have users too lazy to make a few keystrokes in order to gain root access for ssh, then you have users too lazy to trust with root privileges. 

***Thread closed.***

---


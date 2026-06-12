---
title: "sudo problem"
date: 2007-09-26
forum: General Help
---

### Post by Boule on 2007-09-26
I just installed feisty, and the sudo password doesn't work. It works fine when I login with my username, but when I try a command with sudo, and I enter the same password, it says "incorrrect".

Any idea why, and how to fix it ?

---

### Post by dabl on 2007-09-26
> **Boule said:**
> 

I just installed feisty, and the sudo password doesn't work.



That is VERY weird for a brand new installation, and suggests to me that something went wrong during the process -- this should not happen!

> 

Any idea why, and how to fix it ?

There is a special file named /etc/sudoers, and a special editor named visudo that is only for this purpose.  Here's more:

[http://ubuntuforums.org/archive/index.php/t-14366.html](http://ubuntuforums.org/archive/index.php/t-14366.html)

But I personally would be thinking "reinstall" -- just because this is such a suspicious situation that I would be worried about other elements of the installation having gone wrong.

Hope the helps!  :)


EDIT:  I'm assuming you know (and took into consideration) that Linux is case-sensitive, i.e. "DABL" is different than "dabl" to Ubuntu.  ;-)

---

### Post by rsambuca on 2007-09-26
Your sudo password isn't necessarily the same as your user password, unless you intentionally made them the same (which you shouldn't).

---

### Post by bulldog060 on 2007-09-26
> **rsambuca said:**
> Your sudo password isn't necessarily the same as your user password, unless you intentionally made them the same (which you shouldn't).

What OS do you use?  .... On my Dapper and Fiesty boxes the sudo password is your login password, just like it is on my OS X boxes, my Solaris system, and the 3 other linux distros I use.


and they should probably update the sudo man page:
"       sudo allows a permitted user to execute a command as the superuser or another user, as specified in the
       sudoers file.  The real and effective uid and gid are set to match those of the target user as specified
       in the passwd file and the group vector is initialized based on the group file (unless the -P option was
       specified).  If the invoking user is root or if the target user is the same as the invoking user, no pass&#8208;
       word is required.  Otherwise, sudo requires that users authenticate themselves with a password by default
       (NOTE: in the default configuration this is the user’s password, not the root password).  Once a user has
       been authenticated, a timestamp is updated and the user may then use sudo without a password for a short
       period of time (15 minutes unless overridden in sudoers)."

---

### Post by rsambuca on 2007-09-26
Yeah, sorry Bulldog!  I must be sleeping at the wheel this morning.  I was writing from my gentoo box where I have separate root and user logins, each with a different password.  

Ooops.:oops:

---

### Post by bulldog060 on 2007-09-26
heh, don't worry it was early and i know all to well what gentoo does to your brain :P ... i just had to call that out so the new people don't get seriously confused.

im just glad you didn't say to re-emerge sudo

~ron

---

### Post by bodhi.zazen on 2007-09-26
> **Boule said:**
> I just installed feisty, and the sudo password doesn't work. It works fine when I login with my username, but when I try a command with sudo, and I enter the same password, it says "incorrrect".

Any idea why, and how to fix it ?

sudo uses the same password you use to log in.

You need to be a member of the admin group to use sudo.

You can boot to recovery mode and fix your group membership without reinstalling if needed.

---


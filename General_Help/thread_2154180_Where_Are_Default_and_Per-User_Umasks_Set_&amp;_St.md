---
title: "Where Are Default and Per-User Umasks Set &amp; Stored?"
date: 2013-06-13
forum: General Help
---

### Post by Iggy64 on 2013-06-13
A relatively new convert to GNU/Linux, I am trying to learn about file  permissions.  (I am running 12.04 with e17 desktop - Bodhi.)  I seem to be at an impasse in understanding how to set the  default and per-user umasks.  I have read and explored for many hours,  without a successful resolution.

Various sources say that the default umask (which pertains to all users) is stored in /etc/profile.  But my /etc/profile says this:
# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.

So I looked in /etc/login.defs, and I found:
UMASK        022

The literature on the PAM umask module says that:
The PAM module tries to get the umask value from the following places in the following order: 
umask= argument 
umask= entry of the users GECOS field 
pri= entry of the users GECOS field 
ulimit= entry of the users GECOS field 
UMASK= entry from /etc/default/login 
UMASK entry from /etc/login.defs 

Since I couldn't find any umask declarations in any of the other options, I'm concluding that the above
UMASK         022
in /etc/login.defs
is being read by the PAM module as the default umask.

However, when I run:

> umask
it returns
002

So, it appears that my per-user umask is 002 (and not the default 022).  So where is this stored?

According to what I have read, this should be in ~/.profile
However, I find no reference to umask in there.
Nor do I find a umask declaration in ~/.bashrc or the various other places people have suggested.

I need help big time.

Where should I expect to find the default umask (for all users)?
Where should I find the per-user umask?
If these are not editable text files, what is the proper way to modify these masks?

---

### Post by Iggy64 on 2013-06-14
I found help elsewhere, and believe I have my answers.  I figured I'd share here in case someone else might have the same questions.

In my Bodhi Linux distro based on Ubuntu 12.04, the default global umask is stored in 
/etc/login.defs

where the following declarations are found

UMASK 022

and

USERGROUPS_ENAB yes.

The comments in the file say that
# If USERGROUPS_ENAB is set to "yes", that will modify this UMASK default value
# for private user groups, i. e. the uid is the same as gid, and username is
# the same as the primary group name: for these, the user permissions will be
# used as group permissions, e. g. 022 will become 002.

Therefore, the default umask is declare as 022, but it becomes 002.  This is why the system told me my umask was 002.  It was simply showing me that I was under the default.

I learned further that I can provide myself a persistent per-user umask by adding the line

umask 0nnn 

to the end of my ~/.bashrc
(where 0nnn is the octal value for the mask I want).  This change takes effect after logging out and back in, so that .bashrc gets run.

---


---
title: "Renaming a user account"
date: 2008-04-28
forum: General Help
---

### Post by toupeiro on 2008-04-28
A somewhat general support practice in UNIX or Linux can be to rename a user account.  In the past, this has not been overly difficult in any regard at all, simply update the passwd, shadow and groups file.  I've noticed that there doesn't appear to be any GUI mechanism in ubuntu to do this.  Even in super user mode, the user ID field remains greyed out, so the only option is to manually do it.  (To clarify, I am not talking about changing a UID number, but the user ID associated with it.)

While this worked for general login purposes as expected, there were some other things that were troubling:

1. GDM retained the old user name information, even though it would pass the new one and prompt me for the password (using an icon oriented login screen)

and

2.  Sudo or gksudo has completely lost its brain.

an unmodified sudoers file in ubuntu is pointing to an admin user group in /etc/group to control sudo access.  Therefore, changing my entries in the groups file should have sufficed for all the execute permissions sudo needed.  This, however, is not the case.  There are no specific errors that were displayed, it just did nothing. (e.g. sudo apt-get update prompts me for my password, then does nothing once its given.)

Has anyone else encountered these problems?  If so, how did you resolve them?

Many Thanks,

T.

---

### Post by toupeiro on 2008-04-30
Quick update:

I fixed one my two problems.  The fix was apparently user error (which takes the black magic aspect out of the picture)  Apparently when I was editing the group file with vi I did a :q! and not a :wq! because the substitution command I passed through vi did not hold, so the group file did not correlate with the passwd/shadow file.  Hence, Sudo didn't lose it's brain, I just gave it an accidental lobotomy...  ](*,)

The second problem relating to GDM still stands.  I guess I could start blowing away some .files and .directories in my home but I would rather go at it with a little more finesse than that.  I have literally hundreds of .files and .directories unfortunately, so if anyone has done this and can help me isolate it a bit, that would be much appreciated!

Thanks again,

T.

---


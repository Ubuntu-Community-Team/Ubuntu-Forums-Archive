---
title: "HELP! Changed root password, locked out"
date: 2007-10-04
forum: General Help
---

### Post by mollison on 2007-10-04
I was logged into my server remotely as root, using SSH. (Technically I was also ssh'ing through a remote machine.)

I did the following command:
usermod -p newpass root

I then immediately ended the SSH session.

I was expecting to then be able to log in with:
user = root
password = newpass

However, neither the former nor the new password works!!!!

I haven't tried to log into the machine locally, I might try that tomorrow (it's in my office). But for now... does anybody have any idea how this could happen? Or if I can get back in remotely?

I am sure I am perfectly recounting the sequence of events, and that I am typing everything correctly, etc. ... I saved what was in my terminal, so there's no question about my memory being faulty here.

---

### Post by mollison on 2007-10-04
Well, since nobody responded... :confused:

log in as a superuser, then do sudo su, type in your superuser password, and you're root.

---

### Post by cmost on 2007-10-04
If you knew the answer, then why did you ask for help?  What you did is exactly what I would have suggested.  Incidently, that's why Ubuntu's little sudo business causes it to be an extremely insecure OS by default.

---

### Post by mollison on 2007-10-04
> **cmost said:**
> If you knew the answer, then why did you ask for help?  What you did is exactly what I would have suggested.  Incidently, that's why Ubuntu's little sudo business causes it to be an extremely insecure OS by default.

Obviously, I didn't know the answer when I asked. I didn't do my follow-up post until 15 hours after I asked the question.

What you said is equivalent to me saying, "If you would have suggested that, why DIDN'T you?"

---


---
title: "User name convention"
date: 2008-04-17
forum: General Help
---

### Post by cprofitt on 2008-04-17
I am curious why Ubuntu/Debian do not allow user names such as:
 
firstname.lastname
firstname_lastname
 
I am able to use these conventions in openSUSE and Fedora, but I assume there is a reason Ubuntu does not allow these and I have just not been able to find the reason on-line.
 
Any information would be most appreciated.

---

### Post by andrewc6l on 2008-04-17
I don't know, but a guess would be for utilities like chown, which allow

  chown user.group filename

which could have unintended consequences if a user named joe.root or joe.wheel came along.

---

### Post by russo.mic on 2008-04-18
Good question,  periods in front of filenames hid files,  something with that?

---

### Post by warp99 on 2008-04-18
From the 'man adduser.conf' pages:
>  NAME_REGEX
              User names are checked against this regular expression.  If  the
              name  doesn’t match this regexp, user creation is refused unless
              --force-badname is set.  With  --force-badname  set,  only  weak
              checks  are performed. The default is the most conservative ^[a-
              z][-a-z0-9]*$.

You can set them, but you need to use --force-badname when doing so with 'adduser' or change the expression in 'adduser.conf'

---

### Post by cprofitt on 2008-04-18
Warp:

I saw the man page, but was more curious as to why the choice was made in Ubuntu/Debian vs. Fedora/openSUSE.

Andrew:

How would chown cause issues?

russo:

In this case the '.' is in the middle though and not at the end.

---

### Post by andrewc6l on 2008-04-28
I suspect chown wouldn't be able to distinguish between
  <user first name>.<user last name>
and
  <user name>.<group name>

Haven't tried it, so I may be wrong - but it sounds like it would be a good thing to avoid. At the very least there's ambiguity if a user has the same last name as a group name.

---


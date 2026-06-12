---
title: "Useradd  -M creates home directory"
date: 2021-03-24
forum: General Help
---

### Post by skybird182 on 2021-03-24
It appears the -M / --no-create-home switch does not prevent the creation of the home directory as can be seen in the command line text below.
The useradd man page clearly states the following:
 -M, --no-create-home Do not create the user's home directory, even if the system wide setting from /etc/login.defs (CREATE_HOME) is set to yes.

Is this a bug ? Am I missing something ? I am using xubuntu 20.04 LTS

In the /etc/login.defs I could only find CREATE_HOME and not DEFAULT_HOME.

svr@svr-2004:~$ sudo useradd -M test_acct
svr@svr-2004:~$ grep test_acct /etc/passwd
test_acct:1004:1004::/**home/test_acct**:/bin/sh
svr@svr-2004:~$ 

from /etc/logins.def
#
# Should login be allowed if we can't cd to the home directory?
# Default in no.
#
DEFAULT_HOME    yes

---

### Post by spjackson on 2021-03-25
What you show is that the home directory field is set in /etc/passwd, not that the home directory is actually created. Is it created? It isn't for me. If what you are wanting is for the home directory field in /etc/passwd to be empty, then I'm not sure that it is possible to do that.

---

### Post by TheFu on 2021-03-25
useradd doesn't create a HOME by default, so the -M option shouldn't be needed if that is your goal.  Not working with the -M **is** a bug.
I can't reproduce it here.  Both work as expected - no directory was created.

Perhaps there is confusion between **useradd** and **adduser**?  I always have to look up which does what I want. 99% of the time, I want adduser. adduser on Ubuntu does the extra stuff we usually want, like creating a user HOME, copying skel files into it, while also creating a new userid.  Of course, if you are doing LDAP or NIS+ directories for users on NFS HOMEs, then you'd want to not do either and just add them to the LDAP system and manually create the NFS location for their HOME, then copy the skel files into that location.

---

### Post by skybird182 on 2021-03-25
I found out that the file is not created after much investigation. To a new user that is frustrating but a good learning experience.

---

### Post by TheFu on 2021-03-25
> **skybird182 said:**
> I found out that the file is not created after much investigation. To a new user that is frustrating but a good learning experience.

File?  Don't you mean directory?  Or are you speaking from the "on Unix everything is a file" perspective?

People coming from non-Unix OSes often find thousands of things frustrating. All that knowledge and skill from "other OS" doesn't apply.  Let me assure you, it goes the other way too.
Let me also assure you that there is almost always a very good reason for the behavior seen. We may not agree with the reasoning and some newer projects try to go out of their way to break things that worked 20+ yrs for unknown reasons, but that's just a few, daemon control systems and 1 new packaging system doing that that IME.

---

### Post by HermanAB on 2021-03-26
Note that useradd is the actual utility, whereas adduser is a script that invokes useradd and also does a bunch of extra stuff.  The adduser script is specially made for the distribution and is usually what you should use.

---


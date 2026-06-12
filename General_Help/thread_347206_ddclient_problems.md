---
title: "ddclient problems"
date: 2007-01-26
forum: General Help
---

### Post by Pobega on 2007-01-26
I'm trying to use ddclient, so I go about installing it the manual way (As opposed to from the repos), and for some reason I get this error:> pobega@ackbar:~$ /usr/sbin/ddclient -daemon 300 -syslog
WARNING:  file /etc/ddclient/ddclient.conf: file /etc/ddclient/ddclient.conf must be accessible only by its owner (fixed).
Which is weird, because I did:
> chown pobega:pobega /etc/ddclient/ddclient.conf
chmod 777 /etc/ddclient/ddclient.conf
And I still get that error.

---

### Post by dcstar on 2007-01-27
> **Pobega said:**
> I'm trying to use ddclient, so I go about installing it the manual way (As opposed to from the repos), and for some reason I get this error:
Which is weird, because I did:

And I still get that error.

The message says "**only** by its owner", making it accessible by everyone does not meet that condition.

---

### Post by lamego on 2007-01-27
You should keep with the repository versions specially when you don't have much linux know-how.
Setting a file 777 is usually a VERY BAD option.

---

### Post by Pobega on 2007-01-27
Well I ended up getting it working, but for some reason it doesn't want to update anything. And when I shut down my computer (I have quiet off), it shows everything shutting down but specifically says something about ddclient not running.

The version from the repos didn't work for me either, by the way. I've gotten furthest with the source version.

---

### Post by Pobega on 2007-01-27
> pobega@ackbar:~$ sudo ddclient
Password:
WARNING:  unable to determine IP address
Using the one from the repos now, although I'm still basically stuck at the same point as before.

---


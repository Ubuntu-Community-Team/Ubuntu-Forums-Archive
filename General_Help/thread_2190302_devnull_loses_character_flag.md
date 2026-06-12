---
title: "/dev/null loses character flag"
date: 2013-11-26
forum: General Help
---

### Post by Spuds on 2013-11-26
I have two machines with the exact same behavior.  Both are 13.10

One is in an OpenVZ container.  I believe that OpenVZ is the genesis of the problem.

It has already caused problems with SSHD, and now our mailer and backup scripts are having trouble running.

Anyway, I noticed that /dev/null was losing its character flag and then exim, tar and a few other things (most things, probably) start getting a little wonky.

I wrote a script to delete the bad /dev/null and then mknod a new one-- but then it just gets changed back.

I do not have any idea what's causing the change.

EDIT:  I think I may know what is causing it.  I checked out and saw that the /dev/null file was 7 bytes long to I catted it out and it said simply: openvz

And it is in an OpenVZ container.  Why is this happening and how can I make it stop?

Can anyone help?

---

### Post by efflandt on 2013-11-26
Which Ubuntu? Your profile says you are still using 9.04.

---

### Post by Spuds on 2013-11-26
Oh I really feel like a turd now. :)

13.10

---

### Post by Spuds on 2013-11-28
I edited the parent post.

The one that behaves the worst and causes the most problems is the machine that is inside an OpenVZ container.  It is a VPS through a provider.

I found 'openvz' in /dev/null at one point, and I know it's an OpenVZ container-- so this may be the culprit.

However, the server that is in our datacenter is a physical server.  I haven't determined the origin of its problem yet.

Hopefully someone here knows about this strange quirk with OpenVZ or will let me know that I'm on the wrong track.

---

### Post by sudodus on 2013-11-28
Redirecting or writing to /dev/null means (should mean) that you don't write at all. /dev/null is created by the system and belongs to the system. You are not supposed to delete it and make it again. What happens if you reboot your system?

[https://en.wikipedia.org/wiki//dev/null](https://en.wikipedia.org/wiki//dev/null)

> In Unix-like operating systems, **/dev/null** or the **null device** is a special file that discards all data written to it but reports that the write operation succeeded. It provides no data to any process that reads from it, yielding EOF immediately.

What are you trying to do? How are you using /dev/null?

---


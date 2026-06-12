---
title: "Can ubuntu be setup to allow users to use their logins on multiple computers?"
date: 2007-10-26
forum: General Help
---

### Post by sparrowkc on 2007-10-26
I'm just curious, but what I'm asking is if user 'Johnny' can, for example, walk into a computer lab, pick any computer he wishes, login as 'Johnny', and have all of his programs and /home contents show up (from a server)?  Would the /home folder being on the server do all this? Is that what you would call a fat client?

Feel free to just post a link.

---

### Post by Prospero2006 on 2007-10-26
I run a Ubuntu computer lab --I've got it installed on about 150 computers right now, and that's an interesting proposition.

This is what I would try:

I would first make sure that /home is mapped through fstab to a public samba share on the lan.    (Now, every computer in the lab has the same 'home' configuration.)

Then, I would create johnny's account on one computer and export /etc/passwd and /etc/shadow to the rest of the lab. 

At least I would pilot that concept on a few computers and see how it went. 

There's probably a better way to do it, but it'd be worth a shot if have the time and
the lab isn't configured yet.


Pros

---

### Post by sparrowkc on 2008-04-27
This thread is kind of old, I don't know if the forum system will bump it up to the top but...

8.04 can do active directory.  I think a better way to ask my question would have been is there a FOSS active directory equivilent?

---

### Post by Fixman on 2008-04-27
> **sparrowkc said:**
> This thread is kind of old, I don't know if the forum system will bump it up to the top but...

8.04 can do active directory.  I think a better way to ask my question would have been is there a FOSS active directory equivilent?

Or you can just log in on XCMP if they are conneted on LAN (on GDM, preferences->remote XCMP login)

---

### Post by sparrowkc on 2008-05-16
I have never understood why there seems to be an assumption that a linux computer lab is always thin client based.  In a lab of thirty people, a thin client network is not practical, let alone in a school with 4 or 5 labs.

---


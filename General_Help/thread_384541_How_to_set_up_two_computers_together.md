---
title: "How to set up two computers together?"
date: 2007-03-14
forum: General Help
---

### Post by jackn on 2007-03-14
I've got a PC, and I'm getting a laptop.
The point really is, two computers from now on.

I don't know how to handle this new situation. 
Is it necessary to have separate users for each computer? 

On the one hand, each computer requires a user, or else, how can I boot either one without a user?... 
On the other hand, it would be odd to have separate users, as if the computers were independent, although they'll be networked.

Shouldn't I be able to have the same users on either that I could have access to whenever I turned on either computer? Does this kind of setup require a server, and not only a network? Does it require the computer with the server to be always on? I guess this is what I have at work, allowing me to log on as the same user from any machine.

Would it be possible to share a single /home directory, on a separate partition, that would be common to both? I'm pretty sure I've seen this done with dual booting. In other words, can either machine mount the same /home partition, regardless of whether it's on the same computer or not?

I guess I need some basic conceptual input. I'd appreciate basic references, too.

Jackn

---

### Post by gus sett on 2007-03-14
I can help with the basic concepts till someone who has used linux/unix
more recently responds.  Yes, you can have user(s) unique yet commonly
recognized within your *network*, the group of 2 or more computers.  
The dominate computer in a tranaction is the host/server and the subordinate 
one(s) is/are the client(s). The host will have the reference file containing the 
list of the unique users and their attributes, and any clients can have copies of 
the reference file which they can share with each other and the host.  Post any 
follow up inquires you may have.  These days, many software applications
shield you from these details, but it's good that you asked for briefing
on the concepts, because that helps guide your search till more responders
are available.  The reference for the details has traditionally been *man*,
short for manual (pages). :arrow: 

> **hroit said:**
> I've got a PC, and I'm getting a laptop.
The point really is, two computers from now on.

I don't know how to handle this new situation. 
Is it necessary to have separate users for each computer? 

On the one hand, each computer requires a user, or else, how can I boot either one without a user?... 
On the other hand, it would be odd to have separate users, as if the computers were independent, although they'll be networked.

Shouldn't I be able to have the same users on either that I could have access to whenever I turned on either computer? Does this kind of setup require a server, and not only a network? Does it require the computer with the server to be always on? I guess this is what I have at work, allowing me to log on as the same user from any machine.

Would it be possible to share a single /home directory, on a separate partition, that would be common to both? I'm pretty sure I've seen this done with dual booting. In other words, can either machine mount the same /home partition, regardless of whether it's on the same computer or not?

I guess I need some basic conceptual input. I'd appreciate basic references, too.

Jackn

---


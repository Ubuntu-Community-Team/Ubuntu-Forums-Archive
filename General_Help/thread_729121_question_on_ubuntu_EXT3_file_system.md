---
title: "question on ubuntu EXT3 file system"
date: 2008-03-19
forum: General Help
---

### Post by smooth3006 on 2008-03-19
when i installed ubuntu i formatted a 26.5gb partition using EXT3.

and a 2.8gb partition using linux swap.

the question i have is, ive been reading not to format with the EXT3 file system. will this affect my ubuntu install in any way ?

---

### Post by kidders on 2008-03-19
Hi there,

I'm curious about where you read that ... Ext3 is among the most trusted filesystems in the world. There are plenty of excellent alternatives, but Ext3 is a pretty good general-purpose choice for most people. Are you planning on doing something specialised with your hard disk that would make it unsuitable?

---

### Post by banewman on 2008-03-19
Where did you read that?
Ext3 is the default in many linux distros for a good reason - you're ubuntu install will be ok using it.
:)

---

### Post by smooth3006 on 2008-03-19
i read it on a thread in here somewhere.

---

### Post by kidders on 2008-03-19
> **smooth3006 said:**
> i read it on a thread in here somewhere.

Hmm... the thread topic may have been something very application-specific. Ext3 does have a wide variety of major disadvantages, but most users don't see the need to use other filesystem types unless they're actually *affected* by one of them. Perhaps the o/p of the thread you read was.

For example, users with very, very large disks (or arrays of disks) would find Ext3 totally impractical. Your relatively small filesystem will behave itself just fine though. :-)

---


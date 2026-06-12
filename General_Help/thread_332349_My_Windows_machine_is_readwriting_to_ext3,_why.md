---
title: "My Windows machine is read/writing to ext3, why?"
date: 2007-01-05
forum: General Help
---

### Post by tenjin1 on 2007-01-05
I have a NAS formatted to ext3 and my Ubuntu partitions are ext3. My secondary computer is running Win2000, I have samba setup and my home directory is mapped in My Computer. I also have my NAS mapped too. Anyways, I was on my Win computer and browsing my NAS directories and decided to copy/paste file, also deleted it, played mp3 and created folder etc. Did the same thing in my home partition.

I've been reading that Windows can't natively read ext3 without a driver or apps like explore2fs and such. So why am I able to do this? I'm not complaing but..kinda strange. Maybe I already have support for ext3..I dunno? I've double-checked and my NAS is ext3 and my Ubuntu is definitely ext3.

So what do you think the deal is?

---

### Post by Levander on 2007-01-05
It sounds like your Windows box isn't reading the ext3 partition directly.  It's reading it through the samba server.  Samba implements native Windows networking protocols, one of which lets you share files.

So, your Windows machine isn't talking to the ext3 partition.  It's talking to a layer above that, the samba server.  

Your Windows machine wouldn't be able to talk directly to the ext3 partition without something like Samba on top of the ext3 partition that Windows can talk to.

---

### Post by tenjin1 on 2007-01-05
Hmm ok thanks! I was wondering what the deal was...didn't think it was part of Samba but that is what SMB is! :-D 

So in what situation would you use the utilities for win to read ext3?

---

### Post by PilotJLR on 2007-01-05
Only if it were directly attached. For example, if you had a USB connected drive formatted in ext3, then the win ext3 is required.

SMB, like NFS, is an application layer protocol. It's like a "middleman"... the client connected to it doesn't know, and doesn't care about what filesystem is on the server end.

---

### Post by tenjin1 on 2007-01-05
Thx Levander and PilotJLR for the info on Samba! 

Is Cifs replacing Samba and NFS? and why?

---

### Post by PilotJLR on 2007-01-05
CIFS is simply a "newer" version of SMB... think of them both as windows file sharing protocols. They are similar, though I know some distros have deprecated SMB.

NFS is Unix/linux exclusive... similar end goal, but different (and open) implementation.

---

### Post by Levander on 2007-01-06
Didn't Microsoft make some "UNIX Services for Windows" (that's about the name of it) package freely downable a year or two ago?  I remember trying it one time right before it became free, but had too much trouble installing it, got busy, and gave up.

---

### Post by PilotJLR on 2007-01-06
Yeah, I remember seeing that too. I think it's an NFS client.

It's notable that Micro$oft can deploy an NFS client using the open protocol specification, while the Samba team has to reverse engineer SMB, cause it's proprietary.

---

### Post by tenjin1 on 2007-01-06
Yes looks like there's a link for it here:
[http://www.microsoft.com/technet/interopmigration/unix/sfu/default.mspx]("http://www.microsoft.com/technet/interopmigration/unix/sfu/default.mspx")

---

### Post by tenjin1 on 2007-01-06
:twisted:

---

### Post by tenjin1 on 2007-03-02
I guess I should have been more specific with this...while looking back on it. This was really an issue with the NAS and Win2000 and not Ubuntu. What it looks like is, my NAS has a built in SAMBA server for my Win2000 machine to be read/writing to it. Keep in mind this has noting to do w/ Ubuntu, as my NAS has it's own IP and is seperate from Ubuntu. I would consider this thread closed btw.

---


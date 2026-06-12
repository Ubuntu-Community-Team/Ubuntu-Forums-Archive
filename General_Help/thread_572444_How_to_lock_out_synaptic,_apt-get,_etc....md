---
title: "How to lock out synaptic, apt-get, etc..."
date: 2007-10-10
forum: General Help
---

### Post by thomasaaron on 2007-10-10
Hi, folks.

I'm writing a program and, when it is running, I would like for Synaptic, apt-get and the Add/Remove utility to be locked out.

How can I do this?

I know that somehow these programs can detect one another because you get this error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So, to summarize:
I know how to detect those programs. I just don't know how to make THEM detect MY program.

Any ideas?
How can I "lock the administration" directory?

Best,
Tom

---

### Post by dcstar on 2007-10-11
> **thomasaaron said:**
> Hi, folks.

I'm writing a program and, when it is running, I would like for Synaptic, apt-get and the Add/Remove utility to be locked out.

How can I do this?

I know that somehow these programs can detect one another because you get this error:

E: Could not get lock **/var/lib/dpkg/lock** - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So, to summarize:
I know how to detect those programs. I just don't know how to make THEM detect MY program.

Any ideas?
How can I "lock the administration" directory?

Best,
Tom

Well, that file is opened by whatever package admin program is running, so I suggest that your program also opens it.

---

### Post by thomasaaron on 2007-10-11
I did try to open that file.

The other package management programs just ignore mine and do their thing.
So, whatever it is that they are doing to lock that file/directory, it goes beyond just using it.

---

### Post by dcstar on 2007-10-12
> **thomasaaron said:**
> I did try to open that file.

The other package management programs just ignore mine and do their thing.
So, whatever it is that they are doing to lock that file/directory, it goes beyond just using it.

If it is opened for R/W access then (I assume, given every other OS that this works on) it should be locked, if it is opened RO, then it won't be.

---

### Post by thomasaaron on 2007-10-12
OK. I'll give that a try. I did just open for RO access.

---

### Post by thomasaaron on 2007-10-12
Well, I just tried opening it with Write access.
The other package managers didn't seem to care.

---


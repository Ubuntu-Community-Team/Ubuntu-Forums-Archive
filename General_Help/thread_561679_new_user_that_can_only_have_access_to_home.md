---
title: "new user that can only have access to home?"
date: 2007-09-27
forum: General Help
---

### Post by bone2006 on 2007-09-27
On a server I have ssh-server installed and I wanted to create a user that would have their own home directory that they would have full read/write access to this directory, but they could not navigate anywhere else.  Is there a way to create a user that can only access their own home partition and any directories below that?

---

### Post by tszanon on 2007-09-28
> **bone2006 said:**
> On a server I have ssh-server installed and I wanted to create a user that would have their own home directory that they would have full read/write access to this directory, but they could not navigate anywhere else.  Is there a way to create a user that can only access their own home partition and any directories below that?
I don't know if that's possible, because that user won't be able to run anything. No single program. Every user must be able to read many files (executables and their config files, for example).

I think that you're looking for a chrooted environment. This environment would be running a ssh-server. The user will have read-access to everything, and I think it wouldn't be a problem for you.

---

### Post by bone2006 on 2007-09-28
I'm not looking to have the person run any programs. It's on a server and yes it would be logging in with SFTP.

I'd rather the person only have access to the home directory and nothing else, even if it's only read I'd prefer that they are locked to the home directory. Is this not possible?

---


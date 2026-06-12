---
title: "extract tar to ssh server"
date: 2012-12-30
forum: General Help
---

### Post by spiders on 2012-12-30
Hi All,

I have a Ubuntu desktop and a gentoo server, and I have a .tar file on the server I want to extract that to my desktop without setting up windows share (smb).

I can't just scp the file to my desktop and extract it there coz there is not enough disk space and theres not enough disk space on my server to extract it on there and copy it to my desktop.

Is there a way of extracting it to a ssh server or deleting as it extracts.

Help would be appreciated,

spiders

---

### Post by rnerwein on 2012-12-30
> **spiders said:**
> Hi All,

I have a Ubuntu desktop and a gentoo server, and I have a .tar file on the server I want to extract that to my desktop without setting up windows share (smb).

I can't just scp the file to my desktop and extract it there coz there is not enough disk space and theres not enough disk space on my server to extract it on there and copy it to my desktop.

Is there a way of extracting it to a ssh server or deleting as it extracts.

Help would be appreciated,

spiders
hi
no space on both boxes ??? means no extract any where.
cheers

---

### Post by Lars Noodén on 2012-12-30
As stated, if there is not enough room there is not enough room.  

If you do have enough room but want to extract to the desktop without first expanding it on the server, you could do it this way:

```

ssh remote.server.example.org cat foo.tgz | tar zxf -

```

That would be run from the desktop system.

---

### Post by spiders on 2012-12-30
> **rnerwein said:**
> hi
no space on both boxes ??? means no extract any where.
cheers

there is no space for both the .tar and the extracted files, I want to have the .tar on my server and extract to my desktop

---


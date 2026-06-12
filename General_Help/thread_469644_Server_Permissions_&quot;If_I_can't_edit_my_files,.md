---
title: "Server Permissions: &quot;If I can't edit my files, everyone can!&quot;"
date: 2007-06-10
forum: General Help
---

### Post by lightnb on 2007-06-10
I'm having a bit of a problem getting my file permissions set correctly on my server.

Here's my setup:

I have a computer running Ubuntu Server 7.04 that is publicly accessible from the internet. I'm really kind of new to the whole server thing, and really just set it up to use for development, with the added benefit of being able to work on it from anywhere. In other words, it's not meant to be a high volume production server.

I am also running Samba on the server, so that I can edit the .php directly on the server from my other machine (Kubuntu 7.04 Desktop).

Everything seemed to be running Ok until I tried to edit one of the php.files. 

Even though I've logged into the server as the user who owns the files, and the user is allowed to read and write, I still got a no permission error when trying to save.

The only way I could get it to to allow me to save my changes was to CHMOD the file and the folder to 777.

So out of desperation I solved the problem by running:

> #chmod 777 -R /var/*

And now everything works exactly as I expect it to. I can edit my files without getting permissions errors, they load on the web page properly... -But having my /var directory (and all it's contents) writable by everyone in the world doesn't sound too enticing in retrospect.

So I ran:

> #chmod 000 -R /var/*

To protect my files until someone who knows what they're doing can help me set up permissions correctly.

In this configuration, which user should own the files? Which group?

Finally, what should the permissions be set to? One source said 644 was correct, but that causes a 'forbidden' page to display... should it be 655?

---

### Post by machoo02 on 2007-06-10
Have you tried 755?

---

### Post by lightnb on 2007-06-10
755 works for apache on the web side, but was still giving my smb user a hard time.

Should the web page files be owned by 'www-data' or the user that created them? Should www-data have write access to the files?

What if the user has less permissions than the group, is that ok? For example can a .html be 575, owned by www-data, and owned by the smbuser group, so that apache can only read and execute but the smbuser can modify it?

I almost need to set permissions on a per-user, per-file basis. Can that be done?

---


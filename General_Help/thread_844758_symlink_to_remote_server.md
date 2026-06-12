---
title: "symlink to remote server"
date: 2008-06-29
forum: General Help
---

### Post by smmalis on 2008-06-29
Is there a command to create a symlink to some other computer?  I've tried:
```
ln -s http://www.test.com/test.txt test.txt
```
but I get a broken symlink.  Is there any way to do this?

---

### Post by kuja on 2008-06-29
I don't think so. You might be able to create a *.desktop file that can accomplish it, using your file browser, however.

---

### Post by smmalis on 2008-06-29
Unfortunately, that won't work for what I need.  The situation is as follows:
I have two servers, one with 100 mb, and the other with 100 gb.  For technical reasons, people will always be accessing the 100 mb server, which contains binaries, etc.  However, I would like to put a 100+ mb file on the server, and people can't access the 100 gb server through the app we use, which can't be rewritten.  So I was hoping I could put the file on the big server, and just use a symlink on the small server.  The two servers are not networked together in any way, other than the internet.

---

### Post by kuja on 2008-06-29
I've no idea, seeing as the two are across the internet from each other. It may be possible to do using NFS, and the ip address, but I'm not sure as I've never attempted anything quite like that. Here's a quick NFS howto to give you a jumpstart, and I hope it helps :) [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by smmalis on 2008-06-30
I could try NFS, but I need something like a symlink.  I'm using a closed-source (unfortunately) app that needs one file, that I want to make a symlink.

---

### Post by vanadium on 2008-06-30
If you can mount the remote server in a directory on a local file system, then you can create a symlink to a file on the server. It depends on the server on how you can mount it locally, for example, a windows share can be mounted using smbfs, if you have a ssh connection, then you can use sshfs, and indeed nfs is yet another unix way of mounting a server locally.

---

### Post by Vivaldi Gloria on 2008-06-30
If you have ssh then you can use sshfs to mount remote files. If you can't ssh then I don't know the answer. But since there is a fuse fileystem for everything you can think of out there, I thought that there must be a fuse fs which can do what you asked for. I looked at the fuse webpage

[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)

and there are interesting projects here:

[http://fuse.sourceforge.net/wiki/index.php/NetworkFileSystems](http://fuse.sourceforge.net/wiki/index.php/NetworkFileSystems)

See for example

[http://httpfs.sourceforge.net/](http://httpfs.sourceforge.net/)

which can mount web files.

---

### Post by smmalis on 2008-06-30
I don't have root access on the first machine, is there a way to mount without it?

---

### Post by Vivaldi Gloria on 2008-06-30
> **smmalis said:**
> I don't have root access on the first machine, is there a way to mount without it?

Are you asking about sshfs or what?

You can mount sshfs without superuser rights if you have a suitable line in fstab. So you need the superuser rights at least once to add that line if you want to mount as a regular user. AFAIK, if you don't have that line in fstab then you can only mount as superuser. But I'm not 100% sure.

I don't know about httpfs, but I guess it is similar.

The following thread contains howto for feisty but works in hardy:

[http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312)

---

### Post by smmalis on 2008-06-30
Unfortunately, I have no root access whatsoever.  And mounting another file system is something the admin (not me) might not like.  A symlink would be the ideal situation, but that can't go across a network.  Any ideas?

---

### Post by justleen on 2008-06-30
a <a href> link from the 100mb server, to the 100gb server over http/ftp is not an option? just need rights on the 100gb server, though..

if you dont have rights on either machine it will be difficult i think

---

### Post by koenn on 2008-06-30
symlinks require a path to the target, so the file has to be part of your filesystem, be it a local filesystem or a remote filesystem that you mounted locally (nfs, samba, other network protocols that can be mounted)

for a file on a remote server to be accessible it needs to be exported (nfs), shared (samba) or otherwise published (ftp, http, ssh, ....). Like, if you expect a "symlink" (or anything else) with http:// to actually work, you'd need a webserver on the other end to serve up that file. 

If you are in a situation that requires you to publish/share/... files, and you don't have the required (admin) rights to do so, either the place you work at is screwed up, our you're up to something fishy.
Maybe you can explain a bit ?

---


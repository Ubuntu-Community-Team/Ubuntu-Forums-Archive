---
title: "Samba reports out of disk space"
date: 2006-12-04
forum: General Help
---

### Post by mike_d on 2006-12-04
I'm having a small problem that is kind of annoying and I was wondering if anyone had any solutions.  I have a system running Edgy with all updates acting as a file server for my house (i.e. I have all security turned off to keep things simple).  The way I set up the server was to create a main share point, and then I mount the filesystems under that share point.  That way if I add drives and such, I don't have to go around to the other computers and add new shares.  The idea is just to keep it as simple as possible for other people to access the shares.  (I would love to do this with NFS, but I've never found a way to have a NFS share span more than one filesystem.)

Here's an example of what I do:

/share is in the root directory and that's what's shared via Samba
then /dev/hda2 is mounted in /share/a, /dev/hdb1 is mounted in /share/b, and so on.

This works great, on my clients (Windows, MacOSX, and linux), I can access all of the drives as subdirectories of /share.

The problem I've encountered is that Samba reports the amount of free space as the amount on /share only.  It makes sense, as it thinks that /share is all that's being shared and only knows to get the free space from there.  However, I know I have more space, and if I try to copy a large file to one of the other drives the client complains and says there isn't enough free space and won't allow the copy to start.  (There is enough free space - if i ftp to the server and upload the file directly it works fine).

So my questions is, is there a way to tell samba to report a different amount of free space?  Or is there some other trick I can use to make it easy to copy big files over to the share?

Thanks,
Mike

---


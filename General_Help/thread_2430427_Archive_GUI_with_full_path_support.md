---
title: "Archive GUI with full path support"
date: 2019-11-01
forum: General Help
---

### Post by Leechpool on 2019-11-01
Hi,
I'm trying to "back up" changes I've made to various files within a directory structure.
I know the files I've changed, I just want a copy of the file and to know where it was located within the directory structure i.e. it's full path.
I have worked out how to do this with command line tar, but would find it better to use a graphical front end.
I've done a lot of searching and tried many options like archive manager, peazip and ark.
I like ark the best but just can't work out if it's possible to get any of them to store the full path when a file is added to the archive.

I assume something exists that can do this and maybe even the ones I've tried can but I'm stuck.
If anyone could provide some help I would appreciate it.
thanks
:D

---

### Post by TheFu on 2019-11-01
backup tools do this, but working with a single file as the backup source is a huge hassle.

OTOH, if you let the backup tool handle versioning of each backup, it will deal with that sort of stuff for you. rdiff-backup is what I use. It has a very similar option set as what rsync uses, so it isn't hard to learn.  
Or
you could use a version control system if the files are text or text-like.  Huge blobs aren't a good fit for code version control systems, but pretty much anything else will work fine.  git is the normal DVCS used these days, but RCS, SCCS, CVS, SVN all would work. Use symbolic links with RCS.
Or
keep using tar, but tar is a linear archive tool, so any changes/additions/deletions are appended to the end of the  an existing tar file.  tar was designed for use with backup tapes and really designed for 250 MB and smaller sizes.

---


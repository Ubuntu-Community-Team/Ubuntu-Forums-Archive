---
title: "Definitive guide to using NFS with Snaps?"
date: 2020-03-26
forum: General Help
---

### Post by khloe on 2020-03-26
Just upgraded my desktop to 18.04 and am having issues with my NFS share due to Snaps. It seems this has been a long standing issue, but I've never had it bite me until now. I am surprised it has been remarkably hard finding information about how Canonical expects users to use Snaps when they mount NFS shares. Is there a definitive guide somewhere? None of the official NFS manuals and guides give any indication. I've read through a handful of bug reports and forum posts, trying anything suggested and none of them work. There seem to be several major software applications that only officially support Snaps such as GIMP and Chromium, so I don't know what to do there unless I install from unofficial sources (which scares me) or build from source (what a pain).

I have several directories under /home/khloe/ that are NFS shares:

/home/khloe/Documents/
/home/khloe/Recordings/
/home/khloe/Videos/

and so on.

How do I make it so that software installed via Snap are able to read/write to those directories?

I tried modifying /etc/apparmor.d/tunables/home and adding all the paths in the HOMEDIRs variable. That had no effect. 

@{HOMEDIRS}=/home/ /home/khloe/Downloads/ /home/khloe/Videos/ /home/khloe/Recordings/ /home/khloe/Pictures/ /home/khloe/Music/ /home/khloe/Misc/ /home/khloe/Documents/ /home/khloe/Dev/ /home/khloe/Torrents/ /home/khloe/eBooks/

I tried running sudo dpkg-reconfigure apparmor and adding all of them there, and that also had no effect.

---

### Post by TheFu on 2020-03-26
Opinion:
Sadly, snaps are broken and the snap developers are in total denial about this problem along w/ supporting mounts where the local admin places them.

---


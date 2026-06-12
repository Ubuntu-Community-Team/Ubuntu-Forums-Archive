---
title: "&quot;Connect to Server&quot; at login / questions about gvfs-mount"
date: 2012-12-05
forum: General Help
---

### Post by ChoneZone on 2012-12-05
I would like to be able to perform Nautilus's "Connect to Server" feature on login to automatically mount some SFTP locations. From what I understand, the underlying command that Nautilus uses for this is gvfs-mount.

I am able to mount from command line using "gvfs-mount sftp://user@host.name" but when I try to add this line to my bash profile so that it automatically mounts on login, I get the message "Error mounting location: volume doesn't implement mount". Also, when I SSH to the machine from a different machine, I get the same error message both from my bash profile and when trying to enter it in via the command line.

From digging around a little bit, I gather that gvfs-mount might require gvfsd (gvfs daemon) to be running, and that this is not the case when trying to mount from an ssh connection or from bash profile. Does that sound right? How daemons work and how processes get launched at startup is a little bit above my pay grade, so can anyone help clear this up for me and point me in the right direction?

---


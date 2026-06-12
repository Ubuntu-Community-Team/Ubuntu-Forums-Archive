---
title: "[SOLVED] Music, Video, etc. directories in home directory"
date: 2007-12-01
forum: General Help
---

### Post by kens8 on 2007-12-01
I have an 80 gb hard drive, where I have Ubuntu & XP installed, and a 120 gb hard drive, where my music, videos, etc. resides.  Is there any way to point the Music, Video, etc. directories that are in the home directory by default to directories on my other hard drive?  ie. So I can click on "Music" in my home directory and it will access my music directory on my other hard drive.

---

### Post by amauk on 2007-12-01
you can delete the music, video, etc. directories from your home folder
they're just added by default

what you want to do, is make a symlink to your 2nd hard drive's music folder
(same as a shortcut on windows)

goto your music folder in nautilus, right click on it, and "make link"
you can now cut & paste the symlink to your home folder

obviously, the 2nd drive must be mounted in order for the link to work
I'm assuming you've got it automounting in fstab

---

### Post by kens8 on 2007-12-01
Thanks!  That's even easier than what I was thinking about!

---


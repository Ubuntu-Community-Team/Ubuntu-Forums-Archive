---
title: "Merging directories"
date: 2008-01-25
forum: General Help
---

### Post by dsnyders on 2008-01-25
Over the course of many upgrades, hard drive failures, and poor backup planning, I've wound up with many directories which contain essentially the same files.  I have about a dozen home/dsnyders directories scattered in various locations.  I'd like to merge them into a definitive folder.  I've looked at a number of utilities, but they all seem deficient in some way.  Either they are too manual, or they consider files to be identical based solely on content, and not by filename.

I'm looking for a tool to merge directories as follows:

merge source destination
If a filename exists in source but not in destination, move it from source to destination.
If a filename exists both in source and destination, compare the two files.  If the files are identical, remove the file from the source directory.  If the files differ, do nothing.
If there is a subdirectory that exists in the source, but not in the destination, then move it from the source to the destination.
If there is a subdirectory that exists in both the source and the destination, then merge them.
If the source directory winds up empty, remove it.

I'm sure this could be handled with a handful of scripts, but I lack the skill.:-(

---

### Post by 0mcg0 on 2008-01-25
Synaptic has a search function, try it with "merge directory" and you might find something that will help.  Also you should look at some scripting tutorials for bash and maybe python or perl or even ruby.

---

### Post by jpeddicord on 2008-01-25
Check out [Grsync]("apt:grsync"). It's a GTK interface to rsync, a powerful command-line backup/sync program. It might be difficult to get it set up initially, but once you have it going syncs are a snap.

---

### Post by dsnyders on 2008-01-26
*Check out Grsync. It's a GTK interface to rsync,*

I recently discovered rsync, and I'm glad you pointed me to grsync.  They will no doubt be helpful going forward once I've extricated myself from the mess I'm in.  

The grsync program, as far as I can tell, does not remove the files from the source directory.  This is an important step, as my hard drive is nearing capacity.  I'm not sure if rsync itself has this same limitation.  I'm googling for tutorials even now.

---

### Post by dsnyders on 2008-01-28
OK, I got grsync to delete the source IF it copies it to the destination.  You have to add the --remove-source-files option.  The problem is that doing this still leaves the source files in place if it detects that the file is already there in the destination directory.

Would version control software give me what I'm looking for?

---

### Post by dsnyders on 2008-02-03
I'm still looking for a solution to my merging problem.  rsync and grsync leave the files on the source.  fdupes and fslint consider files with different filenames to be the same if they have the same contents.  diff and kdiff3 attempt to merge the contents of files together.  My googling indicates that using a version control software on binary files is not a good idea.  That leaves me with scripting.

Unless someone has other suggestions?

---

### Post by dsnyders on 2008-02-05
Still looking for an answer.
Perhaps some backup software could do this?  The destination directory winds up being essentially a full backup, and the source directory a differential backup.

---

### Post by Mlehliw on 2008-02-09
I don't know if it does everything you want but Beyond Compare is close to releasing its version 3 public beta which will work natively on Linux. It is in private beta right now, but you could try emailing the dev team to see if you could get in.

---


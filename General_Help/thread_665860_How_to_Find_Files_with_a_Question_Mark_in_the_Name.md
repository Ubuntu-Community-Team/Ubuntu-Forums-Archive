---
title: "How to Find Files with a Question Mark in the Name"
date: 2008-01-12
forum: General Help
---

### Post by [z]ephyr on 2008-01-12
The title says it all.  I need to copy a bunch of files (some with question marks in the name) from my Kubuntu desktop to my Windows laptop, but since those files were created on the desktop where question marks are valid in a file name, I have to sit and watch and wait for the error in Windows that says it can't read a file with a ? in the name, figure out what's been copied, and then start again.  I was going to just do a find command to get all the files with ?'s and rename them, but since that's already a wildcard, it doesn't work.  Now I'm out of ideas.  How can I find those 7 or 8 files and just rename them or get rid of them if it comes to that.  I just hate sitting for hours watching the transfer, waiting for it to stop.

---

### Post by #Reistlehr- on 2008-01-12
if you put a \ infront of the ? it will read it as a question mark, not a wildcard. just like navigating directories/files with a space (/etc/directory\ with\ a\ space/file)

Works for me

---

### Post by [z]ephyr on 2008-01-12
Thanks, I didn't know about the leading \.

Anyway, command looked like this, in case anyone cares: find . -name '*\?*.*'

---


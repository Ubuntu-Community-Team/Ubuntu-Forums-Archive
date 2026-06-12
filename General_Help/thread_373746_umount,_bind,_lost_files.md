---
title: "umount, bind, lost files"
date: 2007-03-01
forum: General Help
---

### Post by kramerkeller on 2007-03-01
I did

mount --bind /home/folder /user1/folder
mount --bind /home/folder /user2/folder

Then later I unmounted so that /user1/folder would no longer link to /home/folder

I then could not find any of the files, this happened once before and i rebooted and everything was fine

This time however all the files under /home/folder are gone

However, I can still do locate file

and it shows /home/folder/file with all my files

but when I cd into /home/folder and ls, it lists nothing - did I lose my files or break a link and how do I fix this?  My space stills shows the files to when doing df?  It seems they are there, bu where?

---


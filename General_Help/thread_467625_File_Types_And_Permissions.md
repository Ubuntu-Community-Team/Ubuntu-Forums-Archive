---
title: "File Types And Permissions"
date: 2007-06-07
forum: General Help
---

### Post by Virgo53 on 2007-06-07
I could use the wisdom of the Ubuntu gurus to explain why Ubuntu thinks some JPEG images (photos) on my Windows partition are recognized in Ubuntu as plain text files instead. When I try opening them with the F Spot Image Viewer,  I get a fatal error message. Also, when I go to properties on the photos, I get some crap about not being the owner of the file, so I can't change the file permissions. Same thing in Trash -
 I have some deleted files there that can't be emptied because of the file permissions do-do. Please advise!

---

### Post by pbw on 2007-06-07
change ownership of the pictures to you.

sudo chown yourusername.users /path/to/picture.jpeg

Or to do them all at once

sudo chown -R yourusername.users /path/to/picturefolder/

(r flag means recursive)

---

### Post by Virgo53 on 2007-06-08
Thanks for your reply, pbw. I attempted what you suggested, but am getting "invalid user"when I type my username and path to picture folder.

---


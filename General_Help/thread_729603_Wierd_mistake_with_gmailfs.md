---
title: "Wierd mistake with gmailfs"
date: 2008-03-20
forum: General Help
---

### Post by LeoSolaris on 2008-03-20
I was messing around with gmailfs. I did not get the packages in the repo to work, so I tried doing it through the tar.gz's that the creator pointed to on his site. I followed the instructions and put the py's in the right places. I got it to mount, and that's where I hit a snag...

I mounted it to a usb port by mistake. I went back and made a gmail mount point in /media, and mounted it again there (it could not log in for some reason, gave me a little pop up box that reads "Couldn't display /media/gdrive: The attempt to log in failed" The username and password were correct.) I used the command line mounting rather than altering my fstab, BTW.

I would really like my USB port back, and to get rid of the extra media directory, but I have no idea how...

:confused:
I really hope someone can help.

Leo

Alright, restarting removes the gmailfs's hold on the usb port, and the media spot I made for it after learning how. I did manage to get it to work once, but it got fussy after the first transfer. I will continue to play with it to see if I can get it to be more reliable.

---


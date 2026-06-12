---
title: "Thunderbird: share mail with windows"
date: 2005-03-29
forum: General Help
---

### Post by sander marechal on 2005-03-29
Well, the good folk over at the Mozillazine forums could not help me with this, so I hope you can. I have a FAT32 partition mounted as msdos partition that is both loaded under windows and Ubuntu. On there is (unomg other things) my Thunderbird profile and I would like my Ubuntu thunderbird to use the same profile.

I tried [this method](http://texturizer.net/thunderbird/share_mail.html) but it only partially works. When I start thunderbird on Ubuntu, I see all my e-mail accounts appear, yet their inboxes do not hold any messages. I double-checked that I had edited the prefs.js correctly and I did.

Does anyone have any clue what I did wrong?

---

### Post by sander marechal on 2005-03-29
Okay, I *think* I have figured out the source of the problem:

my (windows) path to my mail is D:\mail\sander and thus my inbox's contents will be stored under: 

D:\mail\sander\Mail\mail.jejik.com\*.*

because of the way Thunderbird stores mail. Now, under MS-DOS this shows as:

D:\mail\sander\Mail\mailje~1\*.*

because of the long foldername. Now, under Ubuntu I mount the D:\ partition as an msdos partition (standard fat32 did not work and folders would show as "file objects" of some sort) with umask="000". Apparently mounting a partition as msdos under Ubuntu won't translate the long WIn32 filenames. My folder shows up exactly like the MS-DOS format. However, when thunderbird tries to access it through the long filename, it tries to access this:

/windows/mail/sander/mail/mailje/*

It doesn't use the ~1 and hence the location is wrong. Instead it creates an empty folder called "mailje" inside my sander/mail/ folder and happily procedes to fill it fresh from the server with all my e-mails.

What can I do now? Is there any way to make a Fat32 partition use Win32 long filenames under Ubuntu? Is there another way to share my mails between windows and linux without getting everything messed up?

Please help... :?

---

### Post by sander marechal on 2005-03-31
This issue has been resolved. I now mount my FAT partition as vfat instead of msdos and it works. The previous error when mounting as vfat (folders showing as file objects instead of directories) didn't reappear and everything works smoothly now. Don't ask me why though, it just does...

---


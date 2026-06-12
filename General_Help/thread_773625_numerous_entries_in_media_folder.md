---
title: "numerous entries in /media folder"
date: 2008-04-29
forum: General Help
---

### Post by darco on 2008-04-29
I have an External USB HHD and each time I access it, it adds another entry in the /media folder (see screenshot). I thought of removing via the rm -r but Im afraid it might wipe out the disk. If I click into any of the folders, I get a " The folder contents could not be displayed" error message. Right clicking does not give me any option to trash or unmount.
The valid folder right now is the one w/the sharing enabled.
Any suggestions?
thxs
darco

---

### Post by darco on 2008-04-29
ahhh...nevermind.....I unplugged the HDD, then deleted the leftover folders (insert embarassed emoticon)

---

### Post by agaudio on 2008-04-29
Glad to see you solved the problem. Though I have been plagued by similar problems myself with an external USB drive. The problem manifested itself as a new version of the drive name appearing with an underscore after the name. The drive remains plugged in all the time. In my case, the problem was simply that I had sbackup configured to run within a few minutes each time the computer starts up in the morning. However, the USB drive does not appear to mount unless someone logs in, and if the computer sat on the login screen for too long, it would create a folder with the same name as the USB driver in /media/ to do the backup to. Then, when I logged in, a new instance of the drive name with an underscore would be created.

So the long and the short of it is that in my case, it had to do with the computer trying to access the drive when it was not mounted.

Don't know if this helps at all, or if you even have any troubles anymore, but I just wanted to share my experience.

---


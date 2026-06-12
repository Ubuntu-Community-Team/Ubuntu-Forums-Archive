---
title: "Icons appeared on Desktop"
date: 2023-11-08
forum: General Help
---

### Post by MadMonkey1966 on 2023-11-08
At some point in the last week, all of the folders in my Home folder (including the Home folder) have now appeared on my Desktop.

I have no idea how. I always install any updates Ubuntu says are waiting when i see them, and all i can presume one of those caused this.

Even stranger is if i go into the Home folder through the icon or Terminal, Desktop is not there.

Somehow it has re-structured my directory is all i can think.

Obviously this does not prevent my computer from working, and all seems fine. I am just used to a clean Desktop.

Was this intended ? a bug or something else ? More to the point,Is there a way to rectify this ?

Any advice would be great.
Ian

---

### Post by yancek on 2023-11-08
Before doing anything, you might check the /home/username/.config/user-dirs.dirs file.  You should have a line (usually the first line) which looks like the below:

> XDG_DESKTOP_DIR="$HOME/Desktop" 

The first line should end with Desktop.  Make a note of the change you made so if it fails, you can change back and try something else but this should work.  You need to logout and login or maybe reboot for it to take effect.

---

### Post by MadMonkey1966 on 2023-11-09
Thanks for the reply.

Yes, your fixed worked. :)

I wonder how that happened, or rather what. I did notice that the file was last accessed/changed on Sunday, which would of been the last time i done any updates.

Still, all good now, and the other folders have gone from my Desktop.

Thanks yancek for your help.

---


---
title: "Disk size on Philips GO Gear 8Gb (can't delete files)"
date: 2013-04-18
forum: General Help
---

### Post by maghoxfr on 2013-04-18
Hello,

I have a Philips GO gear 8gb mp3 player, I'm running Ubuntu 12.04. The problem is that even though I delete folders on the mp3 player, ubuntu doesn't recognize that and never shows me the free space. For ubuntu it's like I never deleted any file. The worst part is that Clementine doesn't let me add more music to it because it's showing full when it's actually not.

ANybody with a hint on what's going on? I really don't want to do the music sync in windows. But if I can't use it on my work I'll go crazy.

IF I right click the mp3 player it says that its file system is msdos. I have no idea if that's of any help.

Thank you

---

### Post by mcduck on 2013-04-18
How are you deleting the files? Make sure they are actually deleted, and not just sitting in the Trash folder...

The files should appear in your main Trash folder, so as long as you empty that you should get the free space back. However if you have disconnected the device before emptying the trash, you might have to go and manually delete the hidden trash folder (".Trash-1000" or something similar) on the device itself...

---

### Post by maghoxfr on 2013-04-18
I wasn't aware that i had to empty t the trash bin before unplugging. Now i checked and there's a .Trash-1000 folder on the device full of undeleted files. Thank you very much.

---

### Post by maghoxfr on 2013-04-18
mcduck, you rock! I didn't this was the way to delete files from external drives. It worked.

Thank you very much

---


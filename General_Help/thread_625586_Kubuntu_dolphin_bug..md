---
title: "Kubuntu dolphin bug."
date: 2007-11-28
forum: General Help
---

### Post by guitarmaniac on 2007-11-28
Whenever I close dolphin in gutsy i get this error.
> Unable to save bookmarks in /home/luke/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.I have tried changing the permissions for this file but it doesnt work, every time I close properties for that and open it up again it comes back up as belonging to root.

---

### Post by guitarmaniac on 2007-11-28
OK I fixed it.
For anyone else that has this problem this is how I fixed it (though its probably a needlessly complicated way :P).
go to /home/USER/.kde/share/apps/d3lphin
Open up bookmarks.html
Go to Location > Save as
Save in your home directory.
right click on the bookmarks.html in your /home directory
go to properties and make sure that under Ownership on the permissions tab it says your user name.
delete the bookmarks.html in /home/USER/.kde/share/apps/d3lphin and replace it with the one you just created.

Obviously the problem was that dolphin couldn't write to the file as it was owned by root, but I couldn't change its permissions it the directory it was in.

---


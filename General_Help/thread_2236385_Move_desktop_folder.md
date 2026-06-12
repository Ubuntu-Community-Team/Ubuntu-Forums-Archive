---
title: "Move desktop folder"
date: 2014-07-26
forum: General Help
---

### Post by kakashi_12 on 2014-07-26
Ubuntu 14.04. I have a separate HDD for personal file storage. The OS is on another HDD.

I'd like to have Home Desktop folders ONLY (not videos or pictures or documents or anything else) to be moved to the other HDD.
I have done this for Windows already. Therefore, I'd want to change the name too if possible. So one would read "DesktopW" and "DesktopL" (for Desktop Linux) if possible.

I also already have a binded shortcut on the linux desktop that already points to the files on that other drive where personal data is. So if I move the desktop folder, hopefully it won't make 2 copies of that folder.

---

### Post by kakashi_12 on 2014-07-29
?

---

### Post by kakashi_12 on 2014-08-07
[http://www.howtogeek.com/howto/17752/use-any-folder-for-your-ubuntu-desktop-even-a-dropbox-folder/](http://www.howtogeek.com/howto/17752/use-any-folder-for-your-ubuntu-desktop-even-a-dropbox-folder/)

For me, need to change Binding.

---

### Post by kakashi_12 on 2014-08-07
_Final Resolution_:

1. Open DataTed folder. Create an empty directory called DesktopL.
(create a test file inside directory if you wish)
2. Open this file: Places, Home Folder, .config, user-dirs.dirs
(sudo permissions are not necessary)
3. On the line "XDG_DESKTOP_DIR=" change the path to the following:
/mnt/UserData/DataTed/DesktopL
4. Log off and back on to see changes take effect. See your test file on desktop. Delete the test file.
(Repeat all above steps for each user)

5. Places, Home Folder, Desktop. Drag the DataTed folder to the GNome bar (will create a Launcher).
6. Drag this Launcher to the *new* desktop (DesktopL).
(repeat above steps for all users)

10. Reboot into Windows. Change the folder name of Desktop to DesktopW. Be sure to re-point path.

*Note: do NOT re-bind. Re-binding will show FULL path, which be less secure since NTFS permissions aren't recognized. Hide the true path by keeping the binding pointed to the old desktop.

---


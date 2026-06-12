---
title: "reinstalling ubiquity on previously removed and remastered iso fails with error"
date: 2017-11-06
forum: General Help
---

### Post by kerrygee on 2017-11-06
Hi,

i did remaster a kubuntu iso and removed (apt purge) the ubiquity "ubiquity" installer package. when running the remastered iso as live system and reinstalling ubiquity inside the live session for installing the iso on the hard drive, i get a "10 passwd/user-fullname-casper-backup file is missing" error inside the dialogs textbox where to enter the username. after entering e.g. "someuser" and continue, it leads to a installer crash when reaching the copy /etc/skel stage. interessting fact: after closing the installer and restaring again, all preselected and given information is restored in the dialogs/textboxes and the installer will successfully pass the copy /etc/skel stage and fully install the live iso on the harddrive. i guess, it is expecting some file or config data somewhere that will be created on the first attempt, but is expected als to be readily available on the first installation attempt....but where is it and what does it expect to be inside e.g. a file or folder or whatever? i also assume, that removing (purging) ubiquity from the iso also removed the expected file/data. so, how do i reinstall or create a appropriate file or data after reinstalling ubiquity, so i dont have to run it twice to make it work. btw the /etc/skel directory holds a few documents and user specific environment configuration data, but i dont think that this is related with the crash, since it works flawless on the second attempt on the same data.

i attached a few screenshots.

any help would be really nice.

K.

---


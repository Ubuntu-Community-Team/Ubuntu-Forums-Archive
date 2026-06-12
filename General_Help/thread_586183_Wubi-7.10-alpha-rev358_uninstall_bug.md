---
title: "Wubi-7.10-alpha-rev358 uninstall bug"
date: 2007-10-22
forum: General Help
---

### Post by molk on 2007-10-22
During uninstall of Wubi even if one selects to backup downloaded files, ubuntu-7.10-desktop-amd64.iso gets deleted from C:\ubuntu\install and does not get placed into C:\ubuntu-backup. c:\ubuntu-backup does get created, but it is empty after the uninstall. One thing I want to point out is that I did not use Wubi to download  ubuntu-7.10-desktop-amd64.is,  but instead placed it into the same directory as the Wubi-7.10-alpha-rev358.exe, berofre running Wubi-7.10-alpha-rev358.exe to install Wubi. Not sure if this is relevant.

Also, whenever one installs Wubi in this way the Ubuntu iso gets moved from the directory in which Wubi-7.10-alpha-rev358.exe is located instead of being copied from it. I realize, that this is faster but this is not what a user would expect. Copying it would be the expected, albeight slower behaviour.

---

### Post by ago on 2007-10-22
> **molk said:**
> During uninstall of Wubi even if one selects to backup downloaded files, ubuntu-7.10-desktop-amd64.iso gets deleted from C:\ubuntu\install and does not get placed into C:\ubuntu-backup.
Yes that's an annoying one, WIll have a look tonight.

> Also, whenever one installs Wubi in this way the Ubuntu iso gets moved from the directory in which Wubi-7.10-alpha-rev358.exe is located instead of being copied from it. I realize, that this is faster but this is not what a user would expect. Copying it would be the expected, albeight slower behaviour.
If backup worked I'd assume that copying would be slower and a waste of space. Let's see what others think. It's easy for me to change that.

---

### Post by molk on 2007-10-22
"If backup worked I'd assume that copying would be slower and a waste of space. Let's see what others think. It's easy for me to change that. "

I think it's OK to keep the current behaviour as long as the user is notified that the ISO file they manually placed into the same directory as the installer is being moved and where it is being moved. I know I was very surprised to see that after I installed Wubi I did not have that ubuntu-7.10-desktop-amd64.iso anymore where I personally placed it. Just like I would be surprised if Wubi-7.10-alpha-rev358.exe was deleted after the installation without the installer asking me if I wanted to delete it or at least letting me know that it was going to be deleted.

Of course the other option is to copying the file instead of moving it.

---


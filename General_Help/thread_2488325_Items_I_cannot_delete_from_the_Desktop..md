---
title: "Items I cannot delete from the Desktop."
date: 2023-07-01
forum: General Help
---

### Post by cscj01 on 2023-07-01
I am on Ubuntu 22.04.2 x64 using Gnome-Flashback.  From I know not where (though I suspect a download), I have two objects on my Desktop that I cannot delete.  One has a .jpg extension while the other appears as a directory with an extension of .jpg.crdownload.  Neither object can be deleted by moving it to Trash.  When I try to do this, I get the following message:> Error while moving files to trash.Later in the block where the error message appears, there is the following:> No such file or directory.  When I go to ~/Desktop, the two items do not show. I might also add I cannot rename the items.  If I check properties, Basic says unknown for the all, and Permissions cannot be determined.  How can I remove something that the system thinks does not exists?

---

### Post by TheFu on 2023-07-01
If the files are still open when deleted, the OS will keep the file handle around until the process using it completes.
If the files are being downloaded, perhaps using a download manager, then there may be a process that keeps them open longer than you expect. If a logout/login doesn't remove the process with the file handle, a reboot certainly will.

If after a reboot, the files still exist, then there is something being run automatically that "someone" is running - automatic or intentional. I'd use **lsof ** to find which process has a file open.

---


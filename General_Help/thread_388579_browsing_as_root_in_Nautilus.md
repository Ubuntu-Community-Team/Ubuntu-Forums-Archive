---
title: "browsing as root in Nautilus"
date: 2007-03-19
forum: General Help
---

### Post by mpooley on 2007-03-19
Hi all
I have read and implemented the "How to" to browse as root.
as i understand it that should give me full permission to move any file i want -  I can rename files  in the etc/samba folder but i cant move them.
I want to create backups temporarily on my desktop while i fiddle.

how can i do this without using the terminal ?

thanks

Mike

---

### Post by taurus on 2007-03-19
<Alt>F2 -> gksudo nautilus

---

### Post by mpooley on 2007-03-20
Thanks thats neat!

But.
 LOL I tried to move smb.conf.bakup onto the desktop and it still wouldnt let me !!

Mike

---

### Post by sdil on 2007-03-20
I think, you, you must follow the instruction from : [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus)

---

### Post by 3rdalbum on 2007-03-20
I see your problem.

The *destination* file browser window must be run as root. The actual desktop is run as a normal user, so when it recieves the file that you dragged to it, it doesn't have permission to move the file.

In your existing root file browser, go to File and Open New Window. Use this window to browse to the "Desktop" folder in your home directory. Then you'll be able to drag and drop to this new file browser window, and the files will appear on your desktop too.

---


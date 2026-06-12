---
title: "when a USB device is plugged in, scan it for a certain file and execute it"
date: 2015-09-04
forum: General Help
---

### Post by kfir2 on 2015-09-04
Hello!

I'm looking for a way to tell when a USB device is being plugged in and then scan it for a certain file and execute it.

For example, let's say that my USB device has the following files in it:


&#9500;---update-2.3.sh
&#9500;---/updates
|   &#9492;---file1.php
|   &#9492;---file2.php
    &#9492;---/sub
        &#9492;---another.php
When I plug that USB device, I want to scan if there is a `update-2.3.sh` file and if there is execute it. [FONT=Helvetica Neue]Now that [/FONT]update-2.3.sh[FONT=Helvetica Neue] file will run certain commands such as [/FONT]mv[FONT=Helvetica Neue] to override existing files (there is a folder `~/code/app/updates) and some commands as admin:

[/FONT]sudo stop kiosk
(sudo?) mv updates ~/code/app/
sudo start kiosk[FONT=Helvetica Neue]
since there may not only be 1 USB device used for updates but many, I would like to listen to ALL USB devices plugged in and scan them for that specific file (the file will always be in the ROOT directory) and execute it.

How can I do that? I heard that udev may help here? maybe there is another solution?[/FONT]

---


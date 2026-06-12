---
title: "computer won't boot after system update"
date: 2008-06-27
forum: General Help
---

### Post by hypersoar on 2008-06-27
I just installed Xubuntu on a laptop. I ran the updater, and one of the updates wanted wanted to create a menu.lst. I figured it couldn't do any harm, so I let it. Now the computer won't boot. I get the message "NTLDR is missing." I'm not sure if the update I mentioned is what caused the problem, but it seemed pertinent.

---

### Post by dominiquec on 2008-06-27
Don't know if this fits the bill, but you may want to give this a try: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Had a problem with Grub one time after I rearranged partitions ([http://ubuntuliving.blogspot.com/2008/05/paritioning-misadventures-part-2.html](http://ubuntuliving.blogspot.com/2008/05/paritioning-misadventures-part-2.html)).  The link above helped me recover.

---

### Post by ago on 2008-06-27
Did you hard reboot by any chance? In case run chkdsk /r on windows. Even if grub was installed in MBR, something which would not happen in an automatic update, it would still be possible to boot windows, and certainly no update would delete external files.

---

### Post by hypersoar on 2008-06-27
How does the bootloader work in a Wubi install? Is it just grub pointing to another part of the same partition?

---

### Post by ago on 2008-06-27
the windows bootloader points to grub4dos which loads kernel/initrd within C:\ubuntu\disks\boot which in turn load up the virtual drive and pivotroots into that

---


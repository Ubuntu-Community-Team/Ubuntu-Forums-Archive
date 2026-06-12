---
title: "Disk Boot Failure"
date: 2007-02-24
forum: General Help
---

### Post by taylonr on 2007-02-24
**_Error Message:_** DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

**_System Setup:_**
2 IDE HDDs.
HDD 0 has Windows XP
HDD 1 has Edgy Eft (and grub)
Bios set to boot off HDD1 

**_Background to the Problem:_**
I booted into Ubuntu
Loaded VMWare XP Machine in full screen mode to do a little VB work
Was working on a VB project when it locked up.
Mouse would not move, arrow keys could not make cursor move, it was not responding to the keyboard at all 
Tried Ctrl+Alt+Del for windows VM Machine
Tried Ctrl+Alt+F? keys trying to get to a command line in Ubuntu
None worked
Pressed the restart button on the front of the case
Rebooted fine, but came up in windows.
Turned off computer and unplugged the ide cable from the windows HDD
Booted and received the above message
 
I inserted the Ubuntu install disk, but did not see anything on there about recovering the OS etc.

I would prefer to not have to reinstall (obviously) but if I do, is there a way to not lose my home directory?

Any suggestions?

Thanks in advance.

---

### Post by taylonr on 2007-02-24
This might just be a configuration problem.
I played around with some bios settings and removed the connection from the XP hdd and it booted fine.

If I find an answer, I'll post it just for future searchers, but it looks like it might be under control

</end panic attack>

---

### Post by JohnPhys on 2007-02-24
Out of curiosity, was your VMware loading a virtual drive of windows, or your physical partition on the other drive?

---

### Post by taylonr on 2007-02-24
Virtual drive.

I get my windows files through mapping my windows drive in samba, and then connecting the VM to the Ubuntu map.  It's a bit convuluted, but it usually works for me :)

---


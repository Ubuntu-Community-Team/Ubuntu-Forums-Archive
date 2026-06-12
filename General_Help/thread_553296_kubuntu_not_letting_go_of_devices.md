---
title: "kubuntu not letting go of devices"
date: 2007-09-17
forum: General Help
---

### Post by nymusicman on 2007-09-17
Whenever I try to safely remove any usb device it doesn't seem to let go of the device. Here is the message I get.

> Unfortunately, the device system:/media/sda1 (/dev/sda1) named 'Sansa e260' and currently mounted at /media/Sansa e260 could not be unmounted. 
Unmounting failed due to the following error:
Cannot remove directory
Moreover, programs still using the device have been detected. They are listed below. You have to close them or change their working directory before attempting to unmount the device again.
Cannot stat /media/Sansa e260: No such file or directory
Cannot stat /media/Sansa e260: No such file or directory
Cannot stat /media/Sansa e260: No such file or directory

If I write to the device instead of saying Cannot stat directory it lists of bunch of processes that could potentially be using it. Like so.\

> Unfortunately, the device system:/media/sda1 (/dev/sda1) named 'Sansa e260' and currently mounted at /media/Sansa e260 could not be unmounted. 
Unmounting failed due to the following error:
Cannot remove directory
Moreover, programs still using the device have been detected. They are listed below. You have to close them or change their working directory before attempting to unmount the device again.
                     USER        PID ACCESS COMMAND
/media/Sansa e260:   root          1 ....m init
                     root       2794 ....m udevd
                     root       4818 ....m getty
                     root       4819 ....m getty
                     root       4821 ....m login
                     root       4824 ....m getty
                     root       4826 ....m getty
                     root       5094 ....m acpid
                     root       5205 ....m syslogd
                     root       5261 ....m dd
...

The current permission set is 

User: myusername
Group: root

I've tried changing the group back to plugdev but even root has insufficient permissions. Am I missing something?

---

### Post by olieviya on 2007-09-17
Weird, have you similar issues with other external devices or just the Sansa?

---


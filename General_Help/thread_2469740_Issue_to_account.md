---
title: "Issue to account"
date: 2021-12-08
forum: General Help
---

### Post by peter-1984 on 2021-12-08
Hi,
How to resolve issue below within Ubuntu 18?

[https://ubuntuforums.org/attachment.php?attachmentid=289602&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=289602&stc=1)

---

### Post by ajgreeny on 2021-12-08
Is **rem01** the only user on the system or is there another who was setup when the OS was installed?

---

### Post by peter-1984 on 2021-12-08
I cannot edit file - /etc/sudoers. What to adjust for this issue?

---

### Post by ajgreeny on 2021-12-08
> **peter-1984 said:**
> I cannot edit file - /etc/sudoers. What to adjust for this issue?
No, nor should you try if you are not aware of the potential problems of doing so; it is very easy to completely lock yourself out of the system if you do not edit it as root using only the one appropriate command line method.

Please answer my question above, which unfortunately was misspelled as I used an Android keyboard which changed it for me (now spelled as it should have been).
Is rem01 the only user on the computer?

---

### Post by deadflowr on 2021-12-08
Boot into recovery mode > open the root shell prompt > reset the file system as read/write > then run
```
adduser rem01 sudo
```
then reboot.

Booting into recovery mode: [https://wiki.ubuntu.com/RecoveryMode]("https://wiki.ubuntu.com/RecoveryMode")
(Also includes how to reset the file system.)


The above assumes that rem01 is your only user you have created.
If you have another user already created who is already in the sudo group, then just su into that user and run the command above prefixed with sudo like
```

su <other-user-name-here>
sudo adduser rem01 sudo
exit
```
(you would replace <other-user-name-here> with the name of whatever your other user is, brackets not included)
After you exit the su'd user you need to logout and login again in order for the user to be properly placed in the sudo group.

---

### Post by peter-1984 on 2021-12-08
Thanks a lot. Is 2nd option below for recovery mode?

---

### Post by ajgreeny on 2021-12-09
Yes, you need the second line in the grub menu, ie, **Advanced Options for ubuntu** which will take you to a sub-menu, including Recovery mode.

---

### Post by peter-1984 on 2021-12-09
What to select below? Should I be with root password to work on it?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289618&stc=1[/IMG]

---

### Post by ajgreeny on 2021-12-10
You need the **Drop to root shell prompt** option

---

### Post by peter-1984 on 2021-12-10
Thanks a lot.

---


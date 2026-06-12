---
title: "Removed Myself From Admin Group"
date: 2008-06-02
forum: General Help
---

### Post by austx on 2008-06-02
Hi,

I managed to accidentally remove myself from the admin group. Now, I can't sudo anymore. Is there any way to get myself back in short of reinstalling the whole system? I can't go into single-user mode either, because it is asking me for the root passwd.

Thanks,
Steve

---

### Post by sisco311 on 2008-06-02
Boot with the live cd. Mount your root file system and try to manually edit the /etc/group file. Add your user name to the admin line.

---

### Post by angry_johnnie on 2008-06-02
I remember this. :-)

Go [here]("http://ubuntuforums.org/showthread.php?t=798775") and look at Aysiu's post (that will be post #6).

If your root account doesn't have a password, you could still do this from recovery mode.

---

### Post by ibuclaw on 2008-06-02
Boot into recovery mode in the GRUB menu (Press ESC at startup and it should be option 2) and go into the root shell.
Then type in this command
```
usermod -a -G admin **yourname**
```
Replace "yourname" with your username, of course :)

Then type in
```
exit
```
To exit the root shell and then continue with the normal boot.

Your admin privileges should be back and working again.

Regards
Iain

---

### Post by austx on 2008-06-02
Sisco311:
Thanks, that did the trick.

angry_johnnie:
That didn't work, because it would always prompt me for the root password, which I didn't have (and it didn't accept my regular password)

tinivole:
Couldn't boot into recovery mode, because again, it asked me for the root password.

Thanks everyone!
Steve

---

### Post by sisco311 on 2008-06-02
(EDIT: You probably know)
You can disable the root account:
```
sudo passwd -d root
```and use sudo and gksudo to run applications as root.
*"sudo -i*" or "*su -" *to start a root session in the terminal.
[Benefits of sudo.]("https://help.ubuntu.com/community/RootSudo")

---


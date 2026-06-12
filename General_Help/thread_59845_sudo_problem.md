---
title: "sudo problem"
date: 2005-08-25
forum: General Help
---

### Post by cymoril on 2005-08-25
hi there,

i'm not sure what i did .. but i can't sudo anymore.

i receive this message in the terminal:

sudo: must be setuid root


also, when prompted to type my userpassword in gnome desktop when I load Firestarter for example, i receive this error message:

failed to run /usr/sbin/firestarter : child terminated with 1 status.

how do i rectify this?

thanks,
cym.

---

### Post by arnieboy on 2005-08-25
[QUOTE=cymoril]hi there,

i'm not sure what i did .. but i can't sudo anymore.

i receive this message in the terminal:

sudo: must be setuid root


also, when prompted to type my userpassword in gnome desktop when I load Firestarter for example, i receive this error message:

failed to run /usr/sbin/firestarter : child terminated with 1 status.

how do i rectify this?

thanks,
cym.[/QUOTE]
Sudo must be setuid root to do its work.  You need to do something like
   ```
chmod 4111 /usr/local/bin/sudo
``` as root. 
HowTo do that?
make sure your root account is enabled.
then do a "su" from terminal.
Also, the file system sudo resides on must *not* be mounted (or exported) with the nosuid option or sudo will not be able to work (check your /etc/fstab file).  Another possibility is you may have '.' in your $PATH before the directory containing sudo.
to have '.' in your path you should make sure it is at the end.

---

### Post by Stormy Eyes on 2005-08-25
EDIT: Arnieboy's method is a good one, if you've already enabled the root password. If you haven't, then you may have to resort to mine:

First, do "which sudo" and note the location of the sudo program. I think it's in /usr/bin, but it might be in /bin or /sbin or /usr/sbin. Once you know where sudo lives, reboot. Don't let GRUB use the default, but instead press a key when GRUB does the countdown and select "Recovery Mode". This will boot you into single-user mode. Once you've gotten into single user mode, do the following command: **chmod a+s $PATH/sudo**. Then reboot again into normal mode. That should make sudo work again.

---

### Post by cymoril on 2005-08-25
arnieboy and Stormy Eyes, thank you.

as i had yet to enable the root password, rebooting into Recovery Mode and using chmod solved my problem.

thanks again,
cym.

---

### Post by Stormy Eyes on 2005-08-25
That's good to hear.

---


---
title: "Help with sudoers file"
date: 2008-03-27
forum: General Help
---

### Post by darkone99 on 2008-03-27
OK here 's the deal 

i accidentally deleted my sudoer s file , when messing around with files in /etc.. now sudo wont work at all , i have a copy of a new sudoers file saved on my desktop . My question now is how do i copy this new sudoers file into /etc ?  when i try copy and paste it gives me a permission error : "You do not have permissions to write to this folder" . the new sudoers file looks like this :

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
%admin	ALL=(ALL) ALL
```

---

### Post by fmartinez on 2008-03-27
> **darkone99 said:**
> OK here 's the deal 

i accidentally deleted my sudoer s file , when messing around with files in /etc.. now sudo wont work at all , i have a copy of a new sudoers file saved on my desktop . My question now is how do i copy this new sudoers file into /etc ?  when i try copy and paste it gives me a permission error : "You do not have permissions to write to this folder" . the new sudoers file looks like this :

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
%admin	ALL=(ALL) ALL
```

I've had a similar situation where I've changed the actual permissions for my account. I wasn't able to execute any codes as a root user. 
Unless you have another account set up as an administrator or you've given root a password I think you out of luck.
Since then I've installed an extra administrator account as a backup (just in case).

---

### Post by mrsteveman1 on 2008-03-27
You can always boot into single user mode, or worst case boot your ubuntu disk and move the files around from there, where you have control over everything.

---

### Post by ibuclaw on 2008-03-27
Boot into Recovery (**option 2 in the GRUB Boot Menu**) and copy the file to /etc/sudoers.

```

cp /path/of/file /etc/sudoers
exit

```
Then Ubuntu will continue to start as normal.

OR
Boot from your **Ubuntu LiveCD** and open a terminal.
Type in:
```

sudo mkdir /media/gutsy
sudo mount /dev/sda1 /media/gutsy
sudo chroot /media/gutsy su
cp /path/of/file /etc/sudoers

```
And reboot.
[EDIT] /dev/sda1 being replaced with your root partition location, respectively.

Regards
Iain

---


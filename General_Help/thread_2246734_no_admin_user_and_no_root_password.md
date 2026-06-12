---
title: "no admin user and no root password"
date: 2014-10-02
forum: General Help
---

### Post by claytonbagwell on 2014-10-02
This old Acer Celeron M 1.3GHz was changed somehow while in the hands of a friend during my 3 month away. I now have it back, but it is a _single user who is not an administrator and the root password is no longer recognized_, producing the well-known 'not on sudoers list' error. I cannot change the single user status to administrator because only the root password will allow access and the root password doesn't work anymore. I have been to GRUB  and Boot Menu to deal with the password problem, but that only effects the password of the present user. I can change that password but that is not the root password. I know the old root password but it gives the sudoers list error everytime I use it. The user is <joseph>. He is not an administrator. Here is a screen shot of id joseph.

This is a screen shot of user accounts:

This is because I don't have the root password to open the user accounts.

So the user is not an administrator and has no priviledges, and the old sudo password is now rejected because it is not on the sudoers list. I have used GRUB, I have used Boot Manager but these methods only change the password for user <joseph> and do not effect root password. I am in a Catch-22.

I need to construct a new root password without knowing the current root password. Every avenue I have encountered so far requires the current root password which is not accepted because of the sudoers list.

Help will be greatly appreciated!

---

### Post by QIII on 2014-10-03
Hello!

I have removed the base64 created when you attempted to paste an image directly into the text entry box.

When posting an image, please use the attachment functionality by clicking the paper clip icon in the tool icons just above the text entry box.

Thanks.

---

### Post by deadflowr on 2014-10-03
Nobody ever knows the root password, unless you made one.
However you can add the user to the sudo group using the recovery mode method.
First reboot, and get the grub boot menu.
(If it doesn't normally show I think you need to tap the shift key right when the screen leaves the bios screen)
Second in the grub menu select recovery mode, usually the second entry.
Third, in recovery mode go to root shell and open.
Fourth, this shell defaults to read only, but it can be changed to read/write using the following command
```
mount -o rw,remount /
```
Now with it remounted read/write enter
```
adduser <username> sudo
```
change <username> to your username.
This will add the user to the sudo group add give the user admin rights.
The exit, and a reboot should be all you need.

---


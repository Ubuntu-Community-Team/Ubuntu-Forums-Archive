---
title: "Cannot login as administrator"
date: 2015-08-19
forum: General Help
---

### Post by nn2 on 2015-08-19
Hello,
My problem is that I cannot login as administrator any more or its taking really really long to log in.
I use ubuntu 14.04 and last week I tried to activate password in my administrator account, but I didnt activate it at the end. 
Now after ubuntu starts loading i get a black screen and nothing.. I tried Diagnostics and the first time i think i got error in the hard disk from previous check. After testing is finished i can log in as Guest but not as Administrator.
ty :KS

---

### Post by buzzingrobot on 2015-08-19
By default, no root user (aka Administrator) account exists in Ubuntu.  Users temporarily elevate their privileges by using the "sudo" command.

Have you tried to create an actual root account, or by "administrator" do you mean the account you created when you installed Ubuntu and that you routinely log in as?

---

### Post by nn2 on 2015-08-19
yes that's what i mean. i ususally log in as "nn" and now i am logged in as "Guest". All my files are saved in the nn account

---

### Post by deadflowr on 2015-08-19
disabled password means disabled user.
to fix you can reboot and in the boot menu go to advanced options and then go to any recovery mode entries listed.
In recovery mode you need to enter the root shell, but...
root shell will be set as read-only, so you need to switch it to read/write.
To do so you can either first go the networking route.
Go to the networking option in recovery mode, open it and when it finishes the root shell will be read/write automatically.
The second method is to go directly into root shell and run
```
mount -o rw,remount /
```
this will also rest it to read/write.
Now with root shell set as read/write run the passwd command to change your password.
Basically like so
```
passwd username
```
it'll ask for the new password and then a confirmation.
with the new password set, type
```
reboot
```
and your user should run with the newly enabled password after the reboot.

Beyond that, I'm not sure what else you might need, but

Hope it helps.

---

### Post by nn2 on 2015-08-20
can i change password logged in as guest?

---

### Post by deadflowr on 2015-08-20
> **nn2 said:**
> can i change password logged in as guest?
If the password is not locked, then maybe.
You'd need to remember the old password, as it asks for it if not using sudo/root.

If the password is locked then, no.
Locked passwords need an admin-level account to unlock them.

---

### Post by nn2 on 2015-08-20
i dont think i remember it. I cannot access recovery mode, do you know why? i hold the shift key but nothing happens.

---

### Post by deadflowr on 2015-08-20
If the machine is newer you might be using UEFI, which you hit the ESC key instead of shift to get the boot menu.
Me thinks...

Alternatively, you can use a livecd as well.
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by nn2 on 2015-08-21
i am sorry, i have multiple problems. 
i cannot enter recovery mode, i think the esc key is correct but recovery doesnt load. this command (with different numbers at the beginning) appears constantly when loading:  
'[20.29.372607] system-udevd [4091] : failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/hal/udev_event': No such file or directory



I am using live cd,  ubuntu 9.04 and i am running these commands

```
 sudo mount -o rw, remount/ 
```
and i get:
```
 can't find remount/ in /etc/fstab or /etc/mtab 
```
 and 
```
 passwd nn 
```
i get
```
 unknown user nn 
```

---

### Post by nn2 on 2015-08-21
i remember the password for nn but it asks password for Guest and it is not same, I don't remember having one

---

### Post by steeldriver on 2015-08-21
AFAIK you won't be able to 'sudo' anything from the guest account since  guests are not added to sudoers: if you can't access Recovery Mode then  you may need to chroot from a live CD/USB

Your mount command must have no spaces between the options, and must have a space before the target directory [COLOR=#0000ff]**/**[/COLOR]

```

mount **-o rw[COLOR=#0000ff],[/COLOR]remount** [COLOR=#0000ff]**/**[/COLOR]

```

---

### Post by jfh on 2015-08-21
I don't know if this will help, but I got stuck in the guest account, from which you apparently can't change anything, including how to get OUT of the guest account.  Seeing no other alternative, I was going to insert the Ubuntu 14.04 dvd and format and reinstall Ubuntu (I have only Ubuntu installed on this old computer).  However, when I inserted the dvd I was suddenly able to exit the guest mode.  Maybe this installation of Ubuntu felt threatened and decided to cooperate. Who knows?
And I still can't get on the internet!

---

### Post by nn2 on 2015-08-21
am i using sudo with live cd?

---

### Post by nn2 on 2015-08-21
i run "mount **-o rw[COLOR=#0000ff],[/COLOR]remount** /" and then "passwd nn" but still it says unknown user
[COLOR=#0000ff][/COLOR]

---


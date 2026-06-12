---
title: "Need help with MAJOR password Issue"
date: 2008-03-13
forum: General Help
---

### Post by theBZA on 2008-03-13
So the issue is, about 4 months ago while I was learning the Ubuntu ropes I went in and changed my profile username and password and, not only that, but I changed my root password.  Now, in some ill state of mind I chose both passwords out of God knows where, because I am trying to log in now and none of my usual suspects work, nor do variations on them.  I have tried logging in recovery mode, but it asks for a root password, and I don't know that either.  The only other option at that point is cntrl+D but that gets me nowhere.

All I need to know is if there is some obscure hack to get/change my friggin password(s), or if all is lost and I need to re-install.  Any help you can give would be GREATLY appreciated.  Thanks

---

### Post by lgambett on 2008-03-13
This is quite easy... While Ubuntu starts you get the GRUB menu. One of the choices of this menu is the recovery mode. Start with this, and you will start in console mode, without the need of a password. Then you can change your password with
passwd username
(change username with actual username).
With Ubuntu there is no root account enabled by default. If you have explicitly defined a root account you can change the password with
passwd
while in recovery mode.
HTH,
Luca

---

### Post by Oldsoldier2003 on 2008-03-13
> **lgambett said:**
> This is quite easy... While Ubuntu starts you get the GRUB menu. One of the choices of this menu is the recovery mode. Start with this, and you will start in console mode, without the need of a password. Then you can change your password with
passwd username
(change username with actual username).
With Ubuntu there is no root account enabled by default. If you have explicitly defined a root account you can change the password with
passwd
while in recovery mode.
HTH,
Luca
The problem is he enabled root, therefor recovery mode asks for the password.

---

### Post by lgambett on 2008-03-13
Ok. Never tried myself, but should work.
1) obtain a live distribution like Knoppix
2) start Knoppix and enter root shell
3) edit /etc/gshadow (nano /etc/gshadow) and modify the line containing the word root as such;
[SIZE="3"]root:*::[/SIZE]
this should disable root password.
Save /etc/gshadow, remove Knoppix CD and reboot in recovery mode. Adjust user passwords as described in my previous post.

---

### Post by Oldsoldier2003 on 2008-03-13
> **theBZA said:**
> So the issue is, about 4 months ago while I was learning the Ubuntu ropes I went in and changed my profile username and password and, not only that, but I changed my root password.  Now, in some ill state of mind I chose both passwords out of God knows where, because I am trying to log in now and none of my usual suspects work, nor do variations on them.  I have tried logging in recovery mode, but it asks for a root password, and I don't know that either.  The only other option at that point is cntrl+D but that gets me nowhere.

All I need to know is if there is some obscure hack to get/change my friggin password(s), or if all is lost and I need to re-install.  Any help you can give would be GREATLY appreciated.  Thanks
If you can log in using your normal account ```
sudo passwd root
``` if not then you have to take more drastic steps...

[http://aplawrence.com/Linux/lostlinuxpassword.html](http://aplawrence.com/Linux/lostlinuxpassword.html) is one way and if you google you'll see plenty of tutorials on how to do this

---

### Post by Oldsoldier2003 on 2008-03-13
> **lgambett said:**
> Ok. Never tried myself, but should work.
1) obtain a live distribution like Knoppix
2) start Knoppix and enter root shell
3) edit /etc/gshadow (nano /etc/gshadow) and modify the line containing the word root as such;
[SIZE="3"]root:*::[/SIZE]
this should disable root password.
Save /etc/gshadow, remove Knoppix CD and reboot in recovery mode. Adjust user passwords as described in my previous post.
if he can edit /etc/shadow to a blank password its good to go. then all he needs to do after he recovers is to disable root login to return to the sudo security model.

---

### Post by RussellW on 2008-03-16
When I was putzing around with my users the other day, I mangled up my password somehow. This really got my a** out of a bind! Thanks a million Luca!!!!!!!!!!

"This is quite easy... While Ubuntu starts you get the GRUB menu. One of the choices of this menu is the recovery mode. Start with this, and you will start in console mode, without the need of a password. Then you can change your password with
passwd username
(change username with actual username).
With Ubuntu there is no root account enabled by default. If you have explicitly defined a root account you can change the password with
passwd
while in recovery mode."

---

### Post by aysiu on 2008-03-16
I have no idea what *gshadow* is, but unless *gshadow* is a secret shortcut to editing /etc/shadow on a mounted partition, then I doubt that will do any good.

And I guess it bears repeating that if you have set and forgotten a root password, booting into recovery mode is useless, as recovery mode will ask you for the root password you forgot.

What you should do is boot up a live CD (it doesn't have to be Knoppix--it could be the Ubuntu Desktop CD) and mount the partition in question. Let's say, for this example, that you mount it to /media/recovery. Then you would edit the /etc/shadow file with this command: ```
sudo nano -B /media/recovery/etc/shadow
``` and make sure the line beginning with the word *root* has ```
root:!:
``` at the beginning of it instead of something like ```
root:$1$qFDMS$o0E9sSuXlAizFZ2Sy9N4z.:
``` Then save (Control-X, Y, Enter), and reboot without the live CD into recovery mode. You should then be able to reset your original username's password: ```
passwd *username*
reboot
```

---


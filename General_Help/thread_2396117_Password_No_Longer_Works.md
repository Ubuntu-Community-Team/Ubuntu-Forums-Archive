---
title: "Password No Longer Works"
date: 2018-07-11
forum: General Help
---

### Post by SpikeLS6 on 2018-07-11
I booted up Ubuntu 18.4 I have been using since April, but it refused my password several time. I used an older boot number, but same result.

I Went into Terminal and did a Recovery Mode/Root and entered "mount -o rw,remount /" I changed the Password and it Ubuntu booted up from Recovery. However, when I tried to reboot, the only way I could get Ubuntu to come up was going through the Recovery Protocol again.

I something missing in my GRUB loader?

---

### Post by Autodave on 2018-07-11
Try hitting the *backspace *key a few times before you enter your password.

---

### Post by friedchips2 on 2018-07-11
Boot from hitting "e" on a "normal" grub entry then change -ro to -rw and add exec=/bin/bash right behind that. That will log you in as root. Then use passwd to change your password. For examle I would use passwd stephen

EDIT:
The line you want to edit is the one start with linux

---

### Post by SpikeLS6 on 2018-07-12
The Backspace several times before entering the Password did not work. Still have to go through the Recovery sequence to get Ubuntu to Boot.

Where does the "Boot from hitting "e" on a "normal" grub entry then change -ro to -rw  and add exec=/bin/bash right behind that. That will log you in as root." entry go? Is that a Terminal line entry?

---

### Post by friedchips2 on 2018-07-12
it goes in grub, where you chose recovery. With a "normal" kernel highlighted press e.

---

### Post by SpikeLS6 on 2018-07-13
In the normal (top most) kernel I did the e entry to gain the list. I went to the Linux line and replaced the ro with an rw, then added exec=/bin/bash. No change; still can not get into the regular kernel with a password.

I went into Recovery again and Updated the Grub2 loader with the same results. I still can only boot up into 18.4 through Recovery and the current password.

---

### Post by friedchips2 on 2018-07-14
when it booted after you made changes were you at a command line?

If so did you do passwd USERNAME?

---

### Post by SpikeLS6 on 2018-07-15
Yea, entered Username XXXX, then passwd XXXXX.

---

### Post by mIk3_08 on 2018-07-15
SpikeLS6, you may try to enter username:_root_ then the password: _is your password_

---

### Post by SpikeLS6 on 2018-07-15
Password is now moot.I downloaded and installed a new driver for a new wide screen monitor and it locked up 18.04 to the point I can not get into it. Monday I'll take it to the shop and ask & pay for help. I need to get this PC working pronto. Thank you for your help and your ideas. I;ll show this as SOLVED, because the new 18.04i install ought to solve lots of issues.

---

### Post by mIk3_08 on 2018-07-15
okay good luck SpikeLS6.

---

### Post by NM5TF on 2018-07-15
> **mIk3_08 said:**
> SpikeLS6, you may try to enter username:_root_ then the password: _is your password_

actually...[COLOR="#FF0000"]it's basic security policy to have separate user & root passwords[/COLOR]....having them the same opens the door to doom

should have been set up that way at installation.....just sayin' :p

---


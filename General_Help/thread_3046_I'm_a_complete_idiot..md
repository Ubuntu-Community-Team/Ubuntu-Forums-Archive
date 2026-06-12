---
title: "I'm a complete idiot."
date: 2004-11-02
forum: General Help
---

### Post by claymore on 2004-11-02
Hi, all.

I am fairly new to linux, and I just managed to totally disable my ubuntu installation.  I'm sure it's an easy fix, but I have no idea how to do it.

Before I had installed ubuntu, I was dual booting Windows XP and Mandrake.  Then I replaced Windows with ubuntu, and the ubuntu installer automatically detected my Mandrake installation when I installed it.  Now, I like Ubuntu a lot better than Mandrake so far, because it is far lighter and faster, so I switched all my stuff over to my Ubuntu installation.  I sometimes miss KDE, though, so I decided to give MEPIS a try.  I used the MEPIS installer to nuke my Mandrake partition, then got it installed.  Unfortunately, the MEPIS grub loader didn't notice my ubuntu partition and now I can't get logged into Ubuntu.

I tried editing the grub loader on the new partition manually.  That has allowed me to load up the correct partition, but I am unable to log in.  It is not able to connect to the ICE file and dumps me back out to the login screen every time.   How can I install a bootloader that will recognize both of these operating systems?  I definitely don't want to reinstall Ubuntu after doing all that configuring.

Thanks in advance for all your help.

---

### Post by FLeiXiuS on 2004-11-02
Can you login at all via CLI?

---

### Post by claymore on 2004-11-02
I was able to log in the failsafe terminal mode, but not into the default gnome mode.  I am not sure what you mean by CLI, sorry.

Just to give a few more details, this is the section I added to the grub loader (I may have missed something important here):

title UBUNTU at hdc1, kernel 2.6.8 k7
kernel (hd0,0)/boot/vmlinuz-2.6.8.1-3-k7 root=/dev/hdc1 ro noapic nolapic quiet splash
initrd (hd0,0)/boot/initrd.img-2.6.8.1-3-k7
savedefault

Also, here is the message I get when I try to log in:
"Unable to read ICE authority file: /home/XXXX/.ICEauthority"

---

### Post by FLeiXiuS on 2004-11-02
[QUOTE=claymore]I was able to log in the failsafe terminal mode, but not into the default gnome mode.  I am not sure what you mean by CLI, sorry.

Just to give a few more details, this is the section I added to the grub loader (I may have missed something important here):

title UBUNTU at hdc1, kernel 2.6.8 k7
kernel (hd0,0)/boot/vmlinuz-2.6.8.1-3-k7 root=/dev/hdc1 ro noapic nolapic quiet splash
initrd (hd0,0)/boot/initrd.img-2.6.8.1-3-k7
savedefault

Also, here is the message I get when I try to log in:
"Unable to read ICE authority file: /home/XXXX/.ICEauthority"[/QUOTE]


CLI = Command Line Interface

First off I have a few ideas.
-Check Permissions
-Re-Setting Permissions

**Checking Permissions**
```
ls -l /home/`user_name`/.ICEauthority
```
Replacing `user_name` with your username.  This should read out as ```
-rw-------
``` if not procede to the following step below.

Re-Setting Permissions
To re-ceate the auth file...run the following command:
```
iceauth -f /home/`user_name`/.ICEAuthority
```
Again replace `user_name` with your current username.

---

### Post by claymore on 2004-11-03
Thanks for your help, FleiXiuS.  I will give that a try as soon as I get home tonight.  I don't understand how that could have gotten changed, though.

---

### Post by claymore on 2004-11-03
Well, the last thing I did before installing MEPIS was to try to run K3B in ubuntu.  Turns out that the Iceauthority bug is a common problem with that, and it's what caused this whole problem, not the grub stuff.

Hopefully, that will solve the problem.  I didn't even think to look up whether it was because of K3B.

Thanks anyway, though.  I appreciate the time you put in.

---


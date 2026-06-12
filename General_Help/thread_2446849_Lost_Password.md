---
title: "Lost? Password"
date: 2020-07-07
forum: General Help
---

### Post by Jim_Robinson on 2020-07-07
Hi Folks,

I have not used the forum for while but now I have a problem that I cannot solve.

I have a dual boot laptop W7Pro & Xubuntu 18.04 LTS

But when I tried to login  the other day, I cannot so, I tried to change the password using "physocats" method which I know works without any difficulty. In fact, I have helped several friends to enable them to login by using this method plus recovering my systems when I have forgotten the password, because I have several PCs, all with different passwords

The problem is that when I select root i.e. Drop to root shell prompt, on the Recovery Menu, it transfers to root as normal but here is the rub,

> Give root password for maintenance
(or press Control-D to continue

i.e. asking for root password again  (endless loop)
I know that I may have forgotten my password, but  as I can boot in the W7 partition using the same password, it is puzzling. Yes I know that is not good to do so but I use the same password for the W7 & the Xubuntu 18.04 LTS partitions. Also I not remember ever setting the Root password. Is there another way of removing the offending password. I have several bootable Live USB keys or should I say that they worked the last time I used them. 

Is there another way of removing/replacing the password file and/or the shadow file when using an external boot.

Best Wishes
Jim

---

### Post by ActionParsnip on 2020-07-07
If the root password is set then you will need to chroot from a live CD/USB OS. You can even use the Ubuntu install media for this.
I suggest checking some YouTube videoa about chrooting. You will then be on as root, can set the user password as well as the root password if you want and reboot.

---

### Post by sisco311 on 2020-07-07
> **Jim_Robinson said:**
> Hi Folks,

I have not used the forum for while but now I have a problem that I cannot solve.

I have a dual boot laptop W7Pro & Xubuntu 18.04 LTS

But when I tried to login  the other day, I cannot so, I tried to change the password using "physocats" method which I know works without any difficulty. In fact, I have helped several friends to enable them to login by using this method plus recovering my systems when I have forgotten the password, because I have several PCs, all with different passwords

The problem is that when I select root i.e. Drop to root shell prompt, on the Recovery Menu, it transfers to root as normal but here is the rub,



i.e. asking for root password again  (endless loop)
I know that I may have forgotten my password, but  as I can boot in the W7 partition using the same password, it is puzzling. Yes I know that is not good to do so but I use the same password for the W7 & the Xubuntu 18.04 LTS partitions. Also I not remember ever setting the Root password. Is there another way of removing the offending password. I have several bootable Live USB keys or should I say that they worked the last time I used them. 

Is there another way of removing/replacing the password file and/or the shadow file when using an external boot.

Best Wishes
Jim



If you can boot a Live USB, then simply mount your root partition and chroot to it. Assuming that /dev/sdb1 is your root partition:
```
sudo mount /dev/sdb1 /mnt
sudo chroot /mnt
```

From here you should be able to use the passwd command (as usual) to change your user's password and/or lock/change the root password.


In case you don't have a working Live CD/USB, you can boot into a root shell with the **init=/bin/bash** kernel parameter.
See: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

EDIT:
It was a long time ago when I used this technique, but I think I had to delete the **quiet** and **splash** parameters to get a functional root shell.

---

### Post by Jim_Robinson on 2020-07-12
Hi Sisco311,

Thanks for the instructions, they worked .
But then I realised that I needed to remove my root password. So I googled and found some further information about removing the root password. I will detail them below.  I have extended your instructions "Sisco331"

```

[B]sudo mount /dev/sda5 /mnt
sudo chroot /mnt

[/B]Additional stages
Edit password file[B]

cd /etc
nano passwd[/B]

[FONT=arial black]Find root[/FONT]
root:x:0:0:root:/root:/bin/bash
[FONT=arial black]**Delete "x" therefore should look like**
[/FONT]
[FONT=arial black]root::0:0:root:/root:/bin/bash
Save updated  file [/FONT][FONT=arial black][FONT=arial black]using 
[/FONT][B][FONT=arial]cntrl x
y[/FONT][/B]

Edit shadow file a similar manner
nano shadow
locate root line but looks quite different

root:[COLOR=#ff0000]$2qwer------until next :numbers:0:10000:[/COLOR]:::

delete red section [/FONT][FONT=arial black][FONT=arial black][COLOR=#ff0000]$2qwer------until next :numbers:0:10000 
[/COLOR][COLOR=#000000]leaving only 4 colons[/COLOR][/FONT]
[/FONT]
[FONT=arial black]root::::
save 
[/FONT]
[FONT=arial black][FONT=arial black][B][FONT=arial]cntrl x
y

reboot
[/FONT][/B][FONT=arial] using "pyschocats" method 
**grub menu**
**recovery mode**
**root** note no request for root password
**mount o rw,remount /**
reset password
**passwd** jim
follow prompt note no feedback on screen re what you are typing in **enter**
follow 2nd prompt and retype password **enter**
if they match all is well
[B]exit
[/B]at recovery menu select[B] resume
[/B]then** OK**[/FONT][/FONT][/FONT]

```

Apologies about the long set of notes/instructions but they worked

Thanks to all who replied.
All I need to do now is mark it solved

Best Wishes 
Jim

---


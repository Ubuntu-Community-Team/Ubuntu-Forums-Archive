---
title: "Login Issues"
date: 2007-04-22
forum: General Help
---

### Post by primate1098 on 2007-04-22
The boot worked fine, but I can't figure out my username & password.  Is there anyway to reset it?  I've been trying to login with the info I thought I put in the installer, but with no luck.

thanks

---

### Post by dreadlord_chris on 2007-04-22
Boot into Recovery Mode. From there you can either reset the password for your account - or create a completely new one.
To reset the password:
```

passwd USERNAME

```
It will then ask for a new password - type one, then confirm it.

If that doesn't work for some reason (the account got corrupted or whatever) then just create a new account:
```

useradd --create-home --password  <PASSWORD> <USERNAME>

```
replace <PASSWORD> with the password you want to use
replace <USERNAME> with the name you want to log in under....

You should be able to log into your account now....

---

### Post by primate1098 on 2007-04-22
how do i boot into recovery mode with this installer?  whenever i reboot it doesn't ever show that GRUB deal, do you have to like push a key to get into GRUB or?

update: i'm able to get into GRUB but I only have one choice to boot and it is just ubuntu w.o out recovery mode. I can edit some GRUB file from there... menu.lst. Is there a way to edit the menu.lst file so I can boot into recovery mode so I can do the password reset command?

Thanks

---

### Post by dreadlord_chris on 2007-04-23
> **primate1098 said:**
> how do i boot into recovery mode with this installer?  whenever i reboot it doesn't ever show that GRUB deal, do you have to like push a key to get into GRUB or?

update: i'm able to get into GRUB but I only have one choice to boot and it is just ubuntu w.o out recovery mode. I can edit some GRUB file from there... menu.lst. Is there a way to edit the menu.lst file so I can boot into recovery mode so I can do the password reset command?

Thanks

Sorry it took so long to get back to you....

you can edit menu.lst? Good. Look for this line:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```
Just put a **#** in front of hiddenmenu:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

```
Right above (probably) the hiddenmenu entry look for:
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

```
You might want to change the timeout to something like 10...
Now scroll down near the bottom, you're looking for your GRUB menu entry. Here's what mine looks like (with the Recovery Mode entry):
```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5794201f-3d92-45bf-ba83-2e4cedc1e8fe ro splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5794201f-3d92-45bf-ba83-2e4cedc1e8fe ro single
initrd		/boot/initrd.img-2.6.20-15-generic

```
Notice the differences? To add a _Recovery Mode_ entry just duplicate your default entry but replace anything that follows **ro**, in the default *kernel line* entry, with **single**.
Now save the file and reboot. You should now have a GRUB menu with (hopefully) a Recovery Mode option.

---

### Post by logan1441 on 2007-05-19
how did you get into the grub thing? mine doesnt come up either

---

### Post by ecology2007 on 2007-05-19
[B]how did you get into the grub thing? mine doesnt come up either.
[/B]Logan these files are not for you they are not up to date. That s why you see some errors.

---


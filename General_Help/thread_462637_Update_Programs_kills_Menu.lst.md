---
title: "Update Programs kills Menu.lst"
date: 2007-06-02
forum: General Help
---

### Post by NJC on 2007-06-02
This is the 2nd time this has occured. I recently downloaded the *.28 kernel (security update?) 21.7mb file for Dapper. Ubuntu requests machine restart and then subsequently alters menu.lst so Ubuntu won't reboot (Linux is on hdb1 and the upgrade rewrites it back to hda1 + removes my Win dualboot code). 

It changes this section:
```
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot
```

I have a backup so can easily change it back but WHY? Any suggestions as to what I can do to prevent this?

---

### Post by confused57 on 2007-06-02
What does your #kopt line show?:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

Your Window's entry has to be outside the ###BEGIN AUTOMAGIC KERNEL LIST and ###END DEBIAN AUTOMATIC...or it will be removed each time update-grub is executed.

---

### Post by NJC on 2007-06-03
confused57;

Thanks for your prompt help. BTW, that's a fantastic link and I've bookmarked.

I never knew the Win dualboot entry should be outside the ###BEGIN AUTOMAGIC KERNEL LIST and ###END DEBIAN AUTOMATIC section. I just looked through menu.lst and saw this comment:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

Had a look and don't have a #kopt entry. I can fix the Win section but it is normal behaviour to rewrite this section?

```
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
```

It would be fine if Ubuntu was on hda1 but it's on hdb1 so the kernel update kills the reboot.

---

### Post by confused57 on 2007-06-03
I'm surprised you don't have a kopt entry, so running the command:
```
gedit /boot/grub/menu.lst
```
doesn't show the #kopt entry?

If it doesn't, it probably wouldn't hurt to make one...using the example in the Hermanzone link.

---


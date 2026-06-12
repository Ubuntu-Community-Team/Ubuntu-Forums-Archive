---
title: "Possible to remove Grub screen option at boot?"
date: 2014-06-24
forum: General Help
---

### Post by 777funk on 2014-06-24
I have my Xubuntu OS on it's own drive which is the first to boot from the BIOS and since it's the only OS on the drive, I really have no use for the GRUB screen. Originally it never showed up. Now a week after the install for some reason I'm now getting the GRUB screen. Is there a way to disable this?

---

### Post by pqwoerituytrueiwoq on 2014-06-24
run this command:
```
sudo update-grub
```
if that does not fix it post the output of this
```
cat /etc/default/grub
```

---

### Post by 777funk on 2014-06-24
Here's what the first spit out. I'll restart and see.

```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Adding boot menu entry for EFI firmware configuration
done

```


EDIT: That did the trick! I wonder why GRUB showed up all the sudden just out of the blue.

---

### Post by monkeybrain20122 on 2014-06-24
Why do you want it disappear? It is handy for trouble shootings.

---

### Post by 777funk on 2014-06-24
> **monkeybrain20122 said:**
> Why do you want it disappear? It is handy for trouble shootings.

You know, you're right. In my last install (Ubuntu 12.04) I had a time where there was a kernel a year or so ago that wasn't doing what I liked and I was able to choose another option. But for the most part I personally (at least for the usual) think it's an annoyance to have one more thing to mess with at startup time. 

Just for the record (so I know how to if I need it), how do I bring it back (never had grub to begin with)?

---

### Post by oldfred on 2014-06-24
With BIOS it is hold down shift key from BIOS start until menu appears.
But with UEFI it seems to be press escape key not even hold it.

Grub does have a check on shutdown, so if computer seems to have issues or not normally shutdown, it defaults to showing menu so you can use recovery mode.

---


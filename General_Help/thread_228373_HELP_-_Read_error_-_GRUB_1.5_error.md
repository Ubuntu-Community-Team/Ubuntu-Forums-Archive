---
title: "HELP - Read error - GRUB 1.5 error"
date: 2006-08-03
forum: General Help
---

### Post by MJSOnline on 2006-08-03
Hello all.  I have a problem.  I have installed a new motherboard [this one](http://www.ebuyer.com/UK/product/110725) and memory to suit.  Booted up ok, but both FDD and HDD lights are always on, but when I load my O/S, Ubuntu I get a read error, GRUB error 1.5.  So I tried the "live CD" and the FDD was showing as my CD drive.  I cant get into my system at all, but the live cd can see and give a discription of the drives inside the base unit.  What do I do to fix it?
Thanks.  Matthew

---

### Post by fourchannel on 2006-08-03
is it "grub error 1.5" or "grub error 15"?

If it's error 15 then that means that it cannot find the expected harddrive it's looking for.

on your live cd see if you can access your installed ubuntu filesystem and copy and paste the contents of these 2 files so we can see why the drives don't match up.
```
/etc/fstab
/boot/grub/menu.lst
```

---

### Post by coffeecat on 2006-08-03
Not sure what you mean by a Grub 1.5 error. There is a stage 1.5 in Grub and the [Grub manual]("http://www.gnu.org/software/grub/manual/") lists the various errors as integers. Might be useful to know what the error number is - it's probably being returned by stage 1.5.

Anyway, if I've understood you correctly, you've changed the motherboard for an already installed Ubuntu. I guess the way the new BIOS has assigned the various drives is at variance to the fstab entries.

Suggestion: Boot into the live CD and make a copy of its /etc/fstab. Now mount the HD from the live CD (if you can) and copy the /etc/fstab from the HD. If there are significant differences, edit the HD version or post back for help.

**Edit:** fourchannel and I posted simultaneously - fourchannel is quite right. You need to look at /boot/grub/menu.lst as well.

---

### Post by MJSOnline on 2006-08-04
Thanks guys.  I will report back once I have tried the report thing.  Looking at the GRUB manual, erro 1.5 is coruppt or damaged partion. How do I fix it? Thanks. Matthew

---

### Post by fourchannel on 2006-08-04
we need to see those 2 files before we can really help you. Right now it's a shot in the dark.

In times past that I've gotten error 15 when my IDE0 and IDE1 got mixed up. It was a bios setting, which one was the primary and secondary harddrives. Maybe that's causing the error?

---

### Post by MJSOnline on 2006-08-04
How do I get the report of the the two files? M

---

### Post by MJSOnline on 2006-08-05
Anyone got a clue? Thanks. Matthew

---

### Post by confused57 on 2006-08-05
You could open the files in a terminal:

```
cat /etc/fstab
cat /boot/grub/menu.lst
```
The .lst is short for list, not first.

I'm not sure, but you might need to mount the partition first:
[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

If you have a Knoppix Live CD, you can mount it using the gui.

---


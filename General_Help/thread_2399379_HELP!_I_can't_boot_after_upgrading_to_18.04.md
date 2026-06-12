---
title: "HELP! I can't boot after upgrading to 18.04"
date: 2018-08-24
forum: General Help
---

### Post by scribner on 2018-08-24
I upgraded to Ubuntu 18.04 from 16.04 last week.

Now, when I restart the computer, I am bombarded with a BusyBox command line with the first command preceded by "initramfs."

How do I get back to the regular operating system from here?

---

### Post by pretty_whistle on 2018-08-24
This won't help you but...oh really? I just tried to upgrade from 16.04.04 to 18.04.1 and got the same thing as you. Then I tried to run updates for 16.04.04 but got the same screen!!!  The update was bad and I'm thinking it made 18.04 not boot!

---

### Post by scribner on 2018-08-25
Does anyone know how to fix this? I should note the OS booted normally the first couple of times.

---

### Post by #&amp;thj^% on 2018-08-25
> **scribner said:**
> Does anyone know how to fix this? I should note the OS booted normally the first couple of times.

Not really. :( All we can do is offer suggestions to try.;)
Have you first tried to check your file system for errors.

To check the file system on your Ubuntu partition...

    *boot to the GRUB menu
    *choose Advanced Options
    *choose Recovery mode
    *choose Root access
at the # prompt, type 
```
sudo fsck -f /
```
    *repeat the fsck command if there were errors
    *type "reboot"

If for some reason you can't do the above...

    1.boot to a Ubuntu Live DVD/USB
    2.start gparted and determine which /dev/sdaX is your Ubuntu EXT4 partition
    3.quit gparted
    4.open a terminal window
    5.type "sudo fsck -f /dev/sdaX" # replacing X with the number you found earlier
    6.repeat the fsck command if there were errors
    7.type "reboot"
initramfs is the real root. It is where the Linux kernel initializes userspace by execing init and subsequently renouncing all responsibility for any problem you might encounter thereafter.

---


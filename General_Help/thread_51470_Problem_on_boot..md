---
title: "Problem on boot."
date: 2005-07-24
forum: General Help
---

### Post by kevcart3 on 2005-07-24
I followed the tutorial to try to change the color and resolution of the boot process. After rebooting here is what happens:

```

Mounting a tmpfs over /dev...
/lib/lsb/init-functions: line 194: below: command not found
 *Cannot find initrd device!
Setting disc parameters...
/lib/lsb/init-functions: line 194: below: command not found

*The device node /dev/hdb1 for the root filesystem is missing,
*incorrect, or there is no entry for the root filesystem
*listed in /etc/fstab.

*The system is also unable to create a temporary node in
*/dev/shm to use as a work-around.

*This means that you have to fix this manually.

*Control-d will exit from the shell and REBOOT the system

``` 

Okay, I'm sort of experienced in using the shell, so I can follow any instructions you can give pretty much.

I could fix the problem myself, because I have a backup of init-functions, BUT it's mounting the filesystem as read-only, so how do I get the filesystem back to where I can read from it and restore the original init-functions back to normal?

Thanks in advance!

---


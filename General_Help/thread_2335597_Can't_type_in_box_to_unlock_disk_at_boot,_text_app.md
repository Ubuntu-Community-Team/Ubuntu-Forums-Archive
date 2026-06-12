---
title: "Can't type in box to unlock disk at boot, text appears in top left"
date: 2016-08-30
forum: General Help
---

### Post by abefroman99 on 2016-08-30
When I installed Ubuntu 16.04, I selected disk encryption, this worked great until a software update installed a new kernel.  Now when it boots I can't type in the textbox to unlock the disk and instead my typing appears in plaintext on the top left of the screen.  If I ctrl+alt+del and select the original kernel it works fine.

It appears similar to this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1391496]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1391496")

How can I fix this?

---

### Post by Jimysbil on 2016-08-30
I have to suggest you a semi-solution would be to set as default kernel your previous one by editing *_/etc/default/grub_* file.

Open a terminal and type:
```
sudo su
```
* It will give you root permissions
After that type:
```
gedit /etc/default/grub
```
When gedit opens change:
```
GRUB_DEFAULT=0
```
to your previous kernel number.(0 is the first option on grub menu)

Your "Advanced options.." should be:
```
GRUB_DEFAULT=1
```

So your old kernel inside the submenu should be:
```
GRUB_DEFAULT=1>3
```

# I am trying this now for myself because I have never use a default option on a submenu.

After my little try I saw the correct syntax of the command is like this:
 ```
GRUB_DEFAULT="1>3"
```

And something very important I didn't mention before.Run the command:
```
update-grub
```
in order to regenarate your grub configuration file or it won't work.

If your kernel is being updated and it's working , you may feel free to restore the default option to 0 and remove your old kernels.(I should advice you to remove the one it wasn't working just in case the new kernel has a bug.)

---

### Post by abefroman99 on 2016-08-31
I've reinstalled the OS and it works fine now, even with the latest version.

:confused:

---


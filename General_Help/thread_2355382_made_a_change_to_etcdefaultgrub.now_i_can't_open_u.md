---
title: "made a change to /etc/default/grub.now i can't open ubuntu 16.04."
date: 2017-03-12
forum: General Help
---

### Post by aliole4731 on 2017-03-12
let me begin by stating that i m a newbie.I was learning to make a bare os kernel.It required to add a menuentry to  grub.cfg.
i went to the folder /etc/default/grub and pasted this at the end :"
menuentry 'kernel 005' {
	set root='hd0,msdos1'
	multiboot /boot/kernel-005 ro
}  "
.i ran the command update-grub and restarted my laptop.
On startup it said "error:invalid magic number."

---

### Post by ajgreeny on 2017-03-12
You should have created a new entry for the grub.gfg menu configuration by editing the /etc/grub.d/40_custom file, not the /etc/default/grub file as you did.

Here's my 40_custom file as an example, which simply adds a **Reboot** and **Halt** option to the grub menu.
After editing you need to make the file executable with ```
sudo chmod +x /etc/grub.d/40_custom
``` then ```
sudo update-grub
```
I am not quite sure how you can overcome your current problem if you can not get into the Ubuntu OS to remove the edit you made and run the update-grub command again; the edit is easy with a live system but that will not update grub so you may need to look into a chroot environment to do that, or perhaps Boot-Repair in my signature will help.
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#
menuentry "Reboot" {
    reboot
}
menuentry "Halt" {
    halt
}

```

---

### Post by aliole4731 on 2017-03-12
I opened ubuntu with an older kernel .How can i undo the changes now?

---

### Post by oldfred on 2017-03-12
Delete your edits to grub.
 sudo nano /etc/default/grub 

And then add your boot stanza to as ajgreeny posted to edit 40_custom where you boot stanza should go.
And then update grub
sudo update-grub

Not seen multi-boot entry like you have?

 [http://askubuntu.com/questions/513234/how-to-compile-a-linux-kernel](http://askubuntu.com/questions/513234/how-to-compile-a-linux-kernel)

---

### Post by aliole4731 on 2017-03-12
> **oldfred said:**
> Delete your edits to grub.[l]("http://askubuntu.com/questions/513234/how-to-compile-a-linux-kernel")
how?the edits do not appear in etc/default/grub.
i'm thinking the changes were specific to a particular kernel and i made the changes to the latest kernel and since i can't open the latest kernel the changes do not appear in etc/default/grub.However,the changes do appear in boot/grub.cfg.

---

### Post by Dennis N on 2017-03-12
**/etc/default/grub** is for grub settings, like theme, colors, timeout setting, etc. through specific keywords such as:

GRUB_TIMEOUT=
GRUB_DEFAULT=
GRUB_GFXMODE=
GRUB_THEME=
etc.

These are not kernel specific. I doubt your added lines in post #1 are recognizable keywords, so would not transfer to grub.cfg and affect booting.

---

### Post by oldfred on 2017-03-12
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---


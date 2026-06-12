---
title: "Vista Boot Manager"
date: 2008-04-05
forum: General Help
---

### Post by Alterac on 2008-04-05
Pardon me for this totally beginner question...

I've got Vista installed first before Ubuntu.

My computer starts up with GRUB but I would like to use Vista's boot manager instead, to boot either vista or ubuntu.

How do I go about doing this?

---

### Post by LaRoza on 2008-04-05
The boot loader for Ubuntu is called "grub". It can handle many operating systems and is easy to use.

Windows doesn't like other operating systems, and if it is possible, it isn't worth the effort.

If you are worried about the Windows MBR being gone (which it is), get the Super Grub Disk (see the link in my sig), which can easily restore the Windows MBR to the way it was. Of course, Ubuntu or any other OS won't boot or even be an option.

If you want to change the default OS, you can do that too.

Runs this command (in terminal, or press Alt + F2):

```

gksudo gedit /boot/grub/menu.lst

```

Find this line:
```

# savedefault=false

```

Remove the # and change false to "true"

```

savedefault=true

```

When you select Windows (or whatever) it will use that as the default when it boots (after ten seconds)

---

### Post by Alterac on 2008-04-05
Hi, thanks for the help!

I think i kind of screwed my com up.

I tried doing the following on my own before reading your post:

1. Using vista, I removed the partition containing ubuntu and also the swap partition.

2. I reinstalled ubuntu, this time I clicked "advanced" and changed the location for the bootloader to hd(0,6) because ubuntu was to be installed to partition 6. The previous time I did not notice the "advanced" option and proceeded with the installation.

After the installation and rebooting, my computer failed to detect any boot manager.

As I do not have my vista cd on hand, I used the ubuntu live cd and followed some instructions online to move grub into the mbr (is that how it works?).

Now when I restart my com, I see grub with the option to boot ubuntu as well as vista. However vista still refuses to boot.

Please provide assistance.

At the moment I've downloaded super grub and am going to try it out.

Thanks in advance.

---

### Post by Alterac on 2008-04-05
I have now managed to access my windows recovery but cannot restore the MBR.

I think I should mention that when I try booting vista, I get "Invalid Partition Table." Is it gone?

---

### Post by LaRoza on 2008-04-05
> **Alterac said:**
> I have now managed to access my windows recovery but cannot restore the MBR.

I think I should mention that when I try booting vista, I get "Invalid Partition Table." Is it gone?

You did some weird things, and I am not sure of exactly what happened.

Restore the Windows MBR, use the Super Grub Disk, boot it:

Advanced->Windows (Advanced) and it is the first option.

Reboot the computer, Windows should boot with no hint of anything else. 

Use the Vista Disk Manager to delete the other partitions (we are going to restart this).

Now, if you want Ubuntu on this computer, install it to the freed space, but install Grub to the MBR. If you don't want Ubuntu, use the Vista disk managing tool to change the partitions to the way you want it.

---

### Post by Alterac on 2008-04-05
> **LaRoza said:**
> You did some weird things, and I am not sure of exactly what happened.

Restore the Windows MBR, use the Super Grub Disk, boot it:

Advanced->Windows (Advanced) and it is the first option.



Thanks for replying.

Losing hope that my vista is still okay.

After selecting the first option, there was an option to choose syslinux or something similar.

After that I had the option to reboot and I did.

The screen still came up with "Invalid Partition Table".

Is there no way around this other than using the Vista DVD? I do not have it at the moment and won't till a few days later.

---

### Post by Alterac on 2008-04-05
UPDATE:

I've fixed it. 

Using a Vista DVD I restored my startup.

Although GRUB is now the boot manager I'm happy just leaving it that way.

Thanks a lot for your help. :)

I'll take my time to slowly explore my ubuntu OS now. :guitar:

---


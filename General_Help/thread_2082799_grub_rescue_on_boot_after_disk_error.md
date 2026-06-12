---
title: "grub rescue on boot after disk error"
date: 2012-11-10
forum: General Help
---

### Post by FariAzz on 2012-11-10
Lately, I've been having Ubuntu crashing randomly.. it goes into read only mode, but once I restart it's working again.

Today it happened again and I had to manually shut the computer down.

Now I'm not able to boot anymore. I get the following when turning the computer on:

error: unknown filesystem
And I'm left at "grub rescue".

I booted from the Live CD and installed "boot-repair". When I run it it says "no os has been found on this computer", it gives me no option to carry out any fixes.

Boot Repair generated the following output which shows some errors: [http://paste.ubuntu.com/1348224/](http://paste.ubuntu.com/1348224/)

Any idea on how to fix this?

Ubuntu 12.10 64 bits

UPDATE:

-i'm trying to mount /dev/sda1 using: sudo mount /dev/sda1 /mnt   

But mount thinks it's a NTFS file system, which is not!! sda1 is a ext4 file system, I don't have Windows installed at all! This is the error I get from the command:

<code>
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
</code>

---

### Post by mardybear on 2012-11-10
Hi FariAzz.

I'm no linux expert. Have you emailed [email]yannubuntu@gmail.com[/email] as per the error message output on line 182 (assuming you have another method of emailing) ?

Quote: No OS has been found on this computer. Please report this message to [email]yannubuntu@gmail.com[/email]

Good luck,

mardybear

---

### Post by FariAzz on 2012-11-10
> **mardybear said:**
> Hi FariAzz.

I'm no linux expert. Have you emailed [email]yannubuntu@gmail.com[/email] as per the error message output on line 182 (assuming you have another method of emailing) ?

Quote: No OS has been found on this computer. Please report this message to [email]yannubuntu@gmail.com[/email]

Good luck,

mardybear

I haven't actually.. doing it right now!

---

### Post by FariAzz on 2012-11-10
SOLVED:

running: sudo fsck /dev/sda1 brought a list of errors within that partition, I selected "yes" for fixing each one of them.. it was a long list of directories, inodes, files.. after finishing I restarted the computer and it booted in Ubuntu as if nothing had ever happened!

---


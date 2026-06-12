---
title: "Can't change ownership of a auto-mount ntfs external drive"
date: 2007-10-25
forum: General Help
---

### Post by Neovos on 2007-10-25
I have a external hard drive that is connected via USB. I use it to store my music and it is formatted under NTFS. Normally when I turn it on, it's automatically detected and mounted on my desktop with no problem. I use exaile for my music and all is well until I go to change the ID tags. I get errors and it can't change them. I *suspect* the problem is a permission one because the drive when mounted says that it's owned by root. But the weird thing is that through nautilus, I can create, delete, and change file names. But when I use exaile or ex falso for the tags, it never works.

So I think that whatever program it is that handles the "auto-mount" process isn't giving the right parameters. But I'm unsure of what that program is. Fstab assumes the drive is always connected and is for mounting on startup right? So I don't think it's in there. When I click properties on the drive icon that shows up on my desktop, under volume it gives these conditions:

Mount Point: /media/Ajax
File System: fuseblk
mount options: rw nosuid nodev noatime user_id=0 group_id=0 allow_other

I assume it's that "user_id" I want to change but where do I do that so everytime I plug it in it gives it the right user id?

Oh yeah, and I've tried sudo nautilus and doing it graphically, but it automatically changed back to root. I've tried "sudo chown -R me:me /media/Ajax" and it looked like it was working for a minute then finished, but nothing changed.

---

### Post by Neovos on 2007-10-31
I found the fix. This is a common problem on pre-"ntfs-3g" posts in which people changed some mount options using various methods. But nothing really referenced a straightforward method using the elegance of the ntfs-3g driver. All I needed to do was use the "Configuration Editor" in Apps > System Tools, go to system/storage/default_options/ntfs-3g and make sure the following values were present:

locale=
exec
umask=077   (this was not present before)
gid=1000  (not present, this is my user group)
uid=       (also not present)

So these are the "ntfs-3g defaults" that get referenced in fstab and such. Hope this helps someone else. This was incredibly frustrating for too long.

---


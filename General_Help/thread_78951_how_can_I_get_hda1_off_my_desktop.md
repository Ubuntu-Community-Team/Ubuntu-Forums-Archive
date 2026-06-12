---
title: "how can I get hda1 off my desktop?"
date: 2005-10-19
forum: General Help
---

### Post by chimera on 2005-10-19
Please you have to help me,I'm allergic to any icons blocking my wallpaper.
There is a large hda1 icon on my desktop(I didn't put it there,it was there since I installed breezy),how do I get it out of there?

---

### Post by manicka on 2005-10-19
alt-f2
gconf-editor

apps-->nautilus-->desktop-->

uncheck volumes visible

---

### Post by chimera on 2005-10-19
thanks,now I can again see my wallpaper in it's full glory,not obscured by an ugly white HD icon :D

---

### Post by hajk on 2005-10-19
...but at the next reboot it will be back!

So, "sudo gedit /etc/fstab" and change the options of /dev/hda1 from
"defaults" to "ro,noauto,user" (assuming that it is a Windows partition that you don't want to write to). The partition can then still be mounted when needed.

---

### Post by A-star on 2005-10-19
[QUOTE=hajk]...but at the next reboot it will be back!
[/QUOTE]

I used the method described above (the one using the gconf editor).
And after I rebooted the icons didn't come back.
So I don't think that it is really necessary to edit your fstab.

---

### Post by hajk on 2005-10-19
...OK, but it will still be mounted, no? Is that what you want? If not, edit 
/etc/fstab.;)

---

### Post by Erin on 2005-10-19
I think recommending anyone to edit fstab without a health warning first is dangerous. hda1 is normally the default '/' partition on a pure *nix boxen.

---

### Post by Jeff Hunter on 2005-10-19
[QUOTE=hajk]...but at the next reboot it will be back!

So, "sudo gedit /etc/fstab" and change the options of /dev/hda1 from
"defaults" to "ro,noauto,user" (assuming that it is a Windows partition that you don't want to write to). The partition can then still be mounted when needed.[/QUOTE]
Question:  What do I make it if it is a Windows partition I DO want to write to, without taking it off the desktop?  Where would I find a good description of the switches and options for fstab, so I can know what all of those mean?

---

### Post by wjp.reg on 2005-10-19
[QUOTE=Jeff Hunter]Question:  What do I make it if it is a Windows partition I DO want to write to, without taking it off the desktop?  Where would I find a good description of the switches and options for fstab, so I can know what all of those mean?[/QUOTE]

This should help

[http://www.ubuntuguide.org/#mountunmountntfs]("http://www.ubuntuguide.org/#mountunmountntfs")

---

### Post by manicka on 2005-10-19
I'd only give write access to a  fat32 drive. Writing to a ntfs drive is hazardous.

---

### Post by Rovenhot on 2005-10-19
I think it is clear that all chimera wanted was to be rid of his hard drive icon from his desktop, not to unmount it, because as he said, he was 'allergic' to icons obscuring his wallpaper.

---

### Post by unclben on 2005-10-19
If you mount the drive to /mnt instead of /media, it will not appear on your desktop.

---

### Post by Saiboogu on 2005-10-19
[QUOTE=unclben]If you mount the drive to /mnt instead of /media, it will not appear on your desktop.[/QUOTE]

I have 5 volume icons on my desktop (local ext3, ntfs, and reiser partitions, and a samba share) which all are mounted to /mnt and show on my desktop. Mounting in /mnt does not prevent them from appearing.

This isn't a problem, I enjoy having all my drives on the desktop. Just thought I'd make that point, though. :)

---

### Post by souled on 2005-10-19
If this still isn't solved, just open up Configuration Editor and go to apps-->nautilus-->desktop.  There is a key "volumes_visible" just uncheck that box.

---

### Post by unclben on 2005-10-19
[QUOTE=Saiboogu]I have 5 volume icons on my desktop (local ext3, ntfs, and reiser partitions, and a samba share) which all are mounted to /mnt and show on my desktop. Mounting in /mnt does not prevent them from appearing.[/QUOTE] Hmmm...good to know. It worked for me, though. :shrugs:

---

### Post by RAOF on 2005-10-20
Actually, I think just removing the "user"/"users" from the fstab line will take the drive off the desktop.  For example, the line:

```
/dev/sda1   /mnt/WinXP    ntfs    defaults,umask=000    0    0
```

Will mount (my) windows NTFS drive to /mnt/WinXP, giving everyone read-write-execute priviledges, and not show up on the desktop.  (The write priviledges are moot, though.  There's no ntfs write support in the ubuntu kernels, and the best support you can hope from a vanila kernel is to be able to overwrite existing files)

Note:  this fstab line is from memory.  The important stuff (the options - defaults,umask) is there, but **don't blindly copy it** - it probably won't work for you :)

---


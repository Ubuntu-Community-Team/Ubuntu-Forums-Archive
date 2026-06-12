---
title: "FAT and gnome-volume-manager, autofs, pysdm"
date: 2007-04-21
forum: General Help
---

### Post by igor.d on 2007-04-21
Hi everybody,

1. I installed Edgy one month ago. I have two hard discs and multiboot environment: Vista, Win x64 and Ubuntu Edgy. This time I made my Ubuntu my primary desktop workplace.

2. I'm using FAT partition for data storage and sharing. I haven't made any changes to the system when problems started. First it was FAT partition - it would randomly lock files (deny access) to my normal user account. I noticed it would happen soon after I access those folders or files moving or copying some of them from my account. After that I would have to [COLOR="Red"]sudo su[/COLOR] and [COLOR="Red"]chown[/COLOR] or [COLOR="Red"]umount/mount[/COLOR] to get permissions back.

3. After some time and investigation I decided to install [COLOR="Red"]pysdm[/COLOR]. Using it I changed permissions to my FAT partition and that was OK for some time (I wasn't looking at /etc/fstab).

4. I have small home network of 3 PCs and I decided to share mounted FAT partition (it contains movies and music and pictures) to my family. I wasn't successfull - other PCs couldn't access shared FAT because of user right permissions.

5. I have working Samba deamon. I can share other data, I have several protected and public shares etc. That made me finally look at /etc/fstab.

6. My fstab now have [COLOR="Red"]duplicated entries[/COLOR] which is very bad. There are ones created by gnome-volume-manager I suppose and ones created by pysdm. 

7. My next step was to update system and I almost regret it because I had to recompile several applications like virtualbox etc. After that I tried installing [COLOR="Red"]bom[/COLOR] boot manager but there is no option to disable gnome-volume-manager. I als have fear that by disabling gnome-volume-manager I would lost DVDRW and USB automount option but I believe I have to do that.

My question is:
How to completely disable gnome-volume-manager?

---


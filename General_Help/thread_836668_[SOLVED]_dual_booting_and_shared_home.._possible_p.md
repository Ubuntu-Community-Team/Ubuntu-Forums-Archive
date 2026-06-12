---
title: "[SOLVED] dual booting and shared /home.. possible problems?"
date: 2008-06-21
forum: General Help
---

### Post by jerome1232 on 2008-06-21
I thinking about multi-booting XPSP3, Fedora 9, Ubuntu 8.04
partition 1 XP 40GB
Partition 2 /boot 512 MB
Partition 3 Extended 
 volume 1 linux swap 1 GB;
 volume 2 / (ubuntu) 10 GB
 volume 3 / (fedora) 10 GB
 volume 4 NTFS mounted as My Documents 10 GB
 volume 5 /home (shared between Ubuntu/Fedora) left over space

now my question is, /home/'user' contains settings for the majority of my programs, so if I share /home, won't programs under Ubuntu/Fedora mess with each others settings? Or do they behave well using the same configs

---

### Post by lswb on 2008-06-21
You can expect many setting conflicts because of all the .files (hidden files) that are usually found in a home directory. I recommend keeping a separate home for each OS, but make a separate partition for files that you may want to access from any OS, then you can make symlinks to them from your home directories (or shortcuts in XP). Or you could just store the files in a directory on one of the bootable partitions, and make the links to them. For instance, I have a laptop with XP, dapper, and hardy installed. I store music files and pictures on the XP partition. In my $HOME in dapper and hardy, I have symlinks on my desktop that point to the directories in the XP partition where they are stored. You'll need to put appropriate entries in /etc/fstab to make this work. I've also changed the "Pictures" directory in my $HOME into a symlink to the directory on the XP partition also, so that it shows up in "Places" on my main menu. In the outline you've proposed, you could store similar files in directories in the "My Documents" partition.

---


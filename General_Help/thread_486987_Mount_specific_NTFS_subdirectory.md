---
title: "Mount specific NTFS subdirectory"
date: 2007-06-28
forum: General Help
---

### Post by unnes on 2007-06-28
I recently installed Kubuntu Feisty on a new partition on my previously Vista-only laptop, and frankly, I'm floored at how Vista and Feisty play nice together. I was expecting headaches, but Feisty can read and write to the Vista partition with ease, and it runs more smoothly than I could have hoped.

Currently, I have the entire Vista partition mounted as follows in fstab:

```
dev/hda1   /media/hda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
```

However, I don't really need (or want) access to the entire partition from Feisty. Ideally, I'd be able to mount C:\users\unnes\videos to /home/movies, C:\users\unnes\music to /home/music , etc.

Is there any way to mount specific subdirectories instead of the entire partition? Or am I forced to navigate through a tree of convoluted paths each time I want to access a file on the NTFS partition?

---

### Post by Enki on 2007-06-28
You could just create a symbolic link to the desired location, under your home folder for instance.

(in GNOME) if you mount to /mnt instead of /media the partition doesn't have a shortcut on the desktop

---

### Post by unnes on 2007-06-28
Forgive my ignorance -- and to think I thought I knew what I was doing! I guess I've been spoiled by simple-to-use Debian derivatives.

How would I go about using symbolic links to do what I want in KDE?

---

### Post by Enki on 2007-06-30
To remove the diskdrive icon to hda1 from your desktop, open up a terminal and type:
```
sudo mkdir /media/vista
```

then edit fstab like this:
```
dev/hda1   /media/vista   ntfs-3g  defaults,locale=en_US.utf8    0    0
```

Make sure you don't have any files from your ntfs partition open and type this in a terminal:
```
sudo mount -a
```
to make the changes effective, or simply reboot.

To create a symbolic link, in a terminal type:
```
ln -s /media/vista/users/unnes/videos /home/unnes/movies
```
It's like a windows shortcut, except that for all intents and purposes, it will behave like a real directory. You can probably do the same by right-clicking in konqueror -> create link or something, but I've never used KDE.

Of course, the volume will still be mounted entirely, I don't think there's a way to do exactly what you asked.

---

### Post by Enki on 2007-07-01
Whoops:
mount under /media -> annoying shortcut on desktop
mount under /mnt -> no shortcut

---

### Post by Philosophicles on 2008-05-05
*bump* - apologies, but this seems the most relevant place for the following.

I was also after a similar solution to unnes.  On the assumption that that is not possible, does anybody know if it's possible, having mounted an NTFS partition at, e.g., /windows, to set the *permissions* differently for a subdirectory (my windows 'home' directory) from the partition as a whole (I have a 'windows' user and group that own everything currently)?

With NTFS-3g (stable write-support to ntfs) this would allow me to actually set /windows/[stuff]/[myusername]/documents to be my home directory, ~, and bypass the need for symlinks (which has been my solution for a while now).

EDIT: D'oh, ignore this - I've just realised this is in the archive.  Question will be re-asked in an active room.

---


---
title: "Changing User Directories"
date: 2013-06-02
forum: General Help
---

### Post by foberle on 2013-06-02
Hi-

Sorry for asking this - I know there are many, many posts and responses that seem to be related to this, but some are obviously obsolete (and sometimes not so obviously), and several conflict with each other, so I thought I would explain what I'm trying to do and look for any advice I can get.

First, I'm using 64 bit Ubuntu 12.04 LTS. I have a dual boot system (with a Redmond OS on a separate partition). I have had, for a long time, multiple physical hard drives, and multiple partitions on each of these drives. I currently share many of these drives (partitions) with both OSs as well as with an older version of Windows running in Oracle's VM to support some ancient software that I still use.

I've done this by automounting each drive/partition in fstab, and then assigning Bookmarks in Nautilus for easy access to everything in Ubuntu. Works fine. BUT:

I would like very much to remove/hide/whatever the "standard" Ubuntu directories for Documents, Music, Pictures, and Videos and point them to the appropriate partitions that I already use for such things. To do that, I tried modifying the $HOME/.config/user-dirs.dirs file, changing the default line [XDG_DOCUMENTS_DIR="$HOME/Documents"] to [XDG_DOCUMENTS_DIR="/mnt/Documents"] for instance. After a little experimentation, I've come to the conclusion that locations that don't begin with "$HOME" aren't recognized, leading me to suspect I might need to move the entire home directory somewhere else, but from what I've read in many posts that seems a little over the top and possibly risky.

I also added a line: XDG_DEVELOPMENT_DIR="/mnt/Development". I wasn't too surprised that this did absolutely nothing, but the comments at the file heading used "XDG_xxx_DIR" so I thought it was worth a shot. Can I assume that only certain keywords (e.g. DOWNLOAD, MUSIC, etc.) are supported.

Another thing I noticed is that there are lines in user-dirs.dirs for XDG_TEMPLATES_DIR and XDG_PUBLICSHARE_DIR; although the directories they point to exist, these items don't show up in the Nautilus sidebar. I can access these directories, but this behavior seems somewhat inconsistent to me - likely confirming that I don't really understand what's going on.

I've googled XDG and found lots of references, but nothing that just says how to use these things. Does anyone either know how to do what I'm trying to do, or know of a good explanation somewhere?

In addition to separating "my stuff" from the operating systems stuff so I can easily upgrade versions, my intention is to make backups more organized. Some of my partitions represent totally different lives/hobbies/whatever and it makes sense to me to keep them isolated.

Thanks much for any pointers or advice....

---

### Post by Cheesemill on 2013-06-02
Why not just delete the empty directories and create symlinks pointing to the actual location you want to use. This is exactly what I do ...
```
rob@arch:~$ ls
total 44K
-rw-r--r-- 1 rob users 9.5K Jan 25 16:59 archlinux-logo-white-scalable.847eeafd581c.svg
lrwxrwxrwx 1 rob users   14 Jun  1 22:47 bin -> /mnt/data/bin/
drwxr-xr-x 1 rob users    0 Jun  1 22:46 Desktop
lrwxrwxrwx 1 rob users   20 Jun  1 22:47 Documents -> /mnt/data/documents/
lrwxrwxrwx 1 rob users   20 Jun  1 22:47 Downloads -> /mnt/data/downloads/
lrwxrwxrwx 1 rob users   15 Jun  1 22:49 Emulation -> /mnt/emulation/
lrwxrwxrwx 1 rob users   15 Jun  1 22:47 ISOs -> /mnt/data/isos/
lrwxrwxrwx 1 rob users   16 Jun  1 22:47 Music -> /mnt/data/music/
drwxr-xr-x 1 rob users   54 Jun  2 11:26 OpenELEC
lrwxrwxrwx 1 rob users   19 Jun  1 22:47 Pictures -> /mnt/data/pictures/
lrwxrwxrwx 1 rob users   17 Jun  1 22:48 Videos -> /mnt/data/videos/

```

First of all make sure the directory you want to point to a different location is empty then run the following commands, I'll use the Music folder in this example...
```
rm -rf ~/Music
ln -s /mnt/data/music Music
```

This way you don't have to mess about with any of the XDG stuff, as the default Music folder now just points to a different location.

---

### Post by ajgreeny on 2013-06-02
I used to do exactly what Cheesemill suggests when I had five OSs on one machine.  Not wanting to duplicate all the data files etc etc I just linked the main OS's default folders, ie, Documents, Downloads, Music, etc etc to new empty ones of then same name in the home folders of the other four OSs.  It all worked faultlessly.

---

### Post by Morbius1 on 2013-06-02
The other way to do this is to "bind" one directory to the other. Taking the Music folder above as an example you would add the following to the end of fstab:
```
/mnt/data/music /home/morbius/Music auto bind 0 0
```

Whatever add / deletes or changes to permissions or ownership you do in your Music home folder happens to /mnt/data/music. Samba won't follow a symlink ( unless you do something Samba considers a security problem ) but it has no problem with a bind if file sharing is also a requirement.

---


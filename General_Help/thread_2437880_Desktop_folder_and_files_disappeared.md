---
title: "Desktop folder and files disappeared"
date: 2020-03-02
forum: General Help
---

### Post by kalyp on 2020-03-02
Hello,

I ran into this exact issue this morning: [https://askubuntu.com/questions/182917/desktop-folder-and-files-disappeared](https://askubuntu.com/questions/182917/desktop-folder-and-files-disappeared), meaning that my home directory was shown on my Desktop and (I presume) the Desktop folder went missing. 
Unfortunately in my case, by the time I noticed it I had downloaded a file that created a new Desktop folder (my downloads are saved on the Desktop), which is why I think the Desktop folder had disappeared. And when I corrected the user-dirs.dirs file, this new Desktop showed up and my old one is still missing. I have no idea where it is; I tried deleting the new one and restarting but the old one did not reappear (an empty one was created instead). I don't remember the filenames of what was in it, which makes it tricky to search for (and it might have been simply deleted anyways). I have no backup.

None of these files are crucial, but I very much would like to recover them still. Any idea where they might be and/or if they're recoverable? 

Thanks in advance!

---

### Post by deadflowr on 2020-03-02
What version of Ubuntu?

---

### Post by kalyp on 2020-03-02
Sorry should have mentioned it. Running 18.04.4 LTS.

---

### Post by oldfred on 2020-03-02
Post these:
cat $HOME/.config/user-dirs.dirs
cat /etc/fstab
lsblk -f

---

### Post by kalyp on 2020-03-02
```
XX@YY:~$ cat $HOME/.config/user-dirs.dirs
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

[This is after I modified the file to add back "Desktop" following the instructions at the link I mentioned in my first post. The first 2 lines were $HOME instead of $HOME/Desktop before. The Desktop is now showing normally, but it is the "new" (empty) Desktop not the one I had this morning.]

```
XX@YY:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9b0a43d1-1be9-4e7d-8884-b4fa8ff898b2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=896d28cc-5f4d-4e00-8da9-010a835b12ff /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=9af99a88-b8be-473d-aa67-50abd867fd87 none            swap    sw              0       0
```

```
XX@YY:~$ lsblk -f
NAME   FSTYPE   LABEL UUID                                 MOUNTPOINT
loop0  squashfs                                            /snap/skype/112
loop1  squashfs                                            /snap/pdftk/1
loop2  squashfs                                            /snap/canonical-livepatch/94
loop3  squashfs                                            /snap/canonical-livepatch/93
loop4  squashfs                                            /snap/youtube-dl/2638
loop5  squashfs                                            /snap/youtube-dl/2209
loop6  squashfs                                            /snap/core/8592
loop7  squashfs                                            /snap/core18/1668
loop8  squashfs                                            /snap/pdftk/9
loop9  squashfs                                            /snap/core/8689
loop10 squashfs                                            /snap/skype/109
sda                                                        
&#9500;&#9472;sda1 ext4           9b0a43d1-1be9-4e7d-8884-b4fa8ff898b2 /
&#9500;&#9472;sda2 swap           9af99a88-b8be-473d-aa67-50abd867fd87 [SWAP]
&#9492;&#9472;sda3 ext4           896d28cc-5f4d-4e00-8da9-010a835b12ff /home
```

Thanks!!

---

### Post by oldfred on 2020-03-02
So does sda3 have corruption and not mounting when you reboot, so it auto creates a new blank default /home?

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda3
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda3

---

### Post by kalyp on 2020-03-02
There is no corruption on sda3 that I am aware of? the /home has no issues, only Desktop did. Home has been mounting properly.
I can run e2fsck tonight but even if the old Desktop was corrupted, now that a new Desktop has been created, I am not quite sure what would happen...

---

### Post by kalyp on 2020-03-03
As an update, I ran e2fsck and nothing changed (no issues were found with the partition, either).

---

### Post by ajgreeny on 2020-03-03
Try running commands ```
sudo updatedb
locate Desktop
```
This may find another folder named Desktop that you have inadvertently moved elsewhere from its usual place in home and may allow you to replace it.

Can you remember what files or folders you had in Desktop? It looks as if it was the default folder for downloads on your system.

---

### Post by kalyp on 2020-03-03
Nothing showed up with the locate Desktop :( 

Your point about the default download folder was brilliant, though. While I couldn't remember the names of files & folders enough to do a search on them, I hadn't thought about the fact that chrome would give me the history of downloads and thus, the name of some files that were on my Desktop (a few I knew I hadn't deleted, especially since they are not in the trash). A search on them didn't return anything so I guess my files are truly gone... 

I guess I'll be more careful in the future about not keeping anything of value on the Desktop. That is one weird bug though. The only thing that I could have done was a \rm -R on the Desktop, and I am 99.9% sure I didn't do that (that would have been an unlikely thing to miss).

Thanks for the help!

---

### Post by dragonfly41 on 2020-03-03
Running the command ```
history
``` will reveal the history of terminal commands run.

---


---
title: "Help with basic rsync command"
date: 2017-10-12
forum: General Help
---

### Post by thanhmy on 2017-10-12
A quick newbie question about a linus command.
I am trying to move the /home folder to 2nd HDD and little confused, the below command has two periods, (.), are these needed? Both after /home .


"sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/."

-------------------------------------------------------------------------------------
Hello, my name is Myca, nice to meet Everyone. [giup viec nha]("http://giupviecvietmy.com/dich-vu-giup-viec-gia-dinh/dich-vu-giup-viec-nha-an-o-lai") | [giúp vi&#7879;c nhà]("http://giupviecvietmy.com/dich-vu-giup-viec-gia-dinh/dich-vu-giup-viec-nha-an-o-lai")

---

### Post by SeijiSensei on 2017-10-12
Put the --exclude after the source and target.

```

cd /
sudo rsync -av home /media  --exclude=*.gvfs*

```

will copy the entire /home to /media/home except for any .gvfs directories.

---

### Post by oldfred on 2017-10-13
I use an exclude file as there are several sub-folders with cache, temp files, thumbnails, etc that you do not need to copy. 

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**

---


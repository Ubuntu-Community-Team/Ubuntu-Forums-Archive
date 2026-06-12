---
title: "Failed to rename file. File exists. error"
date: 2007-05-29
forum: General Help
---

### Post by rumo_orbis on 2007-05-29
I ran across a very weird bug/error/strange-wanted-behaviour when trying to rename a song on my external harddrive, which is fat formatted. I tried to change lower case letters into CAPITAL ones. And it couldn't rename them because of "Failed to rename file. File exists.". 
I guess this is caused somehow because fat is not case sensitive; when i tried to rename them on my internal ext3 partition it worked flawlessly. Strange is though there is indeed no file with the same name, just the one that should be renamed...

anyone knows anything that may help. or do i have to move my files on a ext3 partition in order to change lower case to upper case...?

thanks. rumo.

---

### Post by rumo_orbis on 2007-05-29
I know see that other people have the same problem... and it seems to be "just the way it is". but i still dont understand why. does anyone know?

rumo

---

### Post by fanatik on 2007-05-29
yeah FAT formatted filesystems don't distinguish between upper and lower case filenames, whereas ext3 does. you could mount the FAT filesystem with different mount options, look at man mount and in particular at the shortname option. you can change this in your /etc/fstab if there is an entry for your external hard disk already, i'm not sure where it's set if there isn't.

HTH

---

### Post by rumo_orbis on 2007-05-29
yeah i guess that would be an option... but unfortunately not for me i think. the problem is that i also have a lot of russian files and was very happy with (x)ubuntu because of its thorough utf support. i guess this would not work with the short name option?
anyway, as i only use my external harddrive for my music i'll just move the files on my ext3 partition for renaming and tagging and then move them back.

anyway thanks for the help... argh i hate windows for using ntfs and not supporting ext3 and forcing me to use fat on my external for compatibility (as ntfs still has  issues on linux)...

anyway, thanks for the help
rumo

---


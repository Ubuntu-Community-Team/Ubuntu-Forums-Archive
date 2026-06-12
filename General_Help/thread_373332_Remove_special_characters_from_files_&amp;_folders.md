---
title: "Remove special characters from files &amp; folders"
date: 2007-03-01
forum: General Help
---

### Post by aderby on 2007-03-01
Hi,
A while back I used Sound Juicer to convert my CD collection to MP3's.  However, I made the mistake of not ticking the "Remove Special Characters" option.  Now I've got a bunch of files & folders that can't be backed up to DVD or copied to my FAT based MP3 player.  I'm sure a bulk rename, replacing the special character's with an underscore, can be done via the shell or a script but it's well beyond my level of skill. I'm having no joy searching for a solution, so if anybody could point me in the right direction I'd appreciate it.
Thanks,
Andrew.

---

### Post by LotsOfPhil on 2007-03-01
I am not sure what special characters you want to get rid of, but it is easily done, as you suspected.

```
#!/bin/bash
find . | while read f
do
        new=`echo ${f//[-"$"\!\ ]/_}`
        mv "$f" "$new"
done

```

Just put all your special characters in the [ ]. You'll probably need to escape them all. Might want to try it with 'cp' instead of 'mv' the first time.

---

### Post by aderby on 2007-03-01
Thanks a lot for the helpful reply.  It didn't work for me 100% as it seemed to have trouble with some of the folders (spaces in the folder names?) but it was good enough for me to bodge it.  I copied the whole music folder to a fat32 backup drive I have and ran the script within each of the folders that failed to copy.
Thanks again.

---

### Post by LotsOfPhil on 2007-03-02
Glad it sorta worked :) If you want me to tweak it, you can post an ls that didn't work right and I'll fix it.

---


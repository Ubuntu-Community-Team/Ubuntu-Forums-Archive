---
title: "Rdiff-backup. I can't figure the include-filelist out."
date: 2023-01-01
forum: General Help
---

### Post by Tadaen_Sylvermane on 2023-01-01
Here is what I've been working on. Relevant parts so don't have to search. Fairly large script.M This script runs as root and loops through the user folders in /home

```
DIRBLOCKTMP=/tmp/userbackups.ignore.tmp
# directories  in user folders to block from duplicity and
# do with rdiff-backup
DIRECBLOCK=".kodi 
.minecraft
.var
.steam 
.wine 
.gnupg 
.thunderbird 
.local/share/Steam 
Videos 
Pictures 
Downloads"
```

```
# stage 4 make sure rdiff-backup is installed & create backup of rarely 
    # changed data

    which rdiff-backup && RDIFFBACK=y
    
    [ -f "$DIRBLOCKTMP" ] && rm "$DIRBLOCKTMP"
    
    echo "$DIRECBLOCK" | while read line ; do
        echo "/home/${CURUSR}/${line}" >> "$DIRBLOCKTMP"
    done

    if [ "$RDIFFBACK" = y ] ; then
        su -c "rdiff-backup \
            --exclude /home/${CURUSR}/Videos \
            --exclude /home/${CURUSR}/Downloads \
            --include-filelist \"${DIRBLOCKTMP}\" \
            --exclude /home/${CURUSR} \
            /home/${CURUSR} ${DATADIRPATH}" "$CURUSR"
```

So my problem I only want to include the variable list and ignore everything else. But I want to be able to add / remove from list without having to manually edit the rdiff-backup command, just the variable up top. I really don't know what's wrong. Took me awhile to get this to work. But the problem and I can't figure why is that it runs for a long long time. An initial backup of the folders usually takes less than 5-10 minutes (60gb give or take). However I got this going, with and existing backup and I left to pick up a pizza. It was still running 30+ minutes later. I'm unsure of what it's doing exactly I guess and what I am doing wrong.

---

### Post by Tadaen_Sylvermane on 2023-01-01
I figured it out finally. End result.

```
echo "$DIRECBLOCK" | while read line ; do
        echo "/home/${CURUSR}/${line}" >> "$DIRBLOCKTMP"
    done
    echo "- /home/${CURUSR}/**" >> "$DIRBLOCKTMP" # i had the list formatted wrong. Had to add this at the end.

    if [ "$RDIFFBACK" = y ] ; then
        su -c "rdiff-backup \
            -v 5 \
            --exclude /home/${CURUSR}/Videos \
            --exclude /home/${CURUSR}/Downloads \
            --include-globbing-filelist \"${DIRBLOCKTMP}\" \
            --exclude /home/${CURUSR} \
            /home/${CURUSR} ${DATADIRPATH}" "$CURUSR"
```

Setting the verbosity was what told me. It was taking so long because it wasn't reading the folders properly. As such it was backing up nothing but the upper folder. I deleted my initial backup and then ran it again and it finished in 5 or 6 seconds. Then the googling and here we are. It works :)

---


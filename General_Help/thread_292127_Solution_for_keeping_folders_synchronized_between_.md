---
title: "Solution for keeping folders synchronized between several computers?"
date: 2006-11-03
forum: General Help
---

### Post by daveisadork on 2006-11-03
Basically, I'm looking for a way to keep certain files and settings synchronized between 3-5 computers. For example, I have run into a problem in the past where I needed a chat conversation I had on a different computer than the one I was using. Thus, it would be nice if all my chat logs were on all of the computers I use like Google Browser Sync does with history, bookmarks and cookies for Firefox.

I've considered using iFolder for this, but I'm wondering if anyone here has a better suggestion.

---

### Post by anthro398 on 2006-11-03
I do this between 3 or 4 computers using rsync.  I wrote a little script that goes something like this:

```

#!/bin/bash

#mount remote machine over samba
mount -t smbfs -o credentials=/home/me/.scripts/credentials,uid=me,gid=users //dmz/data /mnt/dmz-data

#copy local data to remote
rsync -avv Documents/ /mnt/dmz-data/Documents

#copy remote data to local
rsync -avv /mnt/dmz-data/Documents/ Documents

#unmount remote machine
umount -l /mnt/dmz-data

```

That way, I benefit from the speed of rsync by copying new or changed data to the remote machine and then copying new or changed data from the remote machine.  I add an alias to my ~/.bash_aliases file and uncomment the aliases loading section of ~/.bashrc so that I can type 'sudo backup' into the the cli and it backs up both ways. One could also use sshfs, I suppose, or use the -e flag in rsync to tell it to use ssh as the tranport protocol.  I just do it this way because it was simple.

Then, when you want to delete or reorganize your data, you have to manually use the rsync --delete flag.  Pretty simple.

You could also specify certain files to cp over.  See my script for remote tar backups, "Remote backup bash script", [here]("http://www.prairienet.org/~jtuttle/projects.html").  One could easily modify that to use cp instead of taring and compressing the data.

---


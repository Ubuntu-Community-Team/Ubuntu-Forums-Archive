---
title: "Restoring Duplicity backup files?"
date: 2013-10-27
forum: General Help
---

### Post by jimford on 2013-10-27
I've stored my backups on [www.box.com](www.box.com) using Deja-Dup, but can't now restore any of the files.

I can download the backup archive to my local machine OK.

I understand that Deja-Dup is a front end for Duplicity. Is there a way I can read and restore my files directly using Duplicity, please?

Jim

---

### Post by gamblor01 on 2013-12-04
So I just ran through something similar to this.  If you can access the files locally then it should follow about the same scenario that I used, but basically you just need to modify the access protocol that you use (http vs. sftp vs. file and so on).

Let's just assume all of your files are stored to some location that you mounted as /backup.  I was able to do the following to list the contents of the backups:

```

duplicity --no-encryption list-current-files file:///backup

```

Again, just modify the protocol if you want to access something else.  For example, if you had the files stored on another server that allows SSH/SFTP access:

```

duplicity list-current-files sftp://user@other-machine:/path/to/backup

```


So I was looking for a very specific file because it looks like my upgrade to Ubuntu 13.10 overwrote the previous version that I had for 13.04 and I didn't necessary want to RESTORE that file (which would overwrite the contents of the file)...I just wanted to extract that file and then be able to diff it to the existing file.  As much as I dislike Apple, doing this with Time Machine backups would be incredibly simple.  Just navigate to the appropriate date and then drag/drop the file anywhere (~/Desktop maybe?).  Now I can easily diff with whatever utility I want.
 

So let's say I want my php.ini file.  I made sure it exists in the archive just by grep'ing through the output (maybe there is a better way, but my backups are relatively small so it doesn't take more than a few seconds for me to get the output):

```

duplicity --no-encryption list-current-files file:///backup | grep "php.ini"

```


This gives me output showing that the file exists at "etc/php5/apache2/php.ini" ... so now I can just restore that one file to my /tmp directory like so:

```

sudo duplicity --no-encryption --file-to-restore etc/php5/apache2/php.ini file:///backup /tmp/php.ini

```


For some reason it gave me an access error without sudo (maybe it's trying to write some lock file or other temp file to a filesystem I don't have write access on?) so I just added sudo to the front of it and it successfully retrieved the file.


If you have deleted files and want to simply restore the entire contents of the backup, or maybe just one file/directory in the backup, I think you do it with the restore option for duplicity.  Something like:

```

duplicity restore Documents/my-saved-directory

```

This would restore the entire contents of that directory back to your filesystem.


I'm still not expert but I was at least able to list my files to find what I want in the backup, and then retrieve the one I wanted to a temp location so that I could do a diff.  Hopefully this helps you.  Further examples that I thought were pretty good can be found here:

[http://duplicity.nongnu.org/duplicity.1.html](http://duplicity.nongnu.org/duplicity.1.html)



Even then I still think the documentation for this program is a bit lacking.  Further examples would be nice so if you find something or you figure out how to accomplish what you are trying to do, please feel free to share.

---


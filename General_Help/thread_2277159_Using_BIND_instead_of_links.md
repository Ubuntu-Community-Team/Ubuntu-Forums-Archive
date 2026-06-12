---
title: "Using BIND instead of links"
date: 2015-05-07
forum: General Help
---

### Post by Ubu1son on 2015-05-07
I'm trying to set up using Bind for the home folders, I seems to work, but once again, I have a problem with moving files to trash.


As an example, I have set it like this ( using Bind script posted by Morbius1 here [http://ubuntuforums.org/showthread.php?t=2192848&p=12870240#post12870240](http://ubuntuforums.org/showthread.php?t=2192848&p=12870240#post12870240) ):

```

start on stopped mountall

script
mount --bind /data/user/Pictures /home/user/Pictures
end script
```

Now, if I create a file in the home/user/Pictures folder, it will show in the data/user/Pictures folder too.

But if move the file to trash in the home/user/Pictures folder, it will create a home/user/Pictures/.Trash folder and move it in there.  
The rubbish icon doesn't change and there is nothing to empty in the rubbish bin (so the files that are moved to trash are taking up space and cant be emptied ).

However, if I move the file to trash while in /data/user/Pictures folder, no .Trash folder is created, and the file is moved to the default .Trash folder on the partition ( /data/.Trash ).
The Rubbish icon shows rubbish, and it can be emptied.


So, how can I fix this, or is it a limitation of using Bind?



Thanks.

---

### Post by Ubu1son on 2015-05-07
Also tried using bind option in fstab instead, same result...... trying symlink again

---


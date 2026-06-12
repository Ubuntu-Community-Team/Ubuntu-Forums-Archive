---
title: "Script to limit the size of Trash"
date: 2006-12-15
forum: General Help
---

### Post by jazzgossen on 2006-12-15
I'm writing a script to manage the size of the .Trash directory (and .thumbnails, and any other directory that needs to be pruned) to remove the oldest or largest files after the size of the directory when it reaches a certain limit. But I just thought that maybe someone else already made such a script. Do you know of one, or should I try to finish mine?

---

### Post by yota on 2006-12-15
Nice idea!

I'm not aware of already existing solutions, but adding something like:
```

[ $(du -sm ~/.Trash/ |awk '{print $1}') -gt #SIZE IN MB# ] && rm -rf ~/.Trash/*

```

to the user crontab should do the trick...

Hope it helps.

--EDIT: sorry! I forgot to handle the file age...  I'll post something better soon.

---

### Post by yota on 2006-12-15
Here we are with age handling (note that today's files are not deleted):
```

#!/bin/bash

limit=7
size=100

while [ $limit -gt 0 ] && [ $(du -sm ~/.Trash/ |awk '{print $1}') -gt $size ]
do
        echo "Deleting files older than $limit days"
        find ~/.Trash -atime +$limit -exec rm -f {} \; -print
        limit=$((limit-1))
done

```

let me know what you think, obiously improvements and/or comments are welcome.

---

### Post by cilynx on 2006-12-15
I don't know how quickly you fill up your trash, but I have this in my cron.hourly
```

[ $(du -sm /home/rcw/.Trash/|awk '{print $1}') -gt 800 ] && rm `ls -tald /home/rcw/.Trash/* |tail -1|head -1 |awk '{print $8}'`

```
In human: 
Every hour, look at the trash folder and see if it is over 800M
If it is, delete the oldest file in the directory

I don't have anything making sure it actually gets under 800M again quickly, but really how quickly do you fill up the trash?  It usually takes me months to get up to 800M.  Preening if necessary every hour keeps mine in check just fine.  If you're going to grab this line, keep in mind the reprocussions of trashing an 800M file.  This line will eventually delete everything in the trash before getting to the one space hog.

For some quick fun bash scripting examples, see:
[http://marc2.theaimsgroup.com/?l=cgi-list&m=105896250311838&w=2](http://marc2.theaimsgroup.com/?l=cgi-list&m=105896250311838&w=2)

---


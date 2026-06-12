---
title: "delete file if it exists"
date: 2016-02-23
forum: General Help
---

### Post by marchello_lippi2 on 2016-02-23
Hi all, 

My need is to delete file if it exists. 
My crontab record is now 
**rm /var/lib/folder1/file1**
Obviously it shows error and comes into my root inbox
**rm: cannot remove '[FONT=Verdana]/var/lib/folder1/file1[/FONT]**[FONT=Verdana]**': No such file or directory**
[/FONT]How do I perform it only when it exists? 
Thanks ahead.

---

### Post by TheFu on 2016-02-23
```
#!/bin/sh

file=/var/lib/folder1/file1
if [ -f "$file" ] ; then
   rm -f "$file"
fi
```

Put that stuff into a file, make it executable, change the crontab to point at the script.
I suspect if you just used **rm -f** then no error would be shown - I didn't check it. The manpage for rm probably has more details.

---

### Post by marchello_lippi2 on 2016-02-24
[[COLOR=#000000]TheFu[/COLOR]]("http://ubuntuforums.org/member.php?u=1037685")[COLOR=#000000] 
Thanks, [/COLOR]**rm -f **[COLOR=#000000]works fine.[/COLOR]

---


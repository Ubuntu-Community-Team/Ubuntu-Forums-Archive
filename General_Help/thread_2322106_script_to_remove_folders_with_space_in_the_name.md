---
title: "script to remove folders with space in the name?"
date: 2016-04-26
forum: General Help
---

### Post by leras2 on 2016-04-26
hi everyone...
got a question.....i have a small script that deletes some specific folders with names in a form like 2016-04-26 or 20160426....
the question is that if there is a space in the name, or other character,it does not delete the folder.....
below is the full command that i use,just to let you know...used on ubuntu 16.04
and just some info,the main folder named 1 has some subfolders like /home/1/20160426 , /home/1/20160425 etc....and maybe there are /home/1/2016 04 26 or /home/1/2016 04 25  
```
**cd /home/errikos/1 && ls -t1 /home/errikos/1 | tail -n +2 | xargs rm -r**
```

any help will be appreciated....

---

### Post by btindie on 2016-04-26
Replace your xargs statement with ```
xargs -r -I{} rm -r '{}'
``` which will quote each argument to take care of the spaces. 

It's generally better not to use them to avoid the problem in the first place.

That command doesn't quite make sense to me. 'ls -1t' will list each file one per line and sort by mtime. The 'tail -n +2' command will remove the first line meaning that everything else in /home/errikos/1 will be deleted. Is that what you wanted?

---

### Post by sisco311 on 2016-04-26
Don't use ls for listing the files: [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

To deal with  spaces and special characters in filenames check out BashFAQ 020 (link in my signature).

To get the newest or oldest file check out BashFAQ 003

---


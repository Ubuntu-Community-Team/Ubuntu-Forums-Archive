---
title: "[SOLVED] rm files by filesize command?"
date: 2008-05-12
forum: General Help
---

### Post by elj4176 on 2008-05-12
I have an app that creates webpages of denied access attempts from internet logfiles. When there are no denied attempts for a day I get an empty logfile that still has html headers (~633kb). 
Is there a command to delete all of these files at one time?
Something like:
sudo rm | grep file -filesize < 650k

thanks!

---

### Post by joselin on 2008-05-12
Check du command.

Then you have to do something like:
```
du <options> | xargs rm
```

Sorry but can't tell you the du options now.

Regards

---

### Post by Monicker on 2008-05-12
Try this
```

find . -name "*.log" -size -650k | xargs echo
```

Change echo to rm once you are confident it is finding the files you want to remove.

I guessed at the extension.  I prefer to be as specific as possible when doing something like this.  :)

---

### Post by elj4176 on 2008-05-12
THanks! I'll give those a try.

---


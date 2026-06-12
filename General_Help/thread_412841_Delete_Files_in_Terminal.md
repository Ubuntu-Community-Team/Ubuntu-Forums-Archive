---
title: "Delete Files in Terminal"
date: 2007-04-18
forum: General Help
---

### Post by Sup3rkirby on 2007-04-18
How do you delete files using the terminal program?
And if i use 'sudo' + the delete command, will it delete files that can not normally be deleted(using Konqueror or any other file manager)?

My internet connection messed up during an update(apt-get install) and the file did not download completely.  When it tries to install it says the file is corrupted.  It will not download the file again....  i think since the file download was so close to actual completion that it won't redownload it because it thinks it is done.  Of course, I am probably completely wrong.  It is just my guess.

Either way, my problem is the same.  I can't redownload the update, and i can't install it because it wasn't completed, so the file is corrupted.  I can't just delete the file(using Konquerer) so i want to delete it using the terminal(as admin(using sudo)) and then I should be able to install the update(because it will have to redownload).

---

### Post by heimo on 2007-04-18
> **Sup3rkirby said:**
> How do you delete files using the terminal program?
And if i use 'sudo' + the delete command, will it delete files that can not normally be deleted(using Konqueror or any other file manager)?

Using rm. For example:
```
rm file
```
will remove "file". You can remove any file using "super user" permissions (sudo) and rm. So be careful.

---

### Post by aysiu on 2007-04-18
I would highly recommend *against* ever typing this phrase: ```
sudo rm
``` It's safer to use ```
kdesu konqueror
```

---

### Post by NT4usB on 2007-04-18
iirc, there's a way to 'force' an install.
man apt-get or apt-get -h
to read about it.
Probably better to fix the download rather than risk rming something you shouldn't...

---


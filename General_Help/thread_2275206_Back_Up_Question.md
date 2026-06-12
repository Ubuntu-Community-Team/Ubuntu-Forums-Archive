---
title: "Back Up Question"
date: 2015-04-24
forum: General Help
---

### Post by aviator1 on 2015-04-24
I'm using Deja Dup to back up my data.

The back up runs fine, but get the following error message when the back up is complete..

[B]Could not backup the following files.  
[/B]
**Please make sure you are able to open them.**
**/home/dave/.gnupg**

Can anyone explain this file, and should it be backed up?

If so, how do I set it to be part of the backup?

Thanks for any help.

Regards to all.

---

### Post by ian-weisser on 2015-04-24
.gnupg contains your gpg key (used for signing packages, digital signatures, encryption, etc. NOT used for ssh)
If you use your gpg key, then yes - you want it backed up.

The error message seems pretty clear - the backup software told you the problem (could not backup). That usually means ownership or permissions.
That particular folder should have the same owner and permissions as the rest of your /home dir - nothing special about it.

The error also recommended a simple way for you to test ownership and permission (try to open the dir in terminal or File Manager). 
Did you do so? What happened?

---

### Post by aviator1 on 2015-04-25
I cannot find the file .gnupg

---

### Post by ian-weisser on 2015-04-25
Does that mean your problem is solved?
Or does that mean your File Manager does not show a dir '.gnupg'?  (Tip: use CTRL+H to toggle the visibility of hidden files)
Or does that mean you tried 'ls -la /home/dave/.gnupg', and received a 'No such fle or directory' response?

---

### Post by aviator1 on 2015-04-26
Thanks for the hint and the terminal command. I did not know those.

I found the file, but when I click on it, the messages says I do not have permission to view it.

In terminal I get the following:

   dave@dave-desktop:~$ ls -la /home/dave/.gnupg  
 total 68  
 drwx------  2 dave dave  4096 Jul  1  2013 .  
 drwxr-xr-x 73 dave dave 40960 Apr 26 15:43 ..  
 -rw-------  1 dave dave  9398 Sep 10  2012 gpg.conf  
 -rw-------  1 dave dave     0 Sep 10  2012 pubring.gpg  
 -rw-------  1 dave dave   600 Apr 11 10:05 random_seed  
 -rw-------  1 dave dave     0 Sep 10  2012 secring.gpg  
 -rw-------  1 dave dave    40 Sep 10  2012 trustdb.gpg

This is a secondary drive that i am backing up, so I really do not need any security or passwords on it.

Thanks for any advice.

Regards

---

### Post by ian-weisser on 2015-04-26
The contents of your .gnupg directory looks appropriate.
Try this to see what the directory ownership and permissions are:
```
ls -la /home/dave | grep  .gnupg
```

---

### Post by aviator1 on 2015-04-26
dave@dave-desktop:~$ ls -la /home/dave | grep  .gnupg
drwx------  2 root root      4096 Dec 30 16:59 .gnupg

---

### Post by ian-weisser on 2015-04-26
> **aviator1 said:**
> drwx------  2 **root root**      4096 Dec 30 16:59 .gnupg

There you are. The directory is owned by root instead of dave, and nobody else has read access.
That last part's okay: It's your gpg key. Nobody else should have read access.

Let's fix the directory ownership:
```
sudo chown dave /home/dave/.gnupg
sudo chgrp dave /home/dave/.gnupg
```

Then see if your backup application stops complaining.

---

### Post by aviator1 on 2015-04-27
Will report this evening. Thanks.

---

### Post by aviator1 on 2015-04-27
Everything is working fine. Thanks for your help.

Regards.

---


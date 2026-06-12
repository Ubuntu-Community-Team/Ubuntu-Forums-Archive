---
title: "CHMOD then unable to access files"
date: 2014-03-04
forum: General Help
---

### Post by df23 on 2014-03-04
Hi 

i executed the following command in a terminal session while pointing at my Thunderbird "Local Folders"

sudo chmod -R 664 *

after this the folders and files in this folder and all sub-folders appear to be corrupt
Type = unknown
Date Modified = unknown
Group = unknown
Owner = unknown
Permissions = unknown

However if i run sudo nemo and navigate to the same folder i can see all the correct attributes of all the folders and files.

Anyone any ideas on what could have happened and how i can correct the files so that i can run Thunderbird again.

Im running Ubuntu 12.04

thanks
Dave

---

### Post by Lars Noodén on 2014-03-04
Directories need to be executable for you to see what's in them.  You could try this on the messed up directory:

```

sudo chmod -R u=rwX,g=rwX,o=rX

```

That should make the directories 775 and the files 664.

---

### Post by ajgreeny on 2014-03-04
> **df23 said:**
> Hi 

i executed the following command in a terminal session while pointing at my Thunderbird "Local Folders"

sudo chmod -R 664 *

Why did you use sudo in that command?  All those files belonged to you so just chmod as user would have done the trick.  Having used **sudo chmod** I wonder to whom those files now belong so lets have a look at the ouitput of ```
ls -l .thunderbird
```from your user terminal

---


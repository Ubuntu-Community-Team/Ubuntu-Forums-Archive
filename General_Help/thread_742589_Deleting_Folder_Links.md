---
title: "Deleting Folder Links"
date: 2008-04-01
forum: General Help
---

### Post by SlalomMan on 2008-04-01
Alright, so I was messing around with getting easier access to my media on my NTFS partition, making links to the files. I changed it so my default picture, document, etc. links go to those respective folders on my windows partition. However, I made an extra picture link on accident, whenever I try to delete it I am greeted with "This folder is on another filesystem." So I think that it's trying to delete the folder on the partition...I just want to get rid of the link. I can't seem to figure out how to do this, but maybe I am just overlooking it. Thanks in advance for the help!

---

### Post by y-lee on 2008-04-01
Try the code below in a terminal :

```
unlink symbolic_link
```

where symbolic_link is the link you wish to remove and note I am assuming you are in the directory that contains the link.

EDIT: When using  rm or unlink to delete a symbolic link to a directory, be sure you don&#8217;t end the target with a &#8216;/&#8217; character because it will not work right :)

---

### Post by SlalomMan on 2008-04-01
Thanks, it worked great! I never knew of that command before...haha.

---

### Post by y-lee on 2008-04-01
Glad it worked I had never used the command before just saw it in mentioned here and there :)

---

### Post by dcstar on 2008-04-01
> **SlalomMan said:**
> Alright, so I was messing around with getting easier access to my media on my NTFS partition, making links to the files. I changed it so my default picture, document, etc. links go to those respective folders on my windows partition. However, I made an extra picture link on accident, whenever I try to delete it I am greeted with "This folder is on another filesystem." So I think that it's trying to delete the folder on the partition...I just want to get rid of the link. I can't seem to figure out how to do this, but maybe I am just overlooking it. Thanks in advance for the help!

Because you have linked to a non-Linux native filesystem, then Linux does not have full control of the link so it is basically warning you of that - you should still be able to delete the link.

---

### Post by SlalomMan on 2008-04-08
Sorry to revive here...I was afraid of deleting the link just incase it deleted the actual folder as well.

---


---
title: "thunar thumbnail refresh"
date: 2008-02-23
forum: General Help
---

### Post by belovedmonster on 2008-02-23
Before I installed all the video codecs instead of getting a video thumbnail for videos files I was just getting a generic film icon. The problem is now I've gotten the codecs I've found that all the files I browsed before I had codecs still show the generic icon and its only folders that I looked at after getting codecs which show the thumbnail.

So how do I refresh the thumbnails? I tried the refresh option in thunar but that that seem to do anything with the thumbnails. Dont tell me I'm stuck with genetic icons for ever in certain folders :(

---

### Post by Pelham123 on 2008-02-23
How about if you 'rename' the file? Would that refresh the file type...and maybe the filetype association? Could also try deleting the items in the following folder /home/<name folder>/.thumbnails/normal/

.thumbnails is the hidden cache folder which stores thumbnail previews, can be safely deleted as they just get refreshed whenever you open a folder etc.

---

### Post by ryth on 2008-02-23
> **belovedmonster said:**
> Before I installed all the video codecs instead of getting a video thumbnail for videos files I was just getting a generic film icon. The problem is now I've gotten the codecs I've found that all the files I browsed before I had codecs still show the generic icon and its only folders that I looked at after getting codecs which show the thumbnail.

So how do I refresh the thumbnails? I tried the refresh option in thunar but that that seem to do anything with the thumbnails. Dont tell me I'm stuck with genetic icons for ever in certain folders :(

Hi Beloved. 

There is an easy fix for this.  All you need to do is delete you existing thumbnails and it will generate the new ones (hopefully with previews).

To do this try the following:
```


1. Places -> Home
2. Ctrl-H (this displays hidden directories and files)
3. Delete/Move directory ".thumbnails" to the trash

```
Alternately you can do this from command line. **Note:** rm -rf is a ***very*** dangerous command. it deletes a directory and all it's contents with no hope of getting them back. only use it when you are VERY sure of where you are applying it, and I would also suggest not using it with any wildcards!

```

cd ~
rm -rf ~/.thumbmails

```

Hope that helps!

---


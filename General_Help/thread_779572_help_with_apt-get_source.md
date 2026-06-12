---
title: "help with apt-get source"
date: 2008-05-02
forum: General Help
---

### Post by Tyke91 on 2008-05-02
I'd like to see what the firefox source code looks like, so i used the command 
```
sudo apt-get source --download-only firefox
```it worked... but now I'd like to open the file... I just don't know where it is.

where does apt usually put source code tarballs?

---

### Post by amingv on 2008-05-02
Check /home/yourusername (or your pwd).
Also notice, you don't need sudo for download only.

---

### Post by lemming465 on 2008-05-02
Jumping in the deep end are we?  Firefox is pretty complicated.  Don't let that stop you if you are really interested.  Note that what you'll have is a triple of files in the directory you ran apt-get in:

  * the .dsc file is the debian source control file
  * the .orig.tar.gz file is the upstream source
  * the .diff.gz file is the Ubuntu patches

If you need more information about what to do with these, I did a presentation on 
[building tools from source code]("https://mywebspace.wisc.edu/jeleinwe/web/BTS/") last fall which you might find helpful.

---

### Post by Tyke91 on 2008-05-02
heh, i don't want to compile it... I just want to see the source code... out of curiosity :)

PS: thank you... I can't believe that I didn't check there first.

---


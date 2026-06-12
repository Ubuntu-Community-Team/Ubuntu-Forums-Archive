---
title: "Strange CD drive problem (s)"
date: 2008-01-25
forum: General Help
---

### Post by Lord Xeb on 2008-01-25
when I went to eject my WoW disc, a message said I did not have permission to eject the disc because I am root... WTF? Now I cant open my drive with the button so I have to use a paperclip -_-

I figured it out. I put in the command for iso9660 and now it says my drive is full O_o how do I cancel it (I am a newb when it comes to unix/linux)

---

### Post by nemilar on 2008-01-26
I'm assuming you meant to say that you don't have permission to eject the disk because you are *not* root, in which case you should try:

```
sudo eject 
```

(this assumes you only have one CD-ROM drive.

---


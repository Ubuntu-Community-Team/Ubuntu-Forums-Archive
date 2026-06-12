---
title: "[SOLVED] System Volume Information Folder"
date: 2008-06-24
forum: General Help
---

### Post by solwic on 2008-06-24
I have a Seagate 160Gb USB External Hard drive.  I recently converted from Windows to Ubuntu (no dual booting for me - see my sig!  :P) and I noticed when I booted the drive up that I have a 5.0Gb folder titled "System Volume Information".  I've never seen it before in Windows, and I found a blog on MSDN that suggests it's a Windows-only thing, but I wanted to make sure before I deleted it and made my drive unusable or something.

Does anybody have any experience with this?  It's only 5Gb out of 160Gb, I know, but still...if I don't need it, I don't need it.  

Thanks!

---

### Post by ibuclaw on 2008-06-24
System Volume Information is a hidden system folder in Windows that keeps system restore information inside.

It isn't needed, Windows can survive without it (It will just create a new one on startup). But it's probably best if you don't go too far snooping around your unprotected Windows Filesystem in Linux.

If you want to have instant access to your Windows documents, perhap a symlink would better prefer you instead?

ie:
```
ln -s "/media/windows/Documents and Settings/Me/My Documents" "/home/Me/Desktop/My WinDocs"
```

Regards
Iain

---

### Post by solwic on 2008-06-24
> **tinivole said:**
> System Volume Information is a hidden system folder in Windows that keeps system restore information inside.

It isn't needed, Windows can survive without it (It will just create a new one on startup). But it's probably best if you don't go too far snooping around your unprotected Windows Filesystem in Linux.

If you want to have instant access to your Windows documents, perhap a symlink would better prefer you instead?

ie:
```
ln -s "/media/windows/Documents and Settings/Me/My Documents" "/home/Me/Desktop/My WinDocs"
```

Regards
Iain


Well, that's good to know.  Thing is, I don't have Windows anymore.  Won't ever go back to it, either, as long as Ubuntu is around.  I don't play games, and I can do everything else in Ubuntu.  So since I have no Windows system (pure Ubuntu for me, no dual booting), I have no need for this folder, right? 

Thanks!

---

### Post by ibuclaw on 2008-06-24
Oh, I see (didn't see that part /me blames his astigmatism)

Yes, of course, if thats what you want.

The folder has nothing to do with Linux, and is pretty much defunct if you don't have Windows. So you can wave goodbye to it.

Regards
Iain

---

### Post by solwic on 2008-06-25
> **tinivole said:**
> Oh, I see (didn't see that part /me blames his astigmatism)

Yes, of course, if thats what you want.

The folder has nothing to do with Linux, and is pretty much defunct if you don't have Windows. So you can wave goodbye to it.

Regards
Iain

That's what I was waiting to hear.  Just got rid of it.  I was just afraid it was something to do with the function of the drive; some files that any OS needed to recognize it.  

I'm a hardware noob, I guess.  :P

Thanks for the help!

---

### Post by MugOTea on 2009-12-31
It's always good to ask before taking the plunge. Like you I know microsoft but have no intention of reverting back. Ubuntu and hardware though, I'm just getting used to it.

I thought that maybe MS stored extended FAT/NTFS details in there for long file names etc. and didn't want to delete it without checking incase I lost all/some of my media HD.

Thanks for asking / posting / putting my mind at ease.

tinivole - good clear and straight forward answers.

---


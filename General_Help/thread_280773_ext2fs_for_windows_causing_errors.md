---
title: "ext2fs for windows causing errors"
date: 2006-10-20
forum: General Help
---

### Post by Polygon on 2006-10-20
i use the ext2fs driver in windows, and i use it so i can transfer data between windows and linux... but it seems that its now causing errors and the two partitons that i copy files onto using windows, is now being flagged as a "filesystem with errors" when i boot up with ubuntu and it has to do a checka and it does ite very reboot so i guess its not fixing the problem

question one: how do i fix this fs with errors thing?

question two: is it safe to still use ext2fs to transfer data between ubuntu/windows?

---

### Post by ciscosurfer on 2006-10-20
I used that program once...worst experience ever!  Windows slowed to an absolute crawl, my filesystems became corrupted, etc. -- it was not good for me.  If you need to absolutely grab files from Ubuntu when you're in Windows, I would simply suggest not to.  Work in Ubuntu and grab your Windows files through Ubuntu rather than trying it the other way around.  I don't know...I tried ext2fs maybe a year ago, and from the sound of it, you're having trouble with it now (so the code is still obviously buggy -- or Ubuntu keeps moving forward, one of the two.)  From what I can recall, what was happening was that Windows was basically loading everything in my EXT3 partitions (EXT3 is simply EXT2 with journaling) and that was slowing things down quite a bit.  I also remember the site saying that it was okay to use on EXT3 b/c really it was only the journaling aspect that was added and so that wouldn't affect the way ext2fs was implemented.  Perhaps this was bad advice on their part; I really couldn't say.  So, for what it's worth, I also had errors and crawls similar to yours; you're not alone.  I would say bag it at this point and try again later.  Or keep searching.  Let me know if you come up with any other programs that are worth taking a look at!

---

### Post by theslut on 2006-10-20
i've used that driver for a while and I have absolutely no problems with it. So no, I don't believe it's that buggy.

I think by the nature of it, it causes the disk checker in ubuntu to run a scan. Have tried setting the disk checking option in fstab to a 0?

---

### Post by ciscosurfer on 2006-10-20
Just because you haven't had problems with it, doesn't mean that others haven't.  It was my best guess that it could be a bug or a problem with the code.  That, my friend, is a bug.

What evidence do you have of Ubuntu's ext2 file system checker being activated on Windows boot?

---

### Post by Polygon on 2006-10-21
well when i boot up now it no longer checks the two filesystems for errors, which means i think that it finally fixed it. I think on my next reformat though ill go back to fat32 =P

---

### Post by bsussman on 2006-10-21
> **Polygon said:**
> I think on my next reformat though ill go back to fat32 =P

That is probably a wise idea.

Windows has a (IMO deserved) reputation for not playing well with others.  It is generally less painful to let the linux side do the extra work, building your pivot filesystem for maximum compatability on the MS side.

---

### Post by srirammurali on 2006-10-21
no problems with the ext2fs driver whatsoever on my box either. seems to work well, the performance on XP has not been compromised with either..

---


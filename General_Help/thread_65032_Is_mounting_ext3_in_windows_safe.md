---
title: "Is mounting ext3 in windows safe?"
date: 2005-09-12
forum: General Help
---

### Post by Steve Smith on 2005-09-12
I've been looking at this program - [www.fs-driver.org](http://www.fs-driver.org) - to mount an ext3 partition in windows.  Is it completely safe, or do you think there would be a risk of data loss?

---

### Post by bsussman on 2005-09-12
Um - it depends on the reliability of this driver.

BUT ACCORDING TO THE FAQ WHICH I HOPE YOU READ, ext3 is processed as ext2 - in other words, you get no journalling reliability.  I should think this is a big negative.

My heart says using MS partitions to share tween MS and Linux is a better strategy.  I trust the Linux community.  In this case, these folks document that they are not supporting ext3 functionality.

---

### Post by Steve Smith on 2005-09-12
Mmm :-/.  I read about not having journalling, but at least with ext3 I'd get journalling in Linux.  WIth fat32 I'd get it with neither, wouldn't I?  What do you think?

---

### Post by bsussman on 2005-09-12
That is a good point - I supppost it just comes down to the wuality of the driver...having no experience with this particular driver, I cannot comment.

But, as I mentioned, there is nothing against basic principles in using alternate drivers.

Just do good backups ;-)

---

### Post by Steve Smith on 2005-09-12
Backups are the things I make when it's too late :P  Well thanks for your thoughts, given me something to think about!

Has anyone here used that driver before?

---

### Post by YourSurrogateGod on 2005-09-12
[QUOTE=happysteve]Backups are the things I make when it's too late :P  Well thanks for your thoughts, given me something to think about!

Has anyone here used that driver before?[/QUOTE]
I've never had experience with it, but I'd suggest to simply back-up your most important files in Ubuntu and try it. If in the worst case your *nix OS isn't bootable, then you can simply re-install it with few if any loss.

---

### Post by Steve Smith on 2005-09-13
[QUOTE=YourSurrogateGod]I've never had experience with it, but I'd suggest to simply back-up your most important files in Ubuntu and try it. If in the worst case your *nix OS isn't bootable, then you can simply re-install it with few if any loss.[/QUOTE]
 The disk was good as blank anyway, I did a full system backup for the first time ever, before installing Ubuntu, and formatted to de-winxp-junk it.  It seems to be working okay, so far so good...

---

### Post by YourSurrogateGod on 2005-09-13
Actually, come to think of it, what bsussman said makes alot of sense. Whether the FS supports journaling or not isn't the bigger topice here.

For example, if the small, in-between FAT32 FS fails or becomes corrupted, then you simply lose your little in-between FS, which can be repaired. If your Ubuntu partition becomes corrupted by the use of that program, then you can't boot to Ubuntu. In the worst possible case scenario, it would be preferable to lose a small FAT partition.

---

### Post by Irony on 2005-09-13
If you want to view linux partitions in Windows go here;

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download)

And download *explore2fs-1.07.zip* - simply unzip it and drag the contents into a folder; then click the executable to run it.

You can then access linux partitions and open files or drag them to windows.

---

### Post by Steve Smith on 2005-09-13
[QUOTE=YourSurrogateGod]For example, if the small, in-between FAT32 FS fails or becomes corrupted, then you simply lose your little in-between FS, which can be repaired.[/QUOTE]
Putting it like that makes a lot of sense!  I can only really afford 1Gb, I'm on a laptop with a 20gig disk, but I guess that'd be enough for what I need to share.

[QUOTE=Irony][http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download)[/QUOTE]
Thanks for that link!  It achieves the same thing as the one I've tried already, but have you had any experience of using this one - have you found it reliable?

---

### Post by YourSurrogateGod on 2005-09-13
[QUOTE=happysteve]Putting it like that makes a lot of sense!  I can only really afford 1Gb, I'm on a laptop with a 20gig disk, but I guess that'd be enough for what I need to share.[/QUOTE]
Well, it depends on the size of files that you need to share. For me, personally, 500MBs would be enough.

Some other options are...
1) Buying an external hard-drive. Yes, they are kind of expensive, but you can send files back and forth between windows and Linux without a problem. You could also back some files up.
2) Getting a memory. Same as a hard-drive, except cheaper and less space to work with.

---


---
title: "Gparted Error: Input/Output error during read on /dev/sda"
date: 2013-12-27
forum: General Help
---

### Post by Ashfaqur Rahman on 2013-12-27
I was trying to shrink /dev/sda1 ( Label: Windows ) partition 10GB and add it to /dev/sda2 (Label: Files) (See Attachment). After moving 286GB suddenly I got that error message( See Attachment ).

FYI I mounted /dev/sda1 partition after starting moving process. May be this is the cause of the error.

I have noticed another thing, If I clicked on Retry/Cancel/Ignore button on the error message, progress bar of the moving process grows 0.01GB. That means to finish this process I have to click more thousands of clicks!! I also worried about my files.

So, Is there any way to safely complete this process or safely terminate this process, so that I can keep my files / data safe?

---

### Post by fantab on 2013-12-27
Do yourself a favor and only use Windows utilities to manage Windows partitions. Linux utilities can cause issues like above. Use Windows Disk Management or any other such tool for Windows to 'resize or move' NTFS partitions.

---

### Post by The Cog on 2013-12-27
> FYI I mounted /dev/sda1 partition after starting moving process. May be this is the cause of the error.
No, you really should not have done that.

If you are really lucky, unmounting the partition again might allow the move to continue, but I have my doubts.

---

### Post by Ashfaqur Rahman on 2013-12-27
Thanks for you advice. @fantab

Actually I did't do it, I was careful, I know that at this stage mounting partitions can cause damage. As I saw that this process would take almost 2 hours, I left my laptop for a while and when I came back I saw my brother mounted /dev/sda1 partition!! As soon as I noticed that I unmounted /dev/sda1 but you can see that error occurred@The Cog

But I am really really lucky this time!! I tried clicking ignore again and again and the progress bar upgraded almost 20GBs. But suddenly Live Ubuntu hanged!! Even hidden terminals(Ctrl + Alt + F1-F6) couldn't work. So I had no option without force shutdown. I did that. When I restarted I noticed that my all files are safe and sound!
But Gparted is showing error sign in /dev/sda2( see attachment ). Under /dev/sda2 when I go to information option It suggest me " 10GB of unallocated space within the partition to grow the filesystem to fill the partition, select the partition and choose the menu item partition --> check "( see attachment )

Now my question is, is it safe to do Check? As It is not possible for me now to backup almost 350GB of space and test myself.

---

### Post by The Cog on 2013-12-28
Oh, that's a relief!

The check option says "check and repair". I guess it should be safe though I've never used it in anger (tried it just now on a spare partition and it instantly said it had finished). 
As always, have a backup first, just in case.

---

### Post by Ashfaqur Rahman on 2013-12-28
Update:
I ran "Check" and It repaired my partition safely!

---


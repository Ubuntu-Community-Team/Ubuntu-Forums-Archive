---
title: "[SOLVED] NTFS deleteing large chunks of data issue"
date: 2008-03-14
forum: General Help
---

### Post by gobuntu on 2008-03-14
Dear friends,

On Windows XP, when deleting LARGE chunks of data (a folder under which there are MANY subfolders and files) which can not fit in the trashcan, I have found that the operation can take a LONG time.

Now, on pretty much the same situation, but from Ubuntu Gutsy, de operation takes NO TIME. 

So I says GREAT!

However, when this is done in Ubuntu as said, the Free Space IS NOT updated!

That means that if the data was all under one folder (and subfolders) and I dropped it, the drive still shows 70% used, SAME as before dropping the data!

Now, there appears to be no real corruption, for then, in XP, the exact same statistics show, and there's no data.

In fact, either can work well in the free 30% of space.

However, the real estate is being wasted (by Ubuntu) it seems.

I've been researching and replicating this problem consistently for quite a while now. 

In research, I found somewhere that NTFS read/write in Linux is still not yet perfect, and it seems to refer to this phenomena, but the article was way to brief.

I am pretty sure of not having any bad hardware, bad installation, or any other factor.

So far, it seems to me that this is the way NTFS read/write works in Ubuntu, which is OK for small file deletes, but not for LARGE chunks of data.

My reason for this little theory is that, otherwise, we would have to defragment the NTFS, and I hear no mention of defragmenting NTFS in linux.

Any one have the beans on this, please help, so I'm square and confident.

Thanks!

---

### Post by kpkeerthi on 2008-03-14
Strange. I never experienced this. The deleted files are probably in trash. If you have an NTFS partition /dev/sda1 mounted to /media/Windows1, look for **.Trash** folder* in /media/Windows1. 

* Its a hidden folder.

---

### Post by gobuntu on 2008-03-14
> **kpkeerthi said:**
> Strange. I never experienced this. The deleted files are probably in trash. If you have an NTFS partition /dev/sda1 mounted to /media/Windows1, look for **.Trash** folder* in /media/Windows1. 

* Its a hidden folder.

No, they are LARGE chunks of data that DON'T FIT in the trash.

I've checked to see there, I've checked via other means too, like number of iles, etc., and SHOW hidden folders.

---

### Post by gobuntu on 2008-03-14
Dear friends,

NEW, interesting findings:

I have now TWO laptops side by side (to discard equipment/installation error), and I can unmount/mount this NTFS formatted USB drive from one laptop to another, as well as drop a HUGE folder by deleting it, and YES, what happens, the deletion is instantaneous, because an invisible folder called .Trash is created, which simply holds the contents.

Now, this invisible folder is created in the same USB drive, not elsewhere, at least that's the way I have it setup.

So I open this .Trash folder and, yes, all the contents are still there, and therefor, correctly the used/unused space of the drive is not really altering.

So, I think, fine, in order to PERMANENTLY delete the data, all I have to do is delete the .Trash folder.

BUT, guess what?

That DOES NOT HAPPEN. What happens is that the .Trash folder is put INSIDE of ANOTHER .Trash folder!!

So, so far, i don't see a way of DELETING NTFS data, and I would very much like to hear from someone who knows different.

In other words, when we deal with NTFS data, we do not really RECOVER unused space, at least in my setup, which should not be peculiar at all, because this USB is auto-mount, conventional installation.

I have a lot more to explore on this issue, since I am planning on relaying on this (and other) USB drives to backup my data from Ubuntu, rather than from the Windows environment.

Thanks for any help, suggestions.

---

### Post by gobuntu on 2008-03-14
Dear friends,

This is kind of my conclusion on this issue:

All is normal under PROPER interpretation, as follows:

1. On the graphical environment "Move to trash" option is really 'move to trash folder', a hidden file, that is created when needed.

2. This folder and contents "don' count' for most purposes.

3. Can never permanently delete the .Trash folder by "Move to Trash" because it just moves into a new .Trash folder.

4. Since "Empty the Trash Can" does not apply to this drive, being external, and having chosen no particular mount, but, rather auto-mount. It's Trash is the .Trash file in the external drive's root directory.

5. I can live with this modus operandi until I want to specifically PERMANENTLY DELETE the .Trash folder with the terminal "su rm -rf FileName".

I have already done this and TOTAL delete of the NTFS data is MUCH faster than in Windows XP.

I only encountered one error message of a filename which the 'operation could not support', and it was easy to fix by RENAMING that filename. That's not a problem of ntfs-3g since some Windows filenames are illegal, and, actually, SOME Windows applications install themselves under 'illegal' names so that they are hard to remove (and they are hard to remove in Windows). ntfs-3g actually does a great job of handling most incompatible filenames.

I'm getting 'there'.

Thanks everyone.

I am calling this issue 'SOLVED' but would like to hear of other solutions, ideas.

---

### Post by Oldsoldier2003 on 2008-03-14
> **gobuntu said:**
> Dear friends,

This is kind of my conclusion on this issue:

All is normal under PROPER interpretation, as follows:

1. On the graphical environment "Move to trash" option is really 'move to trash folder', a hidden file, that is created when needed.

2. This folder and contents "don' count' for most purposes.

3. Can never permanently delete the .Trash folder by "Move to Trash" because it just moves into a new .Trash folder.

4. Since "Empty the Trash Can" does not apply to this drive, being external, and having chosen no particular mount, but, rather auto-mount. It's Trash is the .Trash file in the external drive's root directory.

5. I can live with this modus operandi until I want to specifically PERMANENTLY DELETE the .Trash folder with the terminal "su rm -rf FileName".

I have already done this and TOTAL delete of the NTFS data is MUCH faster than in Windows XP.

I only encountered one error message of a filename which the 'operation could not support', and it was easy to fix by RENAMING that filename. That's not a problem of ntfs-3g since some Windows filenames are illegal, and, actually, SOME Windows applications install themselves under 'illegal' names so that they are hard to remove (and they are hard to remove in Windows). ntfs-3g actually does a great job of handling most incompatible filenames.

I'm getting 'there'.

Thanks everyone.

I am calling this issue 'SOLVED' but would like to hear of other solutions, ideas.

trash is such a pain in the neck that i just habitually dlete from the command line...

---


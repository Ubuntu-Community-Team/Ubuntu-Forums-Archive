---
title: "Confirmation on whether this rsync script is right."
date: 2007-01-31
forum: General Help
---

### Post by Roasted on 2007-01-31
Last time I ran Ubuntu somebody helped me set this up. This time I am on my own.

I have 2 hard drives in my computer. The first drive has windows/ubuntu, and the 2nd one is formatted with ext3 that I use for backing up my home folder on the first drive.

Here is what the script reads.

sudo mount /dev/sdb2 /media/sdb2
rsync -a --progress --delete ~/ /media/sdb2
sudo umount /media/sdb2

I also did a "sudo chmod 775 /usr/local/bin/backup" as well, which is where this script is I pasted above.

I'm curious about something. I opened up two windows. My home folder, and the sdb2 backup folder. I put them side by side. I manually mounted the second drive. Then I created an empty folder in my home folder, and suddenly it appeared on the backup drive. This confused me, because before, I had to manually run the script for it to appear. This time it was just magically copying it, as if it were a true RAID setup.

Why is this? Why is it automatically doing it when it's mounted? Again, when the drive remains mounted, it automatically syncs over everything from my home folder. Last time it didn't do this to my knowledge. Then again, I also had it auto unmount when the script was done.

Can anybody shed some light?

---

### Post by gerbman on 2007-01-31
Is that script in your crontab? Perhaps crontab started it right after you created the folder in your home directory. I can't think of anything else that would have copied the folder.

---

### Post by Roasted on 2007-02-01
I never messed with crontab in this install...

How do I access that and alter whatever I need to?

---

### Post by gerbman on 2007-02-01
> **Roasted said:**
> I never messed with crontab in this install...

How do I access that and alter whatever I need to?If you never used it, then it wouldn't be the cause...it's something you have to set up manually.```
crontab -e
```

---

### Post by Roasted on 2007-02-01
Oh wow. I just realized something. In the window where I'm looking at the spare drive, which is sdb2, once it unmounts, I didn't realize that that window switches over to my home folder automatically. And since the window on the left (the sda home folder) I'm putting a new folder in, of course it'd pop up in the right window! Cause the right window, as I said, switches over to my home folder when the drive is unmounted! duh... NOTHING auto-copies to the 2nd drive. It's just I have 2 home folders open on the same drive and didn't realize it. Blah.

Anyway, this is all I did to set up my rsync script.

I created the script in text editor, gave it chmod 775 rights, and put it in usr/local/bin.

That's it. That's all I did. Is that all I need to do to have a secure reliable (and also manual) way to back up my stuff? (in this case my home folder).

And like I said, I had help last time when I set this script up. Last time what I did was the script was set up in a particular manner, where if there were already files on the 2nd drive that matched what was on the 1st drive, it'd just skip over them. For example, if Metallica is on my first drive and I run the script, it'll copy it to the second drive. If I run the script again, it won't bother recopying it because it's already there. Is that what the --delete tag does in my script? I know --progress shows me what it's doing in terminal, but what is -a? 

Besides my questions, is my script set up pretty decently then? Any suggestions?

---


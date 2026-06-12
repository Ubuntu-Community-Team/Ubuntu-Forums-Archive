---
title: "Installing Windows partition"
date: 2007-08-11
forum: General Help
---

### Post by iota on 2007-08-11
Ok, this is going to sound like a very silly question, but how on Earth do I install Windows in a partition on my linux (ext3) harddrive?

I've done a lot of looking around, and I can't seem to even find the beginnings of an answer.

So far I've tried to resize the current ext3 partition so it is 20gb smaller, and then created a new 20gb raw partition after it. This, I thought, would work.

However upon trying to install windows I am informed that it needs to write to my ext3 partition (Also saying something about mbr, master boot record?). I don't understand why it needs to do this, or how to get around it :( And unfortunately cannot find any information from google/the forums so far.

If anyone can help or has done this themselves the help would be greatly appreciated. Cheers in advance :)

---

### Post by jeremy1138 on 2007-08-11
Why didn't you make the file system on the new partition NTFS?  That's the one that Windows uses...  I've had a dual boot system for a while and I used Norton Partition Magic to set it up.  I had Windows first and then I resized the partition to make room for Ubuntu.  Does the Windows install program let you choose to set things up yourself or does it just automatically want to mess with the Linux partition?  Maybe changing the file system to NTFS will cause Windows to notice it's there?

---

### Post by iota on 2007-08-11
Well, it notices it's there, and usually the windows install would format the partition itself. It just, for some reason, wants to format the other partition on the drive :S

Also gparted seems to have greyed out the ntfs option :( And I have absolutely no idea why that is.

Cheers for the quick reply by the way :)

---

### Post by jeremy1138 on 2007-08-11
This may not work but it's something you could consider...  When I was using Norton Partition Magic to set my computer up it gave me the option to hide partitions and to specify which partition would be the boot partition...  What if you either hid the Linux partition so Windows couldn't see it or you made the new partition the bootable one.  You may not want to try this because I'm not 100% sure of how this all would work but it may be something that you want to consider...  Maybe someone else will see this and give us some more insight?

---

### Post by iota on 2007-08-11
Heh yeah Norton Partition magic requires that i install Windows though :( Which is somewhat of a paradox :P

I think I may have to just wipe the drive clean, try and put what data I can onto my other drives (Although I am very low on space) then install windows, then put the ext3 partition back with gparted/norton.

*hopefully* that might work, I'll let you know right after I've tried it :) Cheers for all the help by the way!

---


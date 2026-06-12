---
title: "Can you undo (or cancel) partitioning?"
date: 2007-12-09
forum: General Help
---

### Post by s.schofield on 2007-12-09
I'm an idiot, please please help me!
I tried to expand a partition to the left using the g-parted live cd-I'm still doing it now- but it's taking far too long. It's currently doing a read only test to move the file system to the left, which is half way through what appears to be a 24 hour process. I'm worried about how long the full thing will take and would like to cancel this now if possible.
Currently the only thing that has been done  to the disc is to move the partition (not the file system) to the left, which took about a second. I would like to cancel moving the file system to the left and then move the partition back to the right to get back to where I was. Is this at all possible?

Other options:
If it takes 24 hours to do the read only test, how long will it take to do the full thing?
What does g-parted do if you press the cancel button?

Any other suggestions?

I'm desperate for help and I don't have long till it finishes doing this test. I really hope someone can help?

---

### Post by ajgreeny on 2007-12-09
I suspect it is rather dangerous to cancel the partition move at this stage and would advise you to let it continue to the end.  I have moved a partition backwards on the disk as you are doing and it did take a long time, though how long will depend upon how much free space there was on the partition to start with and how much ram you have.  As I understand it all the data will be copied and then rewritten to the new sized partition.

As to your actual question, I have absolutely no idea what happens if you cancel the process while it is going through its activities of moving etc, but I do think it best left alone.

---

### Post by forestpixie on 2007-12-09
My son decided he wanted only win on his pc - I deleted the ubuntu partition (with heavy heart) and resized the win partition, left it cooking - when I came back - he'd got fed up waiting and cancelled the operation 

End result was he had to wait even longer because the partition was completely shot and I ended up doing a reinstall of windows for him.

---

### Post by ajgreeny on 2007-12-09
Thanks for that info; worth knowing as it's not something you do everyday (thank goodness for that!)

---

### Post by forestpixie on 2007-12-09
It did make me :D

Children and haste are a bad combination

---


---
title: "I need help with ntfsundelete"
date: 2017-03-31
forum: General Help
---

### Post by Evil Wayz on 2017-03-31
By accident, I deleted 800 movies from my portable hard drive.  I immediately unmounted it so nothing would overwrite the.  Of the options available to me, ntfsundelete was the one i understood the most. Or so I thought.

I have never been very good at writing the options so I need help.

What I want to do is undelete every *.mkv *.avi *.wmv and *.mp4 that was deleted within the last 4 days.  I imagine i will have to use four different commands.

Also the drive has to be forced, no matter how many times i properly unmount it in windows it gives me that message.  

So heres what I have come up with, and it kicks me to the help messages.

Where the drive with the deleted files are located is sdc1.  The drive and folder I want to place the recovered files is /media/wolf/Seagate/wolf

sudo ntfsundelete -r /dev/sdc1 -u -t 4d -m *.avi /media/wolf/Seagate/wolf

is what I thought should work, but It isn't. 

any help would be appreciated, as its 387 gb of media I probably can't get back.

EDIT:  I think the major problem here is I deleted a folder with everything in it.  And each movie was in its own folder.  So what I think I need is some way for it to scan and keep the directory structure intact, if that's even possible.

---


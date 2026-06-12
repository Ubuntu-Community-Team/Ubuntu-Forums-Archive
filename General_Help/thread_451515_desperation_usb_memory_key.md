---
title: "desperation usb memory key"
date: 2007-05-22
forum: General Help
---

### Post by renevee on 2007-05-22
Howdy all!
I recently upgraded my system to Ubuntu 704.  I loved it so much I wiped windoze and stuck with ubuntu, and everything's played nicely.  Until today.  I have about 30 pages of my manuscript and other critically important info on a fairly new dell usb mem stick, 512MB.

It's worked fine in ubuntu until today when after I wiped windoze last night, got up this morning, stuck in the mem key to work on manuscript, and now it's unmountable for some reason.  And in a windoze box it wants of course to format it.

Any help would be magnificent.

I'm very happy and impressed with ubuntu.  In fact I also installed Kubuntu on separate partition.  Incidentally, and unrelated: in Kubuntu none of my other drivers are mounted, visible, or auto mounted.  In Ubuntu, it's all auto, nicely put for my access any time.  Would someone be so kind as to let me in on how to accomplish that?

I'm on a borrowed laptop/connection here, and I haven't had time to exhaustively search the forums and threads yet.  Thanks much in advance!

Rene
renevee AT g mail dot com

---

### Post by renevee on 2007-05-22
sorry, to be clear, the usb key *is* auto mounted, present, but not accessible when I contact it with attempts to access anything on it.  That's when I get the message "not accessible," and if I try to click/mount, I get the message, "not mountable."

Regards

---

### Post by LaRoza on 2007-05-22
> And in a windoze box it wants of course to format it.

If Windows said that, I have very bad news...

Did you happen to pull this USB drive out without "safely removing" it? If you did, you lost everything and will need to reformat it. If you can reformat it, that is good news because you can still use the drive, which is better than destroying the circuitry, which is possible.

Just to be sure, find out the format this drive has, right click it, select properties. If it gives a different format than what it had, like RAW, you have lost the data and need to reformat.

There are utilities that claim to be able to recover such data, but don't get your hopes up. Sorry.

---

### Post by RealTrueSoft on 2007-05-22
You might not be out of luck, but it's not going to be easy to fix this problem unless you're ready to get your hands dirty. I've had the exact same problem with a USB drive before and found this article which was a lifesaver 
[http://www.linuxjournal.com/article/8366](http://www.linuxjournal.com/article/8366) .
  In my case Windows zapped my drive and I had the same symptoms as you described in Ubuntu as well. It took some doing, but following the "repair attempt 2" part of the article I posted got me most of my data back.
The key to safe recovery is making a copy of the disk with the dd command. After you make a copy that way, you should be able to hack away at the copy. Do NOT attempt to hack away at the disk itself. By the way, a little while after I created the copy and tried to mount my USB drive, the drive quit altogether so it might be a good idea to get that data(even if it is temporarily corrupted) copied to a safer location like your hard drive. I ended up having to get a utility to reformat and restore my drive from the manufacturer, but it worked perfectly again after that, minus the data. Thankfully I was able to restore my data using dd before I lost it though. Good luck!

---

### Post by renevee on 2007-05-24
Great!  I appreciate the help, for sure.  I can't even get windows to format the drive for me know, on the assumption the drive would be bad anyhow.  I'm making no further attempts to get at any data until I read this article.

I ddi figure out how to auto mount the drives in KDE.  Thanks again for the great help.

Rene

---


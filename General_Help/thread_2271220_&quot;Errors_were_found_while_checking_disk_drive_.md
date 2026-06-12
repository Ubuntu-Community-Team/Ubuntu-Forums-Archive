---
title: "&quot;Errors were found while checking disk drive /.&quot;"
date: 2015-03-28
forum: General Help
---

### Post by Urbanmasque on 2015-03-28
When I boot up my machine it takes me to the image below. Selecting I works to get me logged in and my computer seems to function normally, but I'm worried that soon when I start it up I wont be able to get to the login screen.

[IMG]http://i.imgur.com/U5fgUYpm.jpg[/IMG]

Do any of you have any experience with this error?
Any idea how I can resolve it?

---

### Post by Vladlenin5000 on 2015-03-28
How old is that drive? Perhaps it's time to start thinking about replacing it...

---

### Post by deadflowr on 2015-03-28
I would boot into a live cd session (from a Ubuntu installation disk/usb, "Try Ubuntu without installing" option)
Then I would open the program called Disks, or Disk Utility if on 12.04.
Then highlight the hard drive listed --it will show the full storage capacity of the drive, so if the drive is a 500GB drive the option to click would be the one stating 500GB; it'll also say the actual drive name, but that is unimportant.
Then in the main window that now shows the drives partition, in the upper right side, just above the partition table graphic, is clickable box marked "Smart Data"
Click on it and look at the info it says, is the drive marked as Healthy or does it say something like drive has a few bad sectors.

now a few bad sectors in and of themselves are not a cause for concern, sometimes a few sectors can be corrupted but that doesn't mean the overall drive is failing.
However, I would think that if the drive has at least 100 bad sectors, it would be worth considering that it is indeed either failing or on the verge of failing. 

(A good practice on drives is to check the status, with this program(or you can install a more verbose program called [smartmontools]("https://help.ubuntu.com/community/Smartmontools")), periodically. On a personal note I once had a drive that had 87 bad sectors. It remained 87 bad sectors for 2 years, so obviously it wasn't totaly failing for those 2 years. When those bad sectors started to increase, I knew the drive was now in a state of failure.)

Now, if the drive show Healthy, then perhaps run an fsck filesystem check.
Some good pointers on that here
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

I strongly recommend doing these from a live session, so that you do not add any possible corruption to the disk.
Live sessions do not mount the hard drive, and since fsck works best on mounted drives/partitions it is easier to deal with, IMO.

Hope this helps.

---

### Post by Urbanmasque on 2015-03-28
> **Vladlenin5000 said:**
> How old is that drive? Perhaps it's time to start thinking about replacing it...

I didn't take that photo - I'm just using it as an example of the messaging I'm getting.  I'm in 14.04 and my SSD is relatively new.

---

### Post by Vladlenin5000 on 2015-03-28
I was concerned about the error message, not the photo itself.
Old or new, I would follow the advice on post #3 to the letter just to be sure. Even a relatively new SSD can fail but hopefully just logical, software correctable, errors. Those might happen after an abnormal shutdown.

---

### Post by Urbanmasque on 2015-03-30
Thanks for the help Vladlenin5000 & deadflowr - I'm going to mark this as solved as I went through the scanning / fixing process and it seems  resolved.  I will shut down and restart my computer properly from here on out (if I can access the menu through a frozen program).

Thanks again!

---


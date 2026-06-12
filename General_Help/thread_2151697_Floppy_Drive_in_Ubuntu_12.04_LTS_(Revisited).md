---
title: "Floppy Drive in Ubuntu 12.04 LTS (Revisited)"
date: 2013-06-05
forum: General Help
---

### Post by foberle on 2013-06-05
When I first decided to dump Windows and try Ubuntu, I loaded 11.10 and then, subsequently, loaded the 64 bit 12.04 LTS, which I am still using. Although Ubuntu seemed to know my 3.5" floppy drive was installed, the entry "Floppy Drive" under "Devices" in Nautilus did nothing.

I posted many queries about this, and learned how to manually mount it when I needed (edits to fstab didn't help at all), but this is annoying.

I subsequently learned that support for floppy drives was inadvertantly trashed in some manner several years back - details in various postings vary as to the timing and reasons for this, but there seemed to be no doubt that it was a problem.

I want to stay with the LTS release for the usual reasons but, attempting to keep current, recently ran the 12.10 Live-CD (actually a DVD from a magazine). To my surprise the "Floppy Drive" entry in Nautilus acted exactly as I would have expected. To insure my sanity, I then ran a Live-CD of 12.04LTS - thinking that maybe somehow I had screwed up my own installation. As expected, the "Floppy Drive" entry did nothing.

So my question is: if I wish to keep using 12.04, is there some file, package, program or whatever that I can safely replace in order to activate the "Floppy Drive" functionality? Or are there too many messy dependencies involved? Has anyone successfully accomplished this?

I'm open to the possibility of upgrading, but I haven't had a chance to look at 13.03 yet, and am not willing to install 12.10 ("Quantal Quetzal," aka "Amazon Appropriations") as I didn't see any benefit to doing so.

Does anyone have any advice or thoughts?

---

### Post by searchfgold6789 on 2013-06-05
Here's what you should do to get your floppy drive working - open up the trusty terminal, and run: ```
gksu gedit /etc/modules
```At the end of the file, add the line: ```
floppy
```And save it. Upon reboot, the floppy kernel module will be loaded. You can also do ```
sudo modprobe floppy
```to load it temporarily if it is not already loaded.

---

### Post by Dennis N on 2013-06-05
If all else fails, you could get yourself an 3.5" external USB floppy drive. I have one made by TEAC that works fine with Ubuntu.

---

### Post by foberle on 2013-06-06
Uhhh, no, but thanks for the response. I know how to do those things. The problem is that "floppy" hasn't worked for several versions, whether due to a problem in the module or in something that uses it.
What I was wondering is if I could safely steal pieces from 12.10 and use them in 12.04 and, if so, which pieces?

---

### Post by oldfred on 2013-06-07
Also:

 [http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
[http://ubuntuforums.org/showthread.php?p=11244050#post11244050](http://ubuntuforums.org/showthread.php?p=11244050#post11244050) post #2 coffeecat
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

---


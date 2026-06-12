---
title: "sshfs+ rm = help!"
date: 2007-10-26
forum: General Help
---

### Post by zksailor534 on 2007-10-26
I recently remotely mounted a folder from another computer on mine using sshfs.  To cut the story short I mistakenly deleted half the files in a folder on that computer using rm -R.  I realized what I had done quickly and stopped the process to save half the files, but is there any way to recover the other files?  The remote folder is on a Mac using OSX 10.4 and nothing has been changed since the rm command.

---

### Post by mayonaise15 on 2007-10-26
The only way I would think recovery would be possible is with a file recovery program.  Helix is a forensic boot cd that can recover deleted files, but I don't know if i works on Macs.  I'm not sure if it can read the file system or not.  If you want to play around with it go to [http://www.e-fense.com/helix/]("http://www.e-fense.com/helix/").  Anybody else know?

---

### Post by xeth_delta on 2007-11-15
> **zksailor534 said:**
> I recently remotely mounted a folder from another computer on mine using sshfs.  To cut the story short I mistakenly deleted half the files in a folder on that computer using rm -R.  I realized what I had done quickly and stopped the process to save half the files, but is there any way to recover the other files?  The remote folder is on a Mac using OSX 10.4 and nothing has been changed since the rm command.

I agree with what mayonaise15 said, you could try a data recovery program. Since the files in question resided on a Mac, I would suggest searching for such programs on [http://www.versiontracker.com/macosx/]("http://www.versiontracker.com/macosx/") or [http://www.apple.com/downloads/]("http://www.apple.com/downloads/"). Another idea would be an eventual back-up you might have had on your Mac.

Xeth

---

### Post by bodhi.zazen on 2007-11-15
See if these links help :

[https://answers.launchpad.net/ubuntu/+question/2178](https://answers.launchpad.net/ubuntu/+question/2178)

[http://www.linux.com/article.pl?sid=06/10/30/1652211](http://www.linux.com/article.pl?sid=06/10/30/1652211)
	[http://www.antipope.org/charlie/linux/shopper/152.html](http://www.antipope.org/charlie/linux/shopper/152.html)

If at all possible, it would be best to shut down the server and do data recovery from a live CD.

---

### Post by az on 2007-11-20
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

Turn off the computer, image the drive and data carve the files out of the image.

---


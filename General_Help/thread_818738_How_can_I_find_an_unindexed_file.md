---
title: "How can I find an unindexed file?"
date: 2008-06-04
forum: General Help
---

### Post by Kirbster919 on 2008-06-04
Long story short, I used Fiesty Fawn's generic "Sound Recorder" to record a lesson.  I hit "stop" and then instead of saving it, I accidentally hit "record" again.  I never saved the file.

Its my understanding that generally a sound recorder would write to the drive, so there should be an unindexed temp file still around somewhere.  I know the date and aprox. time the file was created.  Is there any way for me to find it?

Thanks,
Kirby

---

### Post by forestpixie on 2008-06-04
Not sure but if it's in /tmp it will be deleted on a reboot so check in there as a first call.

Do you have tracker enabled - you could try to look for files created by time I assume, never used it so can't be sure.

---

### Post by Kirbster919 on 2008-06-04
No dice, it does not appear to be in the tmp folder.  Any other ideas?

Thanks,
Kirby

---

### Post by HalPomeranz on 2008-06-04
You might also check /var/tmp.

Failing that, here's a recipe for finding all files on the system newer than a certain date/time:

```

sudo touch YYYYMMDDhhss /tmp/timestamp
sudo find / -newer /tmp/timestamp

```

In the commands above, substitute the approximate date/time you believe the file was created for "YYYYMMDDhhss".

Be prepared for the possibility that the app deleted your recording after you accidentally hit record the second time.  Good luck!

---

### Post by Kirbster919 on 2008-06-05
It wasn't there, so it must have been deleted.  From what I've read, there's no easy way to find it, and its not important enough to put forth the effort.

Thanks for the help though!

---


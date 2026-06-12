---
title: "Mistake while Mounting"
date: 2007-11-09
forum: General Help
---

### Post by omrsafetyo on 2007-11-09
I made an unexpected mistake while installing a new HD into my PC.

I used the command:

```
mount -w -t msdos /dev/hdb1 /home/omrsafetyo
```

when I meant to say 

```
mount -w -t msdos /dev/hdb1 /home/omrsafetyo/Media_Drive
```

Apparently this is bad.  I was a little worried when I was unable to open my home directory in the browser (after successfully mounting the drive in the correct spot) to browse to my new drive.  I figured it was just running slow, and hit ctrl+alt+backsp to restart x.

When I tried to login, I couldn't.  "Your session has last less than 7 seconds.. blah blah"

I log in to my backup account, and navigate to the home folder in the terminal, and do a quick ls -l


```
dwrxwrx--- root root omrsafetyo
```

:(

It seems I somehow chowned my home folder to root when I mistyped my mount command (I was curious I hadn't received an error on the command..)  I tried chowning it, and it did not work.

Now, I tried unmounting - but this didn't work, it was not added to my fstab.  So I checked my mtab, and found a line linking the /dev/hdb1 to my home directory...  I made a backup of mtab, and then got rid of this line.  Tried chowning again... nothing.

Logged out, back in... nothing.

Can anyone help me??

---

### Post by yabbadabbadont on 2007-11-09
If you didn't modify your /etc/fstab file, then simply reboot and the problem should go away.  :D

---

### Post by omrsafetyo on 2007-11-09
Doh!!!!

Far less of a problem than I thought.  Thank you!

Next question - 

How do I get that mount added to fstab - do I edit manually, or is there a flag or the mount command that will add it?

Also - when I tried mounting my drive to the /home/omrsafetyo/Media_drive  it told me this folder was not a valid mountpoint.  Is there a reason for that??  I had ended up mounting it at /Media_drive ... but that is not optimal for various reasons.

So basically - how do I get this drive mounted to a directory in my home directory, and then how do I get that to stick in fstab?


Thanks a bunch!

---


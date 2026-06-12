---
title: "File transfer from ext disk interrupted by authentication timeout"
date: 2017-01-07
forum: General Help
---

### Post by goemonburo on 2017-01-07
I'm having a frustrating time using rsync to copy files from my old hard drive to my new one.  The old one was encrypted and when I plug it into an external USB I'm asked to authenticate, which I do, choosing the "remember forever" option.

But then, 40 or 60 mins or so into the rsync transfer, a popup appears saying something like "Authentication timeout" and I'm locked out of the drive.  I can't unmount, as it gives an error with "operation in progress" and I can't even navigate to new places on the drive.  And the frustrating thing is that because it's only halfway through the rsync, I have to do it all over again...and it again times out.

I'm wondering if there's a way to turn off the timeout or set a variable that will make it take weeks to treat the drive as idle.  Anyone know what's going wrong here?

Thank you!

---

### Post by TheFu on 2017-01-08
Don't know the issue.

rsync doesn't start over from the beginning, so it should take only seconds to see which old files have already been copied over, then it would push new data.  I'm assuming you are using ```
rsync -avz source targer
```

Manually mount it. Forget the GUI. If you post the output from ```
sudo parted -l
``` and **lsblk** in code tags, perhaps we can help? More info will be needed after the crypt partition is mounted.  I can help if it uses LUKS, but not some other method.
Something like this:

```
sudo cryptsetup luksOpen $DEV $PV
sudo mkdir /mnt/root /mnt/Stuff
sudo mount /dev/mapper/c720*root /mnt/root
sudo mount /dev/mapper/c720*Stuff /mnt/Stuff

``` but this makes lots of assumptions that will not apply to you. Won't know without the output from those commands.

---


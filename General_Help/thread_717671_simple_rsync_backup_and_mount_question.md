---
title: "simple rsync backup and mount question"
date: 2008-03-07
forum: General Help
---

### Post by romac on 2008-03-07
I created a very simple script to backup my music and all my photos/files

I used gnome-schedule to crate a cron job for it, but it only seems to work if I right click on the icon labeled "273 GB drive" and select "Mount Volume"

Then the name of the drive changes from "273 GB drive" to "disk-1" and an icon for "disk-1" pops up on my desktop.

the file system on this drive is ext3

is there any way I can mount this drive automatically?
do i need to add a line to my script to mount the drive?

here's my script:
> #!/bin/bash
rsync -r -t -p -o -g -v --delete -l /home/romac/1Personal /media/disk-1/
rsync -r -t -p -o -g -v --delete -l /home/romac/Music /media/disk-1/

Thanks.

---

### Post by .nedberg on 2008-03-08
You need a line like
```
mount -t ext3 - /dev/sdX /media/disk-1
```

That will mount the disk with devicenode /dev/sdX at /media/disk-1

I recomend you create a folder /media/mydisk or something and change the mount line according to that.

---


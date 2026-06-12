---
title: "ddrescue saves no data when saving to image"
date: 2016-02-23
forum: General Help
---

### Post by kukubau2 on 2016-02-23
Hi all

I've started to rescue data I have on a failing disk with ddrescue.

All or most of the guides recommend saving the data to an image file. First I've saved the data using 'partition to partition' which worked/s well then as I wanted to have more flexibility I've used the 'partition to image'. 

For some reason this is where ddrescue runs but seems to save nothing. After 8 hours or so it saved only 80 MB whereas 'disk to partition' saved the whole 700 MB  on the same amount of time and had only the trimming phase to run.

For saving 'to image', I've mounted a 2nd partition on the destination disk to '/media/ubuntu/laprecov' and ran:

ddrescue -v -d -f -c 32 -b 4096 /dev/sdc2 /media/ubuntu/laprecov/laprecov.img /home/laprecov.log

After 8 hours almost no data was written on the destination disk. ~80 MB.

If I run partition to partition:

ddrescue -v -d -f -c 32 -b 4096 /dev/sdc2 /dev/sda2/ /home/laprecov.log

Runs flawlessly.

What's wrong here?

Thank you

---


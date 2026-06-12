---
title: "Hard Drive full."
date: 2016-05-07
forum: General Help
---

### Post by uwe-bungto on 2016-05-07
I tried to copy files from an external HDD to my Home dir and
received a warning that that HDD was full.  !!!!! 

This is not possible since yesterday I had 330GB free. I checked the
size of each dir and it did not add up to anywhere near being full.

For some unknown reason checked /media from a terminal, there was 3
devices connected with the balance of the data that gave a disk full
warning.

Very interesting since at this time no HDDs were connect externally. One
of the devices mounted as root has been in a suitcase for 3 weeks and
the other 2 are in a 5 bay external rack powered off and the USB 3.0
cable disconnected. These two have video files that I have been
transferring between two external HDDs.

Has anyone an theory as to how this might have happened?

---

### Post by bab1 on 2016-05-07
> **uwe-bungto said:**
> I tried to copy files from an external HDD to my Home dir and
received a warning that that HDD was full.  !!!!! 

This is not possible since yesterday I had 330GB free. I checked the
size of each dir and it did not add up to anywhere near being full.

For some unknown reason checked /media from a terminal, there was 3
devices connected with the balance of the data that gave a disk full
warning.

Very interesting since at this time no HDDs were connect externally. One
of the devices mounted as root has been in a suitcase for 3 weeks and
the other 2 are in a 5 bay external rack powered off and the USB 3.0
cable disconnected. These two have video files that I have been
transferring between two external HDDs.

Has anyone an theory as to how this might have happened?
If you forget to attach a partition (with space available) the data  will be stored at the mount point anyway.  Remember the mount point is just a directory that you are using as a mount point.  I usually put a README.1st file in a mount point directory so I can see when a remote file system isn't mounted.  The README.1st file is obscured when the remote file system is mounted.

---

### Post by uwe-bungto on 2016-05-07
Thanks.
That is a great tip; will do

Paul

---

### Post by bab1 on 2016-05-07
> **uwe-bungto said:**
> Thanks.
That is a great tip; will do

PaulIs what I described what happened?

---

### Post by Bucky Ball on 2016-05-07
Looked in your trash? If you've been fiddled about moving vid files, the wasted space could be in the trash. Empty it.

---

### Post by uwe-bungto on 2016-05-08
> **bab1 said:**
> Is what I described what happened?
I can't say for sure if that is what happened.
I am using an Orico 5 bay USB 3 external enclosure  for backups. It has the tendency to power off and back on if a HDD is inserted or removed. At the time I was copying photos and videos to two HDD in the enclosure. After that backing up those to two other HDD. 
I could be I inserted a HDD during the backup. 
Every thing is back to normal.

Thanks

---

### Post by Bucky Ball on 2016-05-08
> Every thing is back to normal.

In that case please mark the thread as solved using thread tools at the top right of this page. Thanks.

You don't have any idea why it's back to normal that you can share with the community or this just fixed itself? Please share if you did something intentionally (or unintentionally) to fix. ;)

---


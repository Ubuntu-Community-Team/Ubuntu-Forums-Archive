---
title: "SSD trim with encrypted home"
date: 2013-06-18
forum: General Help
---

### Post by RomPirate on 2013-06-18
Another SSD trim thread here. For the record, Yes I have searched and none of the threads seem to address my issue.   I just got a SSD and did a fresh install of Ubuntu 12.04.   Since i'm so paranoid about loosing my laptop and having my information fall into the wrong hands, I figured that checking the "encrypt my home folder" box during installation would deter most theives from accessing my passwords and whatnot.   I'm trying to enable TRIM on my ssd. I've followed many guides, and added "discard" to the partitions in the fstab file. Running the "trim check test" shows that the drive is not "trimming" (Did I say that right?)  [http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)  I've also tried to follow this guide which talks about encryption: [http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)  But /etc/crypttab does not exist.   I would appreciate any help.   Thanks!

---

### Post by whatthefunk on 2013-06-18
I've always recommended this guide.  Page 1 tells how to enable trim and page 2 tells how to test it.
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/)

---

### Post by RomPirate on 2013-06-18
> **whatthefunk said:**
> I've always recommended this guide.  Page 1 tells how to enable trim and page 2 tells how to test it. [http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/)  Thank you for the prompt reply. It is a good guide but unfortunately the guide does not address encrypted /home partitions =(

---

### Post by prodigy_ on 2013-06-18
[http://askubuntu.com/questions/115823/trim-on-an-encrypted-ssd](http://askubuntu.com/questions/115823/trim-on-an-encrypted-ssd)

---


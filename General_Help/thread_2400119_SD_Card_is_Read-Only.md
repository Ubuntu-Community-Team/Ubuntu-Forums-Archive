---
title: "SD Card is Read-Only"
date: 2018-09-02
forum: General Help
---

### Post by merlinus on 2018-09-02
When I insert an SD card into my USB reader, it comes up as read-only.  I can copy the files to my HDD, but cannot delete them nor copy files to the card.

I am now running 18.04, but this never happened with 16.04.

---

### Post by HermanAB on 2018-09-03
There may be a tiny little read only slide switch on the SD card.  If so, move it.

---

### Post by merlinus on 2018-09-03
Of course I checked to ensure the read-only slide switch was in the proper position!  Still opening in read-only mode, and even when logged in as root, I cannot delete nor write to the card.

---

### Post by sudodus on 2018-09-03
Your card might be failing, and one stage in that process is 'gridlock', which makes it read-only. See this link,

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

But let us hope that there is 'only' a software problem, and that it can be solved according to one of the following links,

[Common permissions with Microsoft file systems in Linux](https://askubuntu.com/questions/962318/mount-usb-with-exec-flag-by-default/962323#962323)

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by merlinus on 2018-09-03
Thanks for the info.  Here is how I solved the issue.

Although I was listed as owner with read/write permissions, I could only copy from the card, and not write nor delete, even when logged in as root.  So in the terminal:

sudo chown -hR merlin /dev/sdd

I then uplugged the card reader, and when I plugged it back in, no more read-only problems with sd cards!

---

### Post by Impavidus on 2018-09-03
I don't think that chown command should have done anything. Maybe it was just a dirty contact.

---

### Post by merlinus on 2018-09-06
I do not agree, since 6 different SD cards opened read-only, and after running chown, they all work perfectly in read-write mode.

---

### Post by lordfrikk on 2018-09-06
Was the SD card mounted automatically by the system? If so, what were the mounting parameters? ("mount | grep /dev/sdd" while the SD card is mounted)

---


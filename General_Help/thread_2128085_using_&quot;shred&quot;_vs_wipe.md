---
title: "using &quot;shred&quot; vs wipe"
date: 2013-03-22
forum: General Help
---

### Post by Unguidedone on 2013-03-22
Ok so my computers hardware is failing, and tomarrow i need to send it back to store and they will fix it.  But I want to make sure my hard drive has no personal information on it.  

My plan wasa to install ubuntu 10.10 over 12.10 and open up terminal and put  sudo shred -n7 -v/dev/sda      (this will wipe the harddrive)  but this does not seem to work in 12.10.  I did find a thread:

[http://ubuntuforums.org/showthread.php?t=2035123](http://ubuntuforums.org/showthread.php?t=2035123)

sudo shred /dev/hdx  (so this works with 12.10 right ?)

[http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/)
(i heard this can take more then 100 hours for a secure wipe)

what can i use for like 3 random data passes over the hard drive?

---

### Post by ibjsb4 on 2013-03-22
What about dban?

[http://www.dban.org/](http://www.dban.org/)

---

### Post by slickymaster on 2013-03-22
There's also a suite of tools called secure-delete, that has four tools:

srm - securely delete an existing file
smem - securely delete traces of a file from ram
sfill - wipe all the space marked as empty on your hard drive
sswap - wipe all the data from you swap space.

```
sudo apt-get install secure-delete
```

---

### Post by Stonecold1995 on 2013-03-22
Unless you are expecting someone to use advanced, government-level forensics on the drive, a single pass with dd would work.
```
sudo dd if=/dev/urandom of=/dev/sda
```

You could also use the built in ATA secure erasure function ([https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)), which may "scrub" parts that dd missed.  This would probably be the best way, but it carries a small risk of damaging the firmware, aka "bricking" the device (this is because features like ATA secure erase are not used very often, so they aren't tested as thoroughly and are more liable to contain nasty bugs).  If you still want paranoid-level secure-deletion, than I suggest you use DBAN, which you can configure for the old and mostly unneccesary Gutmman method (35-passes), a 7-pass wipe, 3-pass wipe, or 1-pass wipe (I think) and chose between various PRNGs (for a security/speed tradoff).

Also, I wouldn't use multiple wipes if the hardware that is failing is the hard drive itself.  That would be quite stressful for it.

---


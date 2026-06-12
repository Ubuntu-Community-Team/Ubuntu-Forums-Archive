---
title: "Problem caused by changing concurrency=shell in Gutsy. /etc/init.d/rc corrupted!"
date: 2007-10-29
forum: General Help
---

### Post by mervyn_v on 2007-10-29
Hey there,

I'm having a bit of a problem.

I'll try to explain how it happened. I changed a few settings in some configuration files to speed up my system.
I found the info to do that on [http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

After rebooting, I got the error "HAL error". So I changed the grub and fstab settings back to their original and rebooted. Same error. So I tried changing concurrency=shell in init.d/rc to "none". init.d/rc got corrupted for some reason and I couldn't boot anymore. It said init.d/rc: Permission Denied. I nanoed the file and somehow it's content had changed. All gibberish!I had a backup of the file and tried to restore it. But the same thing happened.

Can't boot anymore. And can't seem to find anything on the web to fix it.

Was also wondering, how do I undo :"sudo tune2fs -o journal_data_writeback /dev/sdc1"?

Need your help guys.

Cheers,
Mervyn.

---

### Post by jaybombalous on 2007-10-30
I did this same thing, but instead when I put back in the 'none' part and saved > rebooted. I just got a code error saying a ( was out of place. :(

But I did get the Hal error with 'shell', so u are not the only one that this happened too.

---

### Post by vikrant82 on 2007-10-30
Same here , but I changed back concurrency to none, and my HAL was happy again. :)

---


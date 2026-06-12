---
title: "fsck every boot - edgy"
date: 2006-10-30
forum: General Help
---

### Post by SlCKB0Y on 2006-10-30
Hi, 

I have been having the same problem as in here:
[http://www.ubuntuforums.org/showthread.php?t=267849](http://www.ubuntuforums.org/showthread.php?t=267849)

whereby fsck checks all partitions on every boot. It does not find any errors. I have had this happen since before edgy was in beta. I am running reiserfs on all my partitions so something like tune2fs would not work for me. 

Does anyone know how to fix this or what is causing this?

Thanks.
Stu.

---

### Post by Azathoth_ on 2006-10-30
Change in your /etc/fstab all the final 1 in at the end of each vfat partitions to 0.

---

### Post by SlCKB0Y on 2006-11-01
wow. I feel really silly. 

Will my reiser partitions now be checked in the event they are unmounted uncleanly though?

I dont want to end up with errors...and WHY was this the default in my Edgy?

---

### Post by JLB on 2006-11-01
it is the reiser partitions causing your "perceived problem" . It is actually that reiser partitions are much slower to mount than the ext3 ones. I had this same issue, converted my / and /home partitions to ext3 and that "perceived problem" went away. it was not that partitions were unmounted uncleanly or anything. you end up dumping out of the usplash screen by taking too long :) due to the time it took for each reiser partition to mount. you then saw the fsck messages and perceived this problem. converting my partitions to ext3 actually shaved 28 seconds of my boot times (according to bootchart)

short story... you don't have a problem. if you don't want to see those messages or want faster boot times, backup, reformat to ext3 and restore your stuff.

---

### Post by kamilvr on 2006-11-03
no need to get rid of reiser, just:
[http://www.namesys.com/faq.html#fstab](http://www.namesys.com/faq.html#fstab)

---


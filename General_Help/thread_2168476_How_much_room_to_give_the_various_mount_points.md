---
title: "How much room to give the various mount points"
date: 2013-08-18
forum: General Help
---

### Post by emerson1979 on 2013-08-18
Hello Everyone
                      I'd like to know what size the partitionn should be for / root, /boot, and /home directories


Thank You

---

### Post by carl4926 on 2013-08-18
You don't need a /boot except under specific circumstances
/ should be 20-30GB
/home as big as you can afford - I typically use 100GB or more

---

### Post by 3rdalbum on 2013-08-18
> **emerson1979 said:**
> Hello Everyone
                      I'd like to know what size the partitionn should be for / root, /boot, and /home directories


Thank You

You don't need to have separate partitions for /root, /boot and /home.

Just one partition for / will work fine. It can sometimes be useful to have /home on a different partition or different hard disk but it's not necessary. In earlier years, you needed a separate /home in order to upgrade Ubuntu without losing your files, but this is definitely no longer necessary.

**If you do need /root, /boot and /home for some reason that is still valid:**

/root will probably be fine with 100 megabytes. MEGABYTES. It'll barely have anything in it.
/boot will never have more than a gigabyte in it. You can probably go with five hundred megs, but if you've got the space a gigabyte will do nicely.
/ should have twenty gigabytes. Thirty if you can afford it. This is where your programs go.
/home should have whatever is left. That's where your videos, music, images, e-mails, settings etc will go.

---

### Post by OrangeCrate on 2013-08-18
> **emerson1979 said:**
> Hello Everyone
                      I'd like to know what size the partitionn should be for / root, /boot, and /home directories


Thank You

This is the guide I used to learn how to partition a hard drive. There are many newer guides if you search for them, but, this one is very easy to follow, and should give you a good base of knowledge on the topic:

[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

Swap size is debated by many. See here for current Ubuntu thinking on the subject:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by RichardET on 2013-08-18
My only remark is to allow for a large enough /opt or /usr for upgrades or new software.  I could enver get why the default formatting for solaris was to dump all space into /export/home.  All upgrades go into /home?

---


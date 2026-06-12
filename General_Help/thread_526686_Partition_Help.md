---
title: "Partition Help"
date: 2007-08-15
forum: General Help
---

### Post by Unrequited on 2007-08-15
I recently got a new (refurbished) pc and having used Ubuntu on my (now deceased) laptop decided to install it. The pc came preloaded with vista and I decided I would dual boot. I went through the installation and at the partitioning screen I allocated 16gb to the vista partition (or so I thought) and the remainder of about 136gb to ubuntu. However Grub did not have vista in the list and further investigation revealed that my partition actually looks like this:

/dev/sda1 filesystem Unknown size 136.06gb
/dev/sda2 filesystem ext3 size 16.58gb          used 3.04gb   unused 13.54  flags boot
/dev/sda3 filesystem extended size 753.05mb
    /dev/sda5 filesystem linux-swap size 753.05mb

I'm cautious about changing anything since I'd like to keep vista intact and since it was me doing things without checking that lead to this. Any help would be much appreciated.

---

### Post by Fully216 on 2007-08-15
I just noticed something interesting about your swap size.  The recommended size is:

1. RAM < 1 Gb swap = RAM X2.
2. RAM > 1 Gb swap = 2 Gb

Some claim a swap size of > 1 Gb is excessive. The 2 Gb recommendation is "conservative".  I personally have 2 Gb RAM so I have a 2 Gb swap space.  

Vista is not supposed to be run without at least 1 Gb of RAM.  You can run it at bear bones, without any of the nice features at 512 Mb, but I hear it is slow and not worth it.

Just a thought while you were dealing with the partitioning issues.

This guide should help.  It recommends you go in and change your grub list, althought vista/longhorn should be shown at the bottom under 'other operating systems.'  If not, it is likely something went wrong.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by dabl on 2007-08-15
If understand what I read on other folks' posts, you need to use Vista's partitioner to shrink the Vista main partition, and THEN install Ubuntu on the empty space that is left.

---

### Post by Unrequited on 2007-08-15
> **dabl said:**
> If understand what I read on other folks' posts, you need to use Vista's partitioner to shrink the Vista main partition, and THEN install Ubuntu on the empty space that is left.

Yeah I've been looking around and apparently me using the Ubuntu installer to partition was unwise. Although I only got the pc today and can't access vista because it claims the cd key is invalid (something I've emailed the company I bought from about).

---


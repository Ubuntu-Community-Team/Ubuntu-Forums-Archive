---
title: "Phew - Close one"
date: 2018-03-11
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2018-03-11
Hi All
Just had a close shave with insanity, I'd backed up my pc with the intention of installing windows10 as the main system....that is until I received an email from a friend asking why she should download windows updates, are they important? Phew that changed my mind for me as generally, and fixes are released far faster for Linux the M$ so sticking to Xubuntu...

On another note, how is updating from one release to the next?  I haven't tried it for a few years, but always found problems when I did...slow downs, strange colour configs etc.  Has it improved?

Cheers

Paul

---

### Post by sudodus on 2018-03-11
Sometimes upgrading from one release to the next works well, but it is still risky and there may be some (minor or major) annoying problems even if it works. It depends very much on what you have installed (on top of the basic system, that you installed).

It is often much faster to install a fresh system and copy the personal files, do the tweaks and install new program packages, when you need them. You have probably got a lot of program packages, that you never use nowadays ...

A compromise is to keep the the content of the **/home** directory, ***create a home partition***, and install via the alternative 'Something else' at the partitioning page. That way you will keep the personal files, that you store 'at home' and also many (but not all) tweaks.

You can also create a separate **data** partition with the label 'data', where you keep your personal files. That makes it easy to backup the personal data separately, and makes the installation of a fresh system independent of your personal files.

---

### Post by oldfred on 2018-03-11
Because I follow sudodus suggestion of a separate /mnt/data partition and have at least 2 / (root) partitions.

I had 14.04 and 16.04 which became my main working install soon after 16.04 was released. Actually my 14.04 has already been overwritten with 18.04 just to see what has changed, but 16.04 is still my main working install and will be until 18.04 is released or perhaps a bit later depending on how well it initially works.

With multiple installs, I find the data partition works better as I do not want to share /home. Generally you can upgrade with a separate /home, but then if you boot back into old system, some settings may not apply. Systems are usually designed for upgrade but not tested to know if work on downgrade.
And if I am testing an install I do not want those changes in my main working install. So I keep /home inside / and use /mnt/data for all my data.

Those that find upgrade works, do not have or have  or have turned off all ppas and uninstalled all proprietary drivers. Many times it is the non-standard files in a ppa or drives that need to be new versions and old version interferes with new update.

---

### Post by tinylagarto on 2018-03-11
Actually it works quite good, I mean going from one release to the next. 

> **oldfred said:**
> 

Those that find upgrade works, do not have or have  or have turned off all ppas and uninstalled all proprietary drivers. Many times it is the non-standard files in a ppa or drives that need to be new versions and old version interferes with new update.

But I second that. I do not use PPAs and do not have proprietary hardware.

---


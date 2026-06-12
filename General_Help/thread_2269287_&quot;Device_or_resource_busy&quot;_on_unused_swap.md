---
title: "&quot;Device or resource busy&quot; on unused swap partition"
date: 2015-03-14
forum: General Help
---

### Post by halfbeing on 2015-03-14
I recently clean-installed 14.10 and found that it came with a broken cryptswap setup. After trying to follow various instructions on various forums to get cryptswap working, all without success, I am now trying, in desperation, to set up an unencrypted swap, but here I'm blocked too.

When I swapon /dev/sda5 I get "read swap header failed". So then I try mkswap /dev/sda5, but I get "Device or resource busy". However I can't work out what is using it. I have the /dev/mapper/cryptswap1 line in /etc/fstab commented out.

Obviously things are in a big mess. Ideally I would like to have an encrypted swap partition (with hibernate enabled if possible), but at this stage I will be happy to have any kind of swap that works. Can anyone help me get something working?

---


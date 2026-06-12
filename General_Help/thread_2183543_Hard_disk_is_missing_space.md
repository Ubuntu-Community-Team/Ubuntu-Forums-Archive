---
title: "Hard disk is missing space"
date: 2013-10-25
forum: General Help
---

### Post by symone.cobain on 2013-10-25
Hello. After I uninstall the Windows 8.1, and reinstall the ubuntu, my hard disk is missing space.
I dont know what to do.
My Hd has 1TB and the gparted shows only 930GB.
What should I do?

---

### Post by oldfred on 2013-10-25
You have GiB vs. GB, reserved space and journal. And depending on which tool you use they may include or report differently.

 [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.

 1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes

        sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print

Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdd3

---

### Post by symone.cobain on 2013-10-25
Very thank you. Now I can understand.
The gparted measures the hard disk as GiB.
[COLOR=#000000]
[/COLOR][COLOR=#000000]Thank you[/COLOR]

---


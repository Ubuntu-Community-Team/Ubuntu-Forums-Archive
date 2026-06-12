---
title: "Uninstall windows help"
date: 2006-07-06
forum: General Help
---

### Post by drfox on 2006-07-06
I'd like to uninstall Windows from my notebook, but I'm worried that I won't be able to boot Ubuntu. 
I am attaching a screenshot of my partitions, and, as you can see, windows is on sda1, my bootable partition. 
If I delete sda1, will grub be able to find sda3 (which is where I think / is)? Will sda3 still be sda3?

Thanks for your help!

Larry

---

### Post by nudnik on 2006-07-06
It would be better to erase the the information within the partition using a program like "Kill Disk" if there is any personal data you would rather not resurface at a later date, possibly in the wrong hands. 

You can always reinstall grub (properly configured) if needed using the "alternative" install CD without loss of data from Ubuntu. 

Wait for replies in addition to mine, as someone may have a more elegant solution.

---


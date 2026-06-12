---
title: "AMD 970 Northbridge and AMD SB950 Southbridge Compatability Issues"
date: 2017-10-15
forum: General Help
---

### Post by dhwalden79 on 2017-10-15
Hi. I was given a machine and using a very limited budget i upgraded it to an improved specification. It is by no means the latest and greatest machine but it will do what i want it to do.

I bought a **Gigabyte GA-970A-DS3P (2.x) **motherboard with an AMD FX-4300 chip. In a windows build everything was fine. In a Fedora build everything was ok (Except I didn't like fedora as much as ubuntu!).  When i install Ubuntu/Kubuntu/Mint/Neon any ubuntu derived linux build I have a problem when i cannot get the USB3 ports to work at the same time as the USB1 and 2 ports. I have to enable the IOMMU option in my bios which then disables the usb 3.0 ports and makes the 1 And 2 ports work.  I am using the machine this way currently and after a bit of digging it appears to be a compatibility issue with the north and south bridge chips on the motherboard.

My question is why does the chipset work on fedora but not on ubuntu and is there a fix available for this problem?

---

### Post by kurt18947 on 2017-10-15
Here's something:

[https://ubuntuforums.org/showthread.php?t=2336077](https://ubuntuforums.org/showthread.php?t=2336077)

I don't have that MoBo so no first hand experience. Good question about why it would work on Fedora.

---

### Post by dhwalden79 on 2017-10-15
Just found another post after about 4 months of reading through the forums which gave a suggestion i hadn't seen so i tried it and it worked!!!! 

It appears that the uefi/bios did something if you changed the iommu option in the bios and linux couldn't detect both usb 1.1 and 2.0 hubs and 3.0 hubs.

By editing the grub and telling linux to control the iommu itself everything works! 

I am so happy to finally have all my usb ports working on an ubuntu linux build! :)

The link to the solution i used was......

[https://ubuntuforums.org/showthread.php?t=2111223&page=4](https://ubuntuforums.org/showthread.php?t=2111223&page=4)

---

### Post by wildmanne39 on 2017-10-15
Glad it is working, please use thread tools at the top of the page to mark the thread solved.

Thanks

---


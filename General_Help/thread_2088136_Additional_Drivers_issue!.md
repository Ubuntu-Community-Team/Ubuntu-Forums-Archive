---
title: "Additional Drivers issue!"
date: 2012-11-25
forum: General Help
---

### Post by jcblafrance on 2012-11-25
I recently installed 12.10 on my dell inspiron 5010, I downloaded the driver needed for the wifi card but it will not reflect in the additional drivers. If anyone knows a way of getting the drivers to work please reply.

---

### Post by Mark Phelps on 2012-11-25
The "additional drivers" option downloads and installs the drivers for you.  It's not something that you configure or customize yourself.

Need to know HOW you downloaded the drivers -- as there are different ways of doing this.

---

### Post by jcblafrance on 2012-11-25
I downloaded the driver from the intel linux iwlwifi project site, I just cant seem to find and initiate the driver I downloaded. I am a noob in the linux world, and want to learn as much as possible.

---

### Post by coffeecat on 2012-11-25
> **jcblafrance said:**
> I downloaded the driver from the intel linux iwlwifi project site

Intel wifi should (mostly) just work in Ubuntu - the inbuilt drivers should suffice. Even if you do need to install wifi drivers, downloading them from the manufactuer's website is usually not the best way to go. That's a Windows habit - you usually approach things differently in Linux.

Are you sure your wifi chipset is Intel? Dell often use Broadcom chipsets for wireless and some of those do need extra bits installing.  

Open a terminal and run this command:

```
 lspci | grep -i wireless
```

If that doesn't give any output, try:

```
lspci | grep -i 802.11
```

That should tell you the wireless make and chipset. Post the output. If it is Broadcom, have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---


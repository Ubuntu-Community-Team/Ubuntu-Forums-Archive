---
title: "What type of CPU do I have?"
date: 2015-04-24
forum: General Help
---

### Post by nu2this2 on 2015-04-24
Hello,

I am trying to install a later version than what I have now, I' m trying to go from V10.10 to V14.04 . The following message appears when I try.

**"This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot--please use a kernel appropriate for your CPU".**
 My question is, how can I find the latest version of Ubuntu that is appropriate with an i686 CPU.

Thanks.

---

### Post by dino99 on 2015-04-24
i386 stands for the 32 bits, and amd64 stands for 64 bits
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Yellow Pasque on 2015-04-24
This will tell you more than you ever wanted to know about your CPU.
```
cat /proc/cpuinfo
```

Most likely, you accidentally downloaded the 64-bit image. You have to be sure to select **32-bit** on the dropdown menu. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Or, get it with a torrent (that's the recommended method) using this direct link: [http://releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-i386.iso.torrent](http://releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-i386.iso.torrent)

---

### Post by mörgæs on 2015-04-24
As advised in the other thread you should not go for Ubuntu but one of his lighter relatives.

---

### Post by nu2this2 on 2015-04-24
Hello,
Was able to get the 14.04.2 L.T.S. iso. I burned it and ran it from the disc. The WIFI connection worked, Firefox worked etc. I decided to install. Chose the potion to upgrade from 10.10 to 14.04.2. I also chose to download all the packages it was going very slowly and I was getting messages that certain things were failing. Finally the whole install failed. I saw a message saying to clean the lens on the CD drive. I shut down the computer and tried to restart and the screen showed Local host login: with a blinking cursor. What should I do?

Any suggestions?

Thank you.

---

### Post by Bashing-om on 2015-04-24
nu2this2; Hello;

I would verify the liveDVD's integrity:
boot the liveDVD and as soon as the bios screen clears depress any key -> language screen; escape key to accept the default -> boot options screen;
choose " check disk for defects " .. let the test complete and if no defects are found, as advised reboot.

Depending on what personal files might be on this hard drive, and what your particular use case may be, why not take the easy way and choose to "erase the hard drive and install ubuntu " ?
Be aware this option will do just that - erase all contents on the hard drive, and use the entire drive for ubuntu.

[INDENT][INDENT]easy does it
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-24
Bashing om ,

Thanks very much, I did the disc check and no errors were detected. Since there is nothing of importence on this laptop I will try to erase all the contents of the HD and do a fresh install.

---


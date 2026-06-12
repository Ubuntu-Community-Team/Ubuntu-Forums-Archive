---
title: "boot issue - asus t100ta new install"
date: 2020-04-12
forum: General Help
---

### Post by javicane on 2020-04-12
Hello, 

I have successfully installed ubuntu mate 19.10 in a tablet asus t100ta (which had windows 10) mostly following this guide:

[http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/](http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/)

Everything was ok but when I did the first reboot, I got blue screen "Your PC/Device needs to be repaired... Error code: 0xc0000225 ... Press windows key for UEFI firmware settings"
So I was able to boot by entering to grub command line and set the path to kernel & initdr (as it's said in the guide). Then I installed boot-repair and run it but still the same issue. 
This is the boot repair report link:

[https://paste.ubuntu.com/p/mMJhPfGkfW/](https://paste.ubuntu.com/p/mMJhPfGkfW/)

In the BIOS boot options I have: ubuntu (twice) & Windows boot manager. None of them is working. 
Any Ideas?

Thanks.

---

### Post by CelticWarrior on 2020-04-12
> So I was able to boot by entering to grub command line and set the path to kernel & initdr (as it's said in the guide)

The guide is for an older kernel version. Did you changed it accordingly?

---

### Post by javicane on 2020-04-12
I update both paths (kernel & initdr) and I'm able to boot every time. The problem is always in the first reboot. I hope someome could use the boot repair info to see what's wrong.
(Although I didn't try to boot again since the boot repair "fix". Because I saw that it did some changes and I want everything to be as is in the report)

---


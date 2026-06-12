---
title: "ubuntu 12.04 LTS wont boot from disk"
date: 2013-02-27
forum: General Help
---

### Post by vidkid901 on 2013-02-27
hello everyone reading this post I have used elementary for the last few months but wanted to try Ubuntu but whenever I try to boot from the live CD I burned all that happens is I get a black screen with a white flashing underscore and in case you wanted it I have the md5sum

---

### Post by MoebusNet on 2013-03-01
Hmmm... The list of md5sums seems to indicate that you've downloaded the amd64 version of Ubuntu, but have you checked the md5sum of the iso image itself?

[http://releases.ubuntu.com/precise/MD5SUMS](http://releases.ubuntu.com/precise/MD5SUMS)

Have you checked the documentation on how to boot Ubuntu?

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

You didn't mention the hardware you are using; are you sure your cpu can boot 64-bit or does it need 32-bit?

If you have an older video card, you may need to use the *nomodeset* boot option to use the VESA video driver rather than the radeon video driver to get you started.

---

### Post by vidkid901 on 2013-03-01
sorry did not post specs and my CPU can run win7 64 so it can support 64 bit but here is my specs intel core I5 cpu 3.2 GHz 8GB of mushkin 2GB sticks and a radeon HD 4600 and a asus mother board and I do know how to boot from a cd

---

### Post by Bufeu on 2013-03-01
Try to boot from USB, worked for me.

---

### Post by vidkid901 on 2013-03-01
sadly I dont have the ability to do that

---

### Post by vidkid901 on 2013-03-03
ok everyone thnks for some help I found out i can install it through windows and just boot from that then install so thanks

---

### Post by MoebusNet on 2013-03-03
It looks as though your older video card isn't well supported in the latest Ubuntu releases, though it appears to be supported in 12.04LTS.

[http://ubuntuforums.org/showthread.php?t=2073193](http://ubuntuforums.org/showthread.php?t=2073193)

Installing Ubuntu into Windows via Wubi is a solution (you'll be using the Windows video driver), but if you ever lose your Windows you will also lose Ubuntu because you have installed Ubuntu as a Windows application. You may want to consider continuing to investigate either a dual-boot (Windows/Ubuntu) installation or possibly a Ubuntu guest in a virtual environment:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by vidkid901 on 2013-03-03
dangit sadly the wubi did not work but i dought its the hardware cause useing dameon tools and virtual box I could run a ubuntu live cd??? i wonder what that means?

---

### Post by vidkid901 on 2013-03-03
yes finaly i fixed it i switched disk drives with my disc reader and burner insted of my blueray drive and it magicly fixed it for some reason

---

### Post by MoebusNet on 2013-03-03
Try this:

Go to the section titled 'How to enable kernel options on the livecd (before install)'

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You may need the *nomodeset* and/or the *acpi=off* boot options; try them & see.

---

### Post by MoebusNet on 2013-03-03
> **vidkid901 said:**
> yes finaly i fixed it i switched disk drives with my disc reader and burner insted of my blueray drive and it magicly fixed it for some reason

i think bluray compatibility is still a work in progress, but I don't own a bluray so YMMV.

---


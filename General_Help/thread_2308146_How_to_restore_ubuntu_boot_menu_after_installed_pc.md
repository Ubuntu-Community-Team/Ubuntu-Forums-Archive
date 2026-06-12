---
title: "How to restore ubuntu boot menu after installed pc-bsd in another partition"
date: 2015-12-31
forum: General Help
---

### Post by luke40 on 2015-12-31
I have just installed PC-BSD in another partition of my disk. Now the PC-BSD bootloader with only one entry(PC-BSD, of course) override the boot menu of ubuntu.
How do I restore the ubuntu boot menu and enable both operating systems to be bootable?

---

### Post by QDR06VV9 on 2015-12-31
See if this helps..[http://unix.stackexchange.com/questions/859/how-do-i-add-pc-bsd-freebsd-to-grub-2-boot-loader](http://unix.stackexchange.com/questions/859/how-do-i-add-pc-bsd-freebsd-to-grub-2-boot-loader)
I have not done this myself..Please read carefully and have good back-ups.
Regards

---

### Post by luke40 on 2016-01-01
> **runrickus said:**
> See if this helps..[http://unix.stackexchange.com/questions/859/how-do-i-add-pc-bsd-freebsd-to-grub-2-boot-loader](http://unix.stackexchange.com/questions/859/how-do-i-add-pc-bsd-freebsd-to-grub-2-boot-loader)
I have not done this myself..Please read carefully and have good back-ups.
Regards


The method is a little complicated and I dare not take the risk so I reinstalled ubuntu 15.10 to the partition of PC-BSD
and by doing so restored the ubuntu boot menu and give up installing PC-BSD. Thanks anyway.

Btw, is this problem solved according to the above outcome?

---

### Post by QDR06VV9 on 2016-01-01
If you get the bug again to install and dual boot Ubuntu with BSD.
:D Not so [COLOR=#000000]complicated at all just need to....[/COLOR]
When you install FreeBSD or PC-BSD, _**do not install boot loader at all**._ After finishing installing FreeBSD, boot Ubuntu and your bootloader(Grub) should be left intact) and from there you can add FreeBSD to your Grub on Ubuntu.


1. in /etc/grub.d/40_custom, edit 
```
gksudo <your text editor here> /etc/grub.d/40_custom
```
Then add to _**the bottom of that file**_
```
menuentry "FreeBSD" {
    set root=(hd0,2)
    chainloader+1
}
```
Change the version you are using eg: "FreeBSD" or "PC-BSD"
By the way, (hd0,2) is the second partition of the first hard disk, adjust it to your system.

Update the grub.cfg:
```
sudo update-grub
```
FreeBSD or PC-BSD should appear in your Grub menu when you reboot next time.


Cheers!

---

### Post by luke40 on 2016-01-02
I also read advice about not to install PC-BSD bootloader, but I didn't notice which step during the installation can I make the choice.
Many thanks especially if you can tell me how can I not to install PC-BSD bootloader.

---

### Post by QDR06VV9 on 2016-01-02
> **luke40 said:**
> I also read advice about not to install PC-BSD bootloader, but I didn't notice which step during the installation can I make the choice.
Many thanks especially if you can tell me how can I not to install PC-BSD bootloader.
It has been a year or more since I have last installed PC-BSD with a Debian dual-boot..So I was quite suprised to learn that..
> The option to install a boot loader during PC-BSD installation is no longer present in the GUI, hence the Devs to the discussion around recovering from "accidental use" of that previously available option.

So with this new information _**I should put myself as the tester here and not you**._
I will in the next day or so, Do a dual-boot install with Ubuntu installed first then PC-BSD Next and then show how I did the process, witch will inculde the re-install of grub to boot from.
And will update this thread only if you have real intentions to follow through, So just let me know if this is something you really want.
Regards

---

### Post by luke40 on 2016-01-02
> **runrickus said:**
> It has been a year or more since I have last installed PC-BSD with a Debian dual-boot..So I was quite suprised to learn that..


So with this new information _**I should put myself as the tester here and not you**._
I will in the next day or so, Do a dual-boot install with Ubuntu installed first then PC-BSD Next and then show how I did the process, witch will inculde the re-install of grub to boot from.
And will update this thread only if you have real intentions to follow through, So just let me know if this is something you really want.
Regards


To say the truth, I am a novice for Linux, I installed PC-BSD just for curiosity and for my interest in UNIX. That's why I give up installing PC-BSD so easily.
_**So you don't have to actually do the test yourself.**_
However, if you do and do it successfully, I think that myself as well as many others will much appreciate because it will do much help if we decide to install PC-BSD afterwards.
Many thanks for so much help you gave.

---


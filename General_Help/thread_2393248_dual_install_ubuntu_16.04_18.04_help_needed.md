---
title: "dual install ubuntu 16.04 18.04 help needed"
date: 2018-05-31
forum: General Help
---

### Post by seekertom on 2018-05-31
I have 16.04 lts running well on 1 tbhd, mostly empty. I tried to install 18.04 from dvd, split hd about 50-50 during process, but messed up along the way.

I dont see how to boot into 18. In 16 i see the 480gb volume, lots of folders in it, but 18 isnt listed in grub menu. can I fix it as is, should I try to reinstall, or what?

im not sure how to include screen print here, or id be happy to.
st):P

Sorry for the delay in getting back here. Unfortunately, Due to age and length of time between posts, I lose track of all thats been done during the lifetime of the issues, but bottom line is this: now I boot to ubuntu 16.04, top of the list, by default, but also have 18.04 on grub menu, so I can also select it to boot into. First couple tries after getting into 18, I tried to install some other apps which failed, but after several reboots + ? other operations 18 will run quite happily, and the apps that were problematic at first seem to also be running with no further issues. Luvit when stuff works. Hateit when I dont know why.

I'll probably slap in a new 1 tb hd as sandbox and try to recreate the issue, installing 16.04 lts first, followed by 18.04 lts and see what happens.

Oh, btw, when I select 18 to boot into, screen fills with what appears to be a verbose scenario, showing me each step it takes during bootup. doesnt happen with 16. Is this normal, is it because it's 2nd choice or what?
Thanks again for all yalls help. Couldnt do it without.
st

---

### Post by deadflowr on 2018-05-31
What shows when you run
```
sudo update-grub
```
from 16.04

---

### Post by oldfred on 2018-05-31
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by seekertom on 2018-06-07
```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.13.0-43-generic
Found initrd image: /boot/initrd.img-4.13.0-43-generic
Found linux image: /boot/vmlinuz-4.13.0-41-generic
Found initrd image: /boot/initrd.img-4.13.0-41-generic
Found linux image: /boot/vmlinuz-4.13.0-39-generic
Found initrd image: /boot/initrd.img-4.13.0-39-generic
Found linux image: /boot/vmlinuz-4.13.0-38-generic
Found initrd image: /boot/initrd.img-4.13.0-38-generic
Found linux image: /boot/vmlinuz-4.13.0-36-generic
Found initrd image: /boot/initrd.img-4.13.0-36-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 18.04 LTS (18.04) on /dev/sda6
done
```
this what you want?
st

---

### Post by deadflowr on 2018-06-07
> this what you want?
Sure.
So now when you reboot do you have an option in the boot menu for 18.04?

---

### Post by Dennis N on 2018-06-07
If you installed ubuntu 18.04 after ubuntu 16.04, then 18.04 would be the OS to display the grub menu at startup. 18.04 would be started from first entry, which will probably just say "Ubuntu", and you would see "Ubuntu 16.04..." somewhere below that.

---

### Post by seekertom on 2018-06-11
During bootup, at the time I would usually see a grub menu listing ubuntu, plus other options for memory test etc, i only get a momentary black and white screen saying something about sda... too fast to read. And when it boots fully, i'm at 16, not 18.

---

### Post by yancek on 2018-06-11
Read the post above by oldfred and go to the boot repair site, download and run it as suggested.  YOu will get a link which you should post here for members to view.  The output of update-grub by itself isn't that helpful.

---


---
title: "Ubuntu won't shutdown on Lenovo z570"
date: 2015-08-29
forum: General Help
---

### Post by md96360 on 2015-08-29
Hello.

I have a problem with my laptop Lenovo Ideapad z570 and new Ubuntu 14.04.3 LTS. I had this OS on this same laptop and it worked perfect. Than I replaced my old HDD with new SDD, intalled Ubuntu 14.04 and had a issue with wiffi and bluetooth (I solved it by googling). But the problem with shutting down I can't solve. 

When I try to shut it down, it goes to screen with Ubuntu logo and freezes there, so I have to shut down and power off the laptop using a Power Off button.

After a lot of googling and trying, I ask for help here.

EDIT: Previously, with old HDD I had a dual OS (Windows 7 and Ubuntu 14.04), and now only Ubuntu 14.04.

---

### Post by mörgæs on 2015-08-30
Does it shut down if you push Return or Space at the screen where it freezes?

---

### Post by md96360 on 2015-08-31
Sorry for delayed reply. No, when it freezes it doesn't react at all, no matter what I press (except Power Off button).

---

### Post by dino99 on 2015-08-31
to better know what is going on; swith to verbose by remove 'quiet splash' into /etc/default/grub, then run 'sudo update-grub'

but you can clean the system with "clean/autoclean/autoremove" commands, gtkorphan is also usefull
then update, run 'sudo apt-get install -f' & 'sudo dpkg --configure -a'
and as always your logs should help you to: dmesg, syslog mainly

---

### Post by md96360 on 2015-08-31
First thank you for answering. Since I'm pretty much new with ubuntu, could you please write me full commands I need to enter in terminal?

---

### Post by cubenerd on 2015-08-31
Open Terminal:
type "sudo grub-update"

You can also see if you can shutdown from terminal by typing in "sudo shutdown 0"

---

### Post by md96360 on 2015-08-31
> **kylesuero said:**
> Open Terminal:
type "sudo grub-update"

You can also see if you can shutdown from terminal by typing in "sudo shutdown 0"


This is what I get:

> sudo grub-update
sudo: grub-update: command not found


But If you ment update-grub, than:

> sudo update-grub

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
done

---

### Post by QDR06VV9 on 2015-08-31
Should be
```
sudo update-grub
```
Try that
Ninjad! You beat Me
Regards

---

### Post by md96360 on 2015-09-05
I ques there is no help for me :(:(

---

### Post by md96360 on 2015-09-05
[[img]https://farm6.staticflickr.com/5740/21164878511_02a2ef9a97_z.jpg[/img]](https://flic.kr/p/yfgx1t)[Issue](https://flic.kr/p/yfgx1t) by [rile.tm86](https://www.flickr.com/photos/38301814@N08/), on Flickr

---

### Post by lu_ramaia on 2015-11-30
> **md96360 said:**
> Hello.

I have a problem with my laptop Lenovo Ideapad z570 and new Ubuntu 14.04.3 LTS. I had this OS on this same laptop and it worked perfect. Than I replaced my old HDD with new SDD, intalled Ubuntu 14.04 and had a issue with wiffi and bluetooth (I solved it by googling). But the problem with shutting down I can't solve. 

When I try to shut it down, it goes to screen with Ubuntu logo and freezes there, so I have to shut down and power off the laptop using a Power Off button.

After a lot of googling and trying, I ask for help here.

EDIT: Previously, with old HDD I had a dual OS (Windows 7 and Ubuntu 14.04), and now only Ubuntu 14.04.



I had the same problem with a Lenovo B50-30 and a fresh install of Lubuntu 14.04.3 LTS. I solved upgrading the system BIOS.
Hope it helps

---


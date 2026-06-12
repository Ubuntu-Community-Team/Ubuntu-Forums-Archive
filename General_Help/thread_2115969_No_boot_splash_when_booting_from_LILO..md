---
title: "No boot splash when booting from LILO."
date: 2013-02-14
forum: General Help
---

### Post by E-Rackattack on 2013-02-14
Before I give my problem (More like annoyance) out, some info on my system: 

My computer is a triple-boot system, with which I use Slackware's LILO as my bootloader to choose between Ubuntu 12.10, Slackware 14 and FreeBSD 9.

(Now, my little annoyance):

When booting Ubuntu under GRUB, Ubuntu's boot splash (which I'm assuming is done with plymouth) pops up just fine after selecting your OS. That's normal. But for some reason I have yet to understand, when I boot Ubuntu from LILO, it doesn't start up plymouth (or whatever the botsplash program is) at all, leaving me to watch all this scrolling text. It's not a big deal since I don't mind scrolling text, but I'd like to have a nice-looking way to start up my OSes.

Does anyone have ideas on fixing this? Thank you! :D

---

### Post by oldfred on 2013-02-14
I really do not know lilo, but do you have the quiet splash in the options line for Ubuntu?

[http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX)
Note that LILO uses the syntax:
image = mykernel
  label = mylabel
  append = "myoptions"

... whereas SYSLINUX uses the syntax:
LABEL mylabel
  KERNEL mykernel
  APPEND myoptions

... grub legacy boot stanza
title 1 Most Current Ubuntu on sda8
root (hd0,7)
kernel /vmlinuz root=/dev/sda8 ro [COLOR=Red]quiet splash[/COLOR]
initrd /initrd.img

... grub2
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro [COLOR=Red]quiet splash[/COLOR]
        initrd /initrd.img
}

---

### Post by dwilkens on 2013-10-25
> **E-Rackattack said:**
> Before I give my problem (More like annoyance) out, some info on my system: 

My computer is a triple-boot system, with which I use Slackware's LILO as my bootloader to choose between Ubuntu 12.10, Slackware 14 and FreeBSD 9.

(Now, my little annoyance):

When booting Ubuntu under GRUB, Ubuntu's boot splash (which I'm assuming is done with plymouth) pops up just fine after selecting your OS. That's normal. But for some reason I have yet to understand, when I boot Ubuntu from LILO, it doesn't start up plymouth (or whatever the botsplash program is) at all, leaving me to watch all this scrolling text. It's not a big deal since I don't mind scrolling text, but I'd like to have a nice-looking way to start up my OSes.

Does anyone have ideas on fixing this? Thank you! :D

 I have half a dozen OS and 5 HDs in my old box - I understand what you mean. Ubuntu is tuned to work fine with GRUB, Ubuntu does not like LILO. But LILO is much easier to configure than GRUB or the complicated GRUB2 so I never wanted to deal with GRUB. But Ubuntu 12.x updates always fail when it detects LILO instead of GRUB. I do not care any longer, I use LILO and have a solution in place. 

I found 2 ways to start Ubuntu (12.04) with LILO: An easy way and the normal way. 

Normal way:
Tell LILO about the Ubuntu boot files.  
 Disadvantage: Your nice "Plymouth" fails, Ubuntu updates can not deal with it and fail, too. 

Easy way: 
Put the GRUB boot loader stuff in the MBR of one of your hard disks. Then tell LILO to boot the MBR of that disk just like you start Windows! 
 By booting the MBR the GRUB stuff is triggered and GRUB boots Ubuntu.  So you boot GRUB using LILO!  LILO does boot GRUB without issues. 

Result: The "easy" way works perfect - Ubuntu can edit its GRUB with each kernel update. And the user can stick with lovely LILO.


Some lilo.conf snippets: 

proven example for normal start:

 image=/mnt/UbuntuBoot/boot/vmlinuz-2.6.38-8-generic
 initrd=/mnt/UbuntuBoot/boot/initrd.img-2.6.38-8-generic
 append="root=/dev/sdd2" ## has to use Ubuntus way to label
 root=/dev/sdd2 ## has to use Ubuntus way to label
 label=Ubuntu11           ## the LILO - label

proven example for "easy" start:

# boot GRUB in MBR with LILO 
other=/dev/hdc
label=GRUB_Ubuntu1204

Examples using LILO 22 under RedHat 7.3

---

### Post by andrew.46 on 2013-11-01
Best way is to install lilo to mbr and then install grub to to root of its own Ubuntu partition, chainload this with lilo... Here are the details as I used it quite some time ago:

[http://www.linuxquestions.org/questions/slackware-14/dual-boot-ubuntu-and-slackware-12-1-a-636549/#post3127665](http://www.linuxquestions.org/questions/slackware-14/dual-boot-ubuntu-and-slackware-12-1-a-636549/#post3127665)

**Edit:** Obviously *hda* is gone now...

---


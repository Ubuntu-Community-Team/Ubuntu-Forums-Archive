---
title: "Need Urgent Help: GRUB Error 17"
date: 2006-07-22
forum: General Help
---

### Post by Jucato on 2006-07-22
When I woke up this morning (morning in my place, around 01:00 UTC), I booted up my computer normally. I did what I normally do and started up some apps. However, after a few minutes of smooth running, I here a few beeps. Then my whole system stalls, while the LED that lights up when the hard drive is reading remained lit. After a few minutes of trying to shutdown my system normally, it froze up completely, necessitating a reset. Then my troubles started

Upon rebooting, my 2nd hard drive (where my Linux partition, my /home partition, and my FAT32 shared partition resided) wasn't detected by the system. And since GRUB was installed on my first hard drive (XP), thanks to Kubuntu's installer  :-X, there was no way for me to have access to either OS, unless I restored Window's bootloader. So I popped in  the Windows CD, went into recovery console, and typed *fixmbr*. That restored the bootloader on the MBR of hda. One problem solved.

After a few minutes (ok, almost half an hour) of pulling out and putting back in some IDE and power cables, I finally got my drives working again (I think I'm having some power supply problems). My problems were far from over, though. Not wanting to have to overwrite the MBR of hda again, I opted to reinstall GRUB on the MBR of hdb. So I booted up my Kubuntu Desktop CD, went into Konsole and typed these commands:

```

sudo -i
grub
find /boot/grub/stage1
root (hd1,0)
setup (hd1)
logout
``` 
(stage1 was found in the first partition of my 2nd hard drive, hd1,0 = hdb1)

There were no notable errors. I had previously reinstalled GRUB before using this method, so I thought everything would be ok. I was wrong. Upon booting, I got these messages:

> 
Booting "Ubuntu 2.6.15-26-k7"
root (hd1,0)
Filesystem unknown, partition type 0x7

kernel /boot/vmlinuz-2.6.16-26-k7 root=/dev/hdb1 ro quiet splash

error 17: Cannot mount selected partition 

This is the first time I experienced this error message so I'm a bit worried. Also, the Windows XP entry in GRUB didn't work. It just displayed the usual message (like chainloader +1), but then returned to the GRUB menu.

I tried another whack at it, this time using *grub-install* from the Desktop CD

```

mkdir /home/ubuntu/kubuntu
sudo mount /dev/hdb1 /home/ubuntu/kubuntu
sudo grub-install --root-directory=/home/ubuntu/kubuntu hd1
``` 

Again, the output did not display any errors. But I still got the Error 17 message. Either I did something totally wrong, or there's really no hope for my machine other than a complete reinstallation.

I'm currently running on my Windows XP installation. While I have nothing personal against XP, I'm very anxious to get back to my beloved Kubuntu. Nothing beats the real thing.

I'd greatly appreciate any help. TIA

---

### Post by philippe_carlo on 2006-07-22
Relax, nothing is wrong. I assume you swapped the hard drives, in order to boot from the Linux one? Then, hda1 becomes hda2 and vice versa, right? Second, you have to trick windows into thinking it's installed on the first HD, by using some mapping commands, that go in the head of the windows entry. 

```

map (hd0) (hd1)
map (hd1) (hd0)

```

---

### Post by Jucato on 2006-07-22
I didn't really swap drives. All I did was to change the BIOS to boot from hdb rather than hda. Does that count? I'll try your suggestion. If that doesn't work, I'll try installing GRUB in the MBR of hda. If that still doesn't work...

... I guess I just have to reinstall...

---

### Post by zxee on 2006-07-22
> **Fenyx said:**
> I didn't really swap drives. All I did was to change the BIOS to boot from hdb rather than hda. Does that count? I'll try your suggestion. If that doesn't work, I'll try installing GRUB in the MBR of hda. If that still doesn't work...

... I guess I just have to reinstall...

You shouldn't have to re-install and yes changing the bios boot order will affect grub AFAIK. You could change it back again record what messages you get and post them here. And although you probably already know this if you are having power supply problems it's best to get a new or replacement PS.

---

### Post by Jucato on 2006-07-22
Guys, thanks for trying to help. But mapping didn't work. I was so frustrated that I just did what I should have done: I just reinstalled GRUB on the MBR of hda. Simple solution, right?

*sigh*

Thanks again for your time and effort!

---


---
title: "Windows overwrote GRUB boot loader"
date: 2008-06-25
forum: General Help
---

### Post by Tiersin on 2008-06-25
I duel boot Vista and Ubuntu 8.04 on my laptop. Yesterday my Vista partition crapped out on me and required a reformat and clean install of Vista. Unfortunately, as an unforeseen consequence, my system now uses windows default boot loader (just goes straight to Windows) instead of GRUB. Is there any way to correct this other than reinstalling my Linux partition?

---

### Post by VMC on 2008-06-25
> **Tiersin said:**
> I duel boot Vista and Ubuntu 8.04 on my laptop. Yesterday my Vista partition crapped out on me and required a reformat and clean install of Vista. Unfortunately, as an unforeseen consequence, my system now uses windows default boot loader (just goes straight to Windows) instead of GRUB. Is there any way to correct this other than reinstalling my Linux partition?

Below came from [HERE]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")
Here's the quick and easy way to re-enable Grub.

```
sudo grub
find /boot/grub/stage1
root (hd?,??)
setup (hd?)
quit

```
where hd?,?? is returned from find command. 

============Same thing=========================
1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub "prompt", and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

   ```
 sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit
```

=======More of same==================
And finally:



Other:
```
sudo mount -t ext3 /dev/sda2 /mnt
sudo grub-install –root-directory=/mnt /dev/sda
```

(change sda2 and sda to your linux system and drive, could be hdaX and hda)

---


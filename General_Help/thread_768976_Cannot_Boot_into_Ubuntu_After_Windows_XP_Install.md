---
title: "Cannot Boot into Ubuntu After Windows XP Install"
date: 2008-04-26
forum: General Help
---

### Post by Cheeseweasel on 2008-04-26
Hello!
I am currently doing an ICT course. Those of you who have done a course like it will know what I mean when I say it is *tedious*. It's loads of dreary, repetitive tasks and I have to take a print-screen of myself doing all of them. My teacher doesn't like Linux so she insists I use Windows XP Professional in English (I already had XP Pro; it was in Japanese, my home language, though, so I had to download it in English) to do it.

I downloaded XP Pro and gave it access to 10gb of my hard disk- the rest was still Ubuntu 7.10. Of course, the windows bootloader took over from GRUB. I did the coursework and booted from the LiveCD to do the trick detailed [here](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/) but now when booting my BIOS tells me 'Operating System not found' and hangs on that screen.

Can anybody please give me any help on how to get GRUB back on there? As soon as I've done that, I'm definitely deleting Windows XP for good and never installing it back on there.

Thanks
Kieran

---

### Post by tamoneya on 2008-04-26
take a look at super grub.  It works perfect for me when I had a similar problem.

---

### Post by Cheeseweasel on 2008-04-26
Hm- I downloaded the ISO for the latest version of Super GRUB and burned it to a DVD+R disc but that doesn't seem to be able to boot from the BIOS, even when I chosoe to boot from CD. It hangs for a bit and the drive spins, but it then stops and I get 'Cannot find operating system'. Thanks, but any other help?

---

### Post by zvacet on 2008-04-26
@ **Cheeseweasel**


That guide you used is no good,because one line is missing.Try with [this.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by Cheeseweasel on 2008-04-26
Hello
Thank you, but when I type

```
grub> find /boot/grub/stage1
```

I simply get

```
Error 15: File not found
```

Upon inspecting my filesystem, the entire /boot/ folder appears to have disappeared. Can anybody offer any help?

---

### Post by ghost_ryder35 on 2008-04-26
possibly you could copy the boot directory from the live cd to your hard drive.  
 
[]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Cheeseweasel on 2008-04-26
Perhaps simply a log of the terminal will help deal with my problem:

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/root
mount: special device /dev/sda6 does not exist
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
mount: mount point /mnt/root/proc does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
mount: mount point /mnt/root/dev does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

```[color=red]Of course, it didn't work here, so I tried changing to /sda1: (I know little about hard disks)[/color]
```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
bash: /home/ubuntu/.bashrc: Permission denied
root@ubuntu:/# sudo grub
Probing devices to guess BIOS drives. This may take a long time.
```
Although it looked promising, it didn't work. The problem seems to be here:

```
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
bash: /home/ubuntu/.bashrc: Permission denied
```

Once again, any assistance is much appreciated.
Kieran

---

### Post by Cheeseweasel on 2008-04-27
Hello - sorry to bump the thread, but I still quite urgently need help.

---

### Post by Naatan on 2008-04-27
I hope you didn't enter the EXACT code mentioned here;

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

hd0 - refers to the hard disk, if you have multiple hard disks than this might be hd1 or hd2..
hd0,0 - refers to the first partition on hd0.. whilst Ubuntu might be installed on the second or thirdt.

It doesn't harm testing with this, if it's not the right partition; it won't boot.. simple as that.

---


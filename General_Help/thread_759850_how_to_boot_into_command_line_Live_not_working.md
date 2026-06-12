---
title: "how to boot into command line Live not working"
date: 2008-04-19
forum: General Help
---

### Post by jwxie on 2008-04-19
Hello, i have already installed my ubuntu
but since I installed WIn 2008 Server later, it completed wipe out the Grub loader
so i asked and here is one solution
[http://ubuntuforums.org/showthread.php?t=748707&highlight=jwxie](http://ubuntuforums.org/showthread.php?t=748707&highlight=jwxie)

i like this method
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

but it requires to boot from live cd
and since my desktop, i think it's the video card problem, i cannot boot into live cd
when i installed my ubuntu, i used the alternative cd
and afterward i need to reconfigure and update 7.1 with x-server

**so i need to enter my command live**
and do the sudo grub

does anyone know how to boot into my system in command line???

also, how do i check which parition have i installed???
you see root(hd0,0) if i am not sure, then how do i check when i enter the command line?

thank you

---

### Post by Diabolis on 2008-04-19
You could try to boot with a lighter linux distribution live-cd, such as damn small linux.

It uses a older kernel, which gives support to older hardware, and its very low on requirements. You can do sudo grub from it. Thats what I use.

Steps to reinstall grub:

```

find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

---

### Post by bodhi.zazen on 2008-04-19
You can boot the ubuntu desktop (live) CD.

When the graphical system fails, hit 

Ctr-Alt-F1 or Ctrl-alt-F2 to get a command line interface.

The default user is Ubuntu with an empty password.

---

### Post by jwxie on 2008-04-19
ty! both method works
and i got back to grub loader
but since Web server 2008 is installed after ubuntu did
so the grub loader doesn't have its record

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
i check it, it tells me the step
but i am not sure which partition did the WIn Web Server2008 is located....

---

### Post by bodhi.zazen on 2008-04-19
List your partitions with 

```
sudo fdisk -l
```

Now grub uses a different way of identifying partitions.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by Diabolis on 2008-04-19
You can see the order in which your partitions are set with gparted. Don't look at the sda numbers, focus on the order in which the partitions appear. The first one from left to right is the number 0.

---


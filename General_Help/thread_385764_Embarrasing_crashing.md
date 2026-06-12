---
title: "Embarrasing crashing"
date: 2007-03-16
forum: General Help
---

### Post by bogoliubov on 2007-03-16
I have Feisty on a small partition on my iBook, mainly to play around with.
But after a recent kernel update my system didn't want to boot. So I tried to select "old" (instead of "Linux") at the Yaboot prompt. It turned out that I didn't have any old image.

So I booted a Live-CD and thought that I could copy over the files from the Live-CD to the /boot folder. By mistake I overwrote the current kernel (instead of putting in an old one). 
Of course, the system can't boot (or, to be more precis, it stops booting after a while).


Any ideas on how I can repair this? What files/sym-links to I need to have in /boot? I don't want to reinstall Feisty if I don't have to...

---

### Post by kidders on 2007-03-16
Hi there,

Thankfully, to use a broken Linux install, you don't absolutely _have_ to be able to boot it. If I had your problem, I would let a CD take care of the booting part, chroot into my broken install, and use apt to reinstall a working kernel & rewrite my bootloader.

If you want to try that, there's plenty of help around to get you started. You would do something like this:

Make somewhere to mount your broken root filesystem
```
sudo mkdir /mnt/ubuntu
```

Mount your root filesystem
```
sudo mount /dev/whatever /mnt/ubuntu
```

Create a /proc and a /dev inside the chroot
```
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev/ mnt/ubuntu/dev
```

Enter the chrooted environment
```
sudo chroot /mnt/ubuntu /bin/bash
```

Update your environment
```
source /etc/profile
```

Exactly how much work to do depends on what you want to do inside the chroot. For instance, if you need internet access, you may want to copy in the CD environment's /etc/resolv.conf. Some applications may also like to have /sys mounted.

In any case, as long as you use a boot CD from a Linux distro that is at least *reasonably* similar to Ubuntu, you should be able to treat your chrooted system as though it had booted _itself_ up. For you, the next steps would be to reinstall your kernel and maybe re-run yaboot's setup.

Once you're done, you can reboot your machine and see what happens...

Return to the CD's environment
```
[CTRL]+D
```

Dismount everything
```
sudo umount /mnt/ubuntu/proc /mnt/ubuntu/dev /mnt/ubuntu
```

Cross your fingers
```
sudo reboot
```

I hope that helps.

---

### Post by bogoliubov on 2007-03-16
Thanks, I'll give it a try!

---

### Post by bogoliubov on 2007-03-16
Great, it worked like a charm! Did what you described, remove the old kernel and installed a new one. Everything works perfectly!

Thanks alot for the help!

---

### Post by kidders on 2007-03-16
Excellent. :-)

Chrooting is a neat trick that's useful in all sorts of situations that involve running one Linux system inside another one. I'm glad it worked for you.

---


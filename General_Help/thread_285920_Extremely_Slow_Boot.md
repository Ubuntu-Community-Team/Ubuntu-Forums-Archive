---
title: "Extremely Slow Boot"
date: 2006-10-27
forum: General Help
---

### Post by mad0master on 2006-10-27
I've installed Ubuntu 6.06 boot time was faster than my Win XP. Was waiting for 6.10 release. After installation it boots almost two minutes... =-0

I've tried to switch off some deamons that start but didn't mansge do smth better (only checkfs).

Where should i dig? Laptop: Asus M9v [Intel 1.73 Centrino, 512Mb RAM, 80Gb HDD, 256 Mb swap]

---

### Post by Jingo on 2006-10-27
* sudo aptitude install bootchart
* reboot
* attach bootchart to thread ( /var/log/bootchart )

Might be your usplash settings ! Look at /etc/usplash.conf for resolution, you need to "sudo dpkg-reconfigure linux-image-2.6.17-10" if changing something.

BTW: If you want hibernation to work sometime, you'll need more swap space than you have ram, as swap part. is where things are dumped on hibernation..

---

### Post by mad0master on 2006-10-27
It's magic! :KS  Attached that pic, trying to analyze it myself... 

My resolution is ok i think 1024x768

---

### Post by mad0master on 2006-10-30
Hey! Any ideas?
I've configured /etc/network/interface by hand, a little bit faster, but nothing more! Give me a hint... :confused:

---

### Post by McGregor927 on 2006-11-01
Sadly, I've had the same problems with my laptop.  It's a Sony VAIO.  With dapper it booted and ran just fine, but I reinstalled with edgy and now it takes longer to boot and to get my kde session up and running.

---

### Post by mad0master on 2006-11-01
[http://ubuntuforums.org/showthread.php?t=287537](http://ubuntuforums.org/showthread.php?t=287537)
They are discussing the same problem ](*,) 
Hmmm, is it time for Ubuntu team to pay attention to this posts? :-k

---

### Post by McGregor927 on 2006-11-01
I installed Kubuntu, but I can't image that would be the problem, as it's only use kde as the interface on top of everything else.  Here is my boot chart.  It takes over a minute to boot.  I know it didn't take this long on dapper.

---

### Post by dtfinch on 2006-11-01
Starting today, I too experienced an extremely slow boot. It seemed too soon since my last forced fsck to be that, and in the past it seemed to take only a minute when it happens every 30th boot.

But dmesg shows a 4 minute break on the ext3 initialization step:
[17179624.908000] eth0: no IPv6 routers present
[17179875.740000] EXT3 FS on hda1, internal journal

If that was a fsck, it was unusually long, non-verbose, and off-schedule.

I don't think usplash has worked since I upgraded to Edgy. Ubuntu has a blank screen until it reaches the gdm login.

---

### Post by McGregor927 on 2006-11-01
I disabled the network devices and it only took off 2 seconds.  These laptops are always such a pain...

---

### Post by mad0master on 2006-11-01
Try disabling all acpi, that are not for your laptop, e.g. ibm, toshiba etc.

---

### Post by rseaward on 2006-11-15
I have Edgy Kubuntu loaded with Ubuntu and Xubuntu desktops on a sony vaio with XP already on.  XP had the first 2 partitions.  Then I had a partition with 4 GB on which I had Ubuntu (before I knew I could add Ubuntu onto my Kubuntu).  I had 8 GB for the Kubuntu partition.

After finding out I coulod add the Ubuntu desktop, I removed the ubuntu, but could not merge the partition with kubuntu.  So I had to merge it with the second XP drive.

Kubuntu was starting up within 20 seconds.  Ever since I made the changes and merged the drive, reinstalle3d Grub, Kubuntu now takes atleast 2 minutes.

The bar shows it loading until it almost gets 1/2 way (about 4/10) and then it stops there.  There is no more hd activity, and then a couple mintues later it continues to load and finishes in a few seconds to the log in screen.

COuld someone help me know what has made it go slow and how I can fix it.

thanks.

---

### Post by carbonic on 2006-11-19
My edgy boots way slower than Dapper as well.
Annoying.

---

### Post by -NabLa- on 2006-11-23
same here, on a sony vaio VGN-FS285M. Very slow boot.

---

### Post by kafo on 2006-11-23
I also have Sony Vaio FS and also had extremely slow boot. The solution for me was to install linux-image-386 and linux-restricted-modules-386. I then removed generic kernel and restricted modules. It seems that the generic kernel uses 686 optimized kernel which doesn't seem to work.

I hope this helps someone.

Best Regards, Saso

---

### Post by monckywrench on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903) worked for me.

---

### Post by pavicnat on 2008-01-19
yeah I have the same problem on my laptop, and I have the same specs as the first poster in this thread! Perhaps the Ubuntu team should start paying attention. However, my slow boot started only when I tried configuring a wireless network (which didn't work might I add). 

I shall try some of the methods posted here.

---

### Post by linuxfreak003 on 2008-02-05
k, i found this on some other forum i guess and it fixed my problem... i can't redirect you to the thread though because i couldn't find it and had to figure it out/ remember it on my own again. this happens to me like every time i update my comp or at least the kernel stuff.
go to /boot/grub/menu.lst (open it with whatever you want but remember to open it with root)
find the kernel you are booting e.g. mine looked like this
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2bfdacc7-e31f-4dbf-b65b-338a47641413 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
(note: that is just the kernel i am booting, it might be on the other but idk cuz i didn't care as long as it worked for what i need)
i don't understand it myself but all you have to do is remove "ro quiet splash" off the kernel line and remove the last line ("quiet").
should look like this
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2bfdacc7-e31f-4dbf-b65b-338a47641413
initrd		/boot/initrd.img-2.6.22-14-generic
```
 It might just be that now it's verbose and i can see what is going on so it seems faster but the first time i tryed it it was about 3 min faster, don't ask me why :P. I don't know about having a splash screen over it or anything cuz i never use one anyway. although it shouldn't be too hard to figure out if you wanted it there.

---

### Post by jdbell63 on 2008-03-06
Thanks for the tip.

---

### Post by bobberJR65 on 2008-04-14
Thanks linuxfreak003!
I thought I had already edited menu.lst
The boot is just fine now!

---

### Post by Rippy on 2008-04-14
Does doing that menu.lst edit stop the progress bar from appearing during startup? I kind of like it :P

I do wish Ubuntu started up faster though. There was a time where it would boot up a minute faster than my Windows partition, but on my new PC Windows boots up in 30 seconds while Ubuntu takes 2 minutes :/

---

### Post by gcorrea on 2008-04-22
The tip given by linuxfreak003 is really good. Worked perfectly in my notebook! Boot is now done in half the previous time.

---

### Post by jakupl on 2008-04-22
> **Rippy said:**
> Does doing that menu.lst edit stop the progress bar from appearing during startup? I kind of like it :P

I do wish Ubuntu started up faster though. There was a time where it would boot up a minute faster than my Windows partition, but on my new PC Windows boots up in 30 seconds while Ubuntu takes 2 minutes :/

you could try doing this instead, 

```
sudo gedit /etc/usplash.conf
```
change from 1280 x 1024 to 1024 x 768

```
sudo update-usplash-theme usplash-theme-ubuntu
```

let me know if it helps.

---

### Post by philphil on 2008-05-28
I can't believe that actually worked, removing "quiet" literally HALVED my boot time

---


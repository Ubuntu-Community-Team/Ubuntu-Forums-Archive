---
title: "Booting Ubuntu from an external"
date: 2007-09-01
forum: General Help
---

### Post by LoganSerman on 2007-09-01
I've seen this same type of thread on these forums before, but can't find a solution to my own problem.

At first, I thought you could just install Ubuntu (at first, I used Xubuntu 7.04) on the external and boot it whenever the external was turned on, otherwise it would boot to my internal hard drive (WinXP). Then I realized that the installer installed GRUB on my internal, and I got GRUB Error 21.

I got out my copy of the Ultimate Boot CD and used fixmbr to restore my original MBR on the WinXP hdd. It worked, I now had a useless Linux external hard drive and a booting WinXP internal. I still wanted Linux, so I searched my problem and went back to fix it.

This time I used an Ubuntu 6.10 CD and started ubiquity. I installed GRUB to /dev/sda instead of hd0, so that GRUB would boot from the external, not the internal.

I figured that was the solution, and booted up. Nope. I still booted to the WinXP hard drive and now I have another useless Ubuntu install on my external. My BIOS is set to boot from CD, Removable Drive, and then HDD. I'm not sure if its recognizing the external on boot-up or not, tell me how I can check and I'll do so because that's the problem.

Any help would be appreciated :)

---

### Post by meierfra on 2007-09-01
Try this (this should install grub onto your external hard drive)

Boot the Ubuntu Live CD. In a terminal:

```
sudo grub
```

```
find /boot/grub/stage1
```

The output should of the form (hdx,y),  (probably (hd1,0))

```
 root (hdx,y)
```

```
setup (hdx) 
```

```
 quit 
```

You should be able to boot into Ubuntu now. If you can boot into Ubuntu, but do not get an option to boot into windows, you need to edit the file "menu.lst" (If you need help that you can google it or come back here  for help)

---

### Post by LoganSerman on 2007-09-02
I did that, the terminal told me it was successful, but I still boot straight into Windows. No GRUB or Linux :(

Keep in mind I want to be able to bring this external over to other peoples houses and boot into Ubuntu off of their machine without installing GRUB or screwing up their MBR.

I hope thats possible.

---

### Post by meierfra on 2007-09-02
Here are a couple of howtos for installing  ubuntu on a external drive:

[http://ubuntuforums.org/showthread.php?t=80811]("http://ubuntuforums.org/showthread.php?t=80811")

[http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external]("http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external")

---


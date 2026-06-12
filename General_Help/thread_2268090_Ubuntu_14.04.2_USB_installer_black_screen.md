---
title: "Ubuntu 14.04.2 USB installer black screen"
date: 2015-03-06
forum: General Help
---

### Post by polochamps on 2015-03-06
Hi,

When booting my Ubuntu 14.04.2 USB installer, it proceeds to grub only then just displays black screen after choosing.
I didn't encounter this problem on Ubuntu 14.04.1, 15.04 and Elementary OS Freya Beta 2.
I always use Rufus when creating my UEFI installer and the usual settings (GPT both usb and target drive/CSM off) that worked with the OSes mentioned.

Thank you

---

### Post by Bucky Ball on 2015-03-06
When at the list of kernels after boot (the grub menu) choose your kernel and instead of hitting enter, hit 'e'. 

At the end of the line that ends with 'quiet splash' leave a space and add:

nomodeset

Follow the instructions at the bottom of the screen to save and boot. Any different? If that works, we can make it permanent.

PS: 15.04 is not released until April and still testing. Unless you don't mind unexpected breakage and know your way around Ubuntu or are willing to learn quickly, leave it alone.

---

### Post by sudodus on 2015-03-06
You can try another tool to flash the iso file to the USB pendrive. Maybe [mkusb]("https://help.ubuntu.com/community/mkusb") (from linux) or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") (from Windows) will succeed with Ubuntu 14.04.2 LTS.

There might also be a driver problem (with the graphics or wifi chip). In that case you can try various [boot options]("https://help.ubuntu.com/community/BootOptions"). Start with **nomodeset**.

An alternative is to install Ubuntu 14.04.**1** LTS and check if it can be updated and upgraded without problems.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by polochamps on 2015-03-06
> **Bucky Ball said:**
> When at the list of kernels after boot (the grub menu) choose your kernel and instead of hitting enter, hit 'e'. 

At the end of the line that ends with 'quiet splash' leave a space and add:

nomodeset

Follow the instructions at the bottom of the screen to save and boot. Any different? If that works, we can make it permanent.

PS: 15.04 is not released until April and still testing. Unless you don't mind unexpected breakage and know your way around Ubuntu or are willing to learn quickly, leave it alone.

Hi Bucky Ball,

I tried your solution until I can bypass the problem by installing the Nvidia drivers. 
My concern is why does the 14.04.**2** specifically had this problem whereas the 14.04.1, 15.04 and I would also add 14.10 does not exhibit this kind of problem?
Is it possible to release an updated ISO with the applied fix?

Thank you

---

### Post by polochamps on 2015-03-06
> **sudodus said:**
> You can try another tool to flash the iso file to the USB pendrive. Maybe [mkusb]("https://help.ubuntu.com/community/mkusb") (from linux) or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") (from Windows) will succeed with Ubuntu 14.04.2 LTS.

There might also be a driver problem (with the graphics or wifi chip). In that case you can try various [boot options]("https://help.ubuntu.com/community/BootOptions"). Start with **nomodeset**.

An alternative is to install Ubuntu 14.04.**1** LTS and check if it can be updated and upgraded without problems.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Hi sudodus,

I think that win32 disk imager would format the boot partition as MBR.
I would try dist-upgrade if there's no alternative solution anymore.
I just can't see why is this happening only on 14.04.2.

Thank you

---

### Post by sudodus on 2015-03-06
Win32 Disk Imager simply copies every bit from the iso file to the pendrive. I use it (and I tested a lot when I was writing the wiki page), and I know that it works, also for UEFI :-)

I'm not sure why it is happening for you. Either you have problems because of the tool for flashing to the pendrive, or it is a driver issue. Both of these problems can appear in one version but not in other versions.

---

### Post by oldfred on 2015-03-06
What nVidia card/chip?

I have had to use nomodeset since about 10.10? And built it into my grub boot of every new ISO, so did not know that at least with 14.04 it did boot without nomodeset in UEFI mode. Have not tried 14.04.2.

It may just be a regression on the open source driver. nVidia has started helping the developers of the open source driver, but the open source driver keeps adding some of the newer features to support newer cards and sometimes that causes other issues.

---

### Post by polochamps on 2015-03-06
> **sudodus said:**
> Win32 Disk Imager simply copies every bit from the iso file to the pendrive. I use it (and I tested a lot when I was writing the wiki page), and I know that it works, also for UEFI :-)

I'm not sure why it is happening for you. Either you have problems because of the tool for flashing to the pendrive, or it is a driver issue. Both of these problems can appear in one version but not in other versions.

Oh. Nice tip!:KS Thanks!
Maybe the tool but I suspect that it's the version of Nouveau driver in 14.04.2 iso. Much newer than 14.10 and 15.04? That I don't know.


> **oldfred said:**
> What nVidia card/chip?

I have had to use nomodeset since about 10.10? And built it into my grub  boot of every new ISO, so did not know that at least with 14.04 it did  boot without nomodeset in UEFI mode. Have not tried 14.04.2.

It may just be a regression on the open source driver. nVidia has  started helping the developers of the open source driver, but the open  source driver keeps adding some of the newer features to support newer  cards and sometimes that causes other issues.

Got a GTX 660Ti - Kepler.
There seems to be no problem on 14.04 - 15.04. Just on this point release of 14.04 I encountered this one.
Yeah maybe there are regressions on the version of Nouveau they included in this build.

---

### Post by sudodus on 2015-03-06
You can try various [boot options]("https://help.ubuntu.com/community/BootOptions"). Start with **nomodeset**.

And if that works, you can install ***proprietary nvidia drivers*** (test those available). But the alternative to start with 14.04.1 LTS and update/dist-upgrade is a good alternative, that might work well.

---

### Post by sammiev on 2015-03-06
I'm sure you checked the file checksum with at least md5sum before you flashed your usb media. Just a thought.

---

### Post by sudodus on 2015-03-06
> **sammiev said:**
> I'm sure you checked the file checksum with at least md5sum before you flashed your usb media. Just a thought.

+1, Yes it happens that downloads fail, so it is good to check (unless you use torrent, because there is a built-in check).

---

### Post by polochamps on 2015-03-06
> **sudodus said:**
> You can try various [boot options]("https://help.ubuntu.com/community/BootOptions"). Start with **nomodeset**.

And if that works, you can install ***proprietary nvidia drivers*** (test those available). But the alternative to start with 14.04.1 LTS and update/dist-upgrade is a good alternative, that might work well.

Yeah I'm running it right now with the proprietary driver but what bothers me is the issue in which it was not on the other said operating systems.
I don't know if it's related or not but I had an issue with Steam with some dependencies about mesa in which I also didn't encounter this problem with the other versions of Ubuntu.
It's resolved right now but still didn't know what triggered it. Thread - [http://ubuntuforums.org/showthread.php?t=2268104](http://ubuntuforums.org/showthread.php?t=2268104)

> **sammiev said:**
> I'm sure you checked the file checksum with at  least md5sum before you flashed your usb media. Just a thought.

Yes it's a match sir.

---


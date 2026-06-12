---
title: "K3B copy slooooow??"
date: 2007-03-21
forum: General Help
---

### Post by ArgentSilver on 2007-03-21
So I was trying to copy a data CD with K3B and the initial copying from the CD to hard drive file was so painfully slow (looked like it was going to take about 20 min) that I gave up and took it over to a Windows box with Nero to make the copy.

Is this normal? Or is there something that can be configured to speed that up? Or is there a better app. than K3B?

---

### Post by tijmz on 2007-03-21
I had the same thing this evening and tried to use GnomeBaker, but that had even more trouble reading the disc. So at least in my case, I wouldn't blame the app.

If anyone has any idea what else could cause this problem I'd be much obliged :)

---

### Post by kpkeerthi on 2007-03-21
Did you check if [DMA is turned on?]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM")

---

### Post by ArgentSilver on 2007-03-23
Well, turning on DMA didn't help. It seems that the CD speed during the read is slow. Normally the CD spin-up can be heard, but not when K3B is reading a CD for copying.

Have I really found something that works better under Windoze?

---

### Post by tijmz on 2007-03-29
Hi all,

I think I managed to fix it on my installation.

When I turned on the DMA as per the link above, I did this for both my CD-ROM drive (in my case /dev/hdd) and my CD/DVD burner (/dev/hdc). Result: I could read fast from the CD/DVD burner and then burn, but my CD-ROM was still slow. Obviously, I wanted to read from the CD-ROM and burn with the burner, so I wasn't satisfied.

I looked through the fstab (/etc/fstab) and I found that no entry regarding my CD-ROM was there. So I copied the line about the burner, altered it somewhat and remounted:

**/etc/fstab:**
```
/dev/hdc        /media/dvdrw0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

To do this you have to make sure that the directories (in this case /media/[..] actually exist. Reloading fstab resulted in higher reading speed from my CD-ROM.

Now I have no idea why this works, since I am not completely sure what it means to edit fstab in this way. The way I get it, fstab tells the system what devices to mount, but I would figure not mounting a CD-ROM would result in no CD-rom activity whatsoever, instead of slower activity. Then again, I am completely new to Linux and perhaps I am understanding things wrongly.

I hope this helps speeding up your CD reading as well.

---

### Post by ArgentSilver on 2007-03-29
Huh, how 'bout that!

Worked for me too....

And now the CD spins up to a fast speed and copies speedily. :KS

---


---
title: "Lubuntu 16.04 not shutting down"
date: 2016-08-20
forum: General Help
---

### Post by steveminchington on 2016-08-20
Hi all, I am a new user on here, but not new to Linux. First time using Ubuntu - I have just done a fresh install of Lubuntu 16.04 64bit which went ok. Just have a small problem of it not shutting down. When you click shut down, it goes to the shut down screen but just hangs there, so you have to power off, which I would think is not good for the system!
Anyone have any ideas what to look for? Thanks in advance, Steve.

---

### Post by oldrocker99 on 2016-08-20
Welcome to the forums! There is more than one way to shut down.

Try this:
```
sudo shutdown -P now
```

---

### Post by steveminchington on 2016-08-20
> **oldrocker99 said:**
> Welcome to the forums! There is more than one way to shut down.

Try this:
```
sudo shutdown -P now
```

Thanks for the reply - just tried this but it didn't work. Steve.

---

### Post by oldrocker99 on 2016-08-21
What happens when you shut down? Does the computer just sit there? Does it appear to shut down and restart? You might try this:```
sudo pm-hibernate
```

This won't shut your computer down, but it **should** put it into hibernation, in which your machine is copied to the swap partition, shuts down, and comes back up as it was when you turn it back on.

---

### Post by steveminchington on 2016-08-21
> **oldrocker99 said:**
> What happens when you shut down? Does the computer just sit there? Does it appear to shut down and restart? You might try this:```
sudo pm-hibernate
```

This won't shut your computer down, but it **should** put it into hibernation, in which your machine is copied to the swap partition, shuts down, and comes back up as it was when you turn it back on.

It just hangs on shutdown. The last two lines on the shutdown log read:

systemd-shutdown[1]: failed to finalize DM devices, ignoring
reboot: Power down

And that's where it stops.

I tried sudo pm-hibernate and that seems to work, although looking at the shutdown log, everything seems to be packed up and put away so maybe it won't do any harm powering it off. I don't know what DM devices are though.

---

### Post by gordintoronto on 2016-08-22
[http://superuser.com/questions/131519/what-is-this-dm-0-device/131520](http://superuser.com/questions/131519/what-is-this-dm-0-device/131520)

---

### Post by steveminchington on 2016-08-22
> **gordintoronto said:**
> [http://superuser.com/questions/131519/what-is-this-dm-0-device/131520](http://superuser.com/questions/131519/what-is-this-dm-0-device/131520)

Thanks gordintoronto, I found this while searching for answers. DM=device mapper! I partitioned the drive using LVM, so that figures. I have found a lot of people experiencing similar shutdown problems but no answer that works for me yet!

---

### Post by banceu_sergiu_ione on 2016-08-22
What about
```
 sudo systemctl poweroff 
```

---

### Post by poorguy on 2016-08-22
How old is your computer.

I had a shut down problem with a desktop with Ubuntu 32 / 64 bit 16.04 didn't matter which. 
This desktop would work perfectly with Ubuntu 14.04 no shut down problem at all. 

I tried all of the so called fixes and it didn't make a difference.
Someone on another forum mentioned that my system bios appeared to be old and suggested to upgrade my system bios so I did and no more shut down problems.

This may be related to your problem and may not only a suggestion worth investigating IMO.

---

### Post by steveminchington on 2016-08-23
> **banceu_sergiu_ione said:**
> What about
```
 sudo systemctl poweroff 
```

Thanks for your suggestion, unfortunately it didn't work.

So far I have tried:

shutdown now
shutdown -P
shutdown -h
poweroff
systemctl poweroff
halt -p
pm -hibernate

None of these have worked. The last one did go into hibernation from where I could boot back up but it caused another problem. It flagged up a system software error which I sent a report for.

---

### Post by steveminchington on 2016-08-23
> **poorguy said:**
> How old is your computer.

I had a shut down problem with a desktop with Ubuntu 32 / 64 bit 16.04 didn't matter which. 
This desktop would work perfectly with Ubuntu 14.04 no shut down problem at all. 

I tried all of the so called fixes and it didn't make a difference.
Someone on another forum mentioned that my system bios appeared to be old and suggested to upgrade my system bios so I did and no more shut down problems.

This may be related to your problem and may not only a suggestion worth investigating IMO.

Hi poorguy, my install is on a Dell/Wyse thin client, 2011. AMD64 dual core 1.6ghz, 2GB ram, 120GB ssd. It has a Phoenix securecore tiano bios which is UEFI - not that old but AFAIK not upgradeable.

---

### Post by banceu_sergiu_ione on 2016-08-23
Try this 2 forms too

```
 systemctl -i poweroff 
```
```
 systemctl -f poweroff 
```

do you get any fail output when run it ?

---

### Post by steveminchington on 2016-08-24
> **banceu_sergiu_ione said:**
> Try this 2 forms too

```
 systemctl -i poweroff 
```
```
 systemctl -f poweroff 
```

do you get any fail output when run it ?

Hi banceu_sergiu_ione, thanks for your suggestion. I tried both of these but neither worked. Every time I get the same fail output:

systemd-shutdown[1]: failed to finalize DM devices, ignoring

---

### Post by banceu_sergiu_ione on 2016-08-24
How about you have a look at your syslog/kernel.log/boot.log. See what you can find at time you run the command line.

Try also
```
 init 0 
```

---

### Post by steveminchington on 2016-08-25
> **banceu_sergiu_ione said:**
> How about you have a look at your syslog/kernel.log/boot.log. See what you can find at time you run the command line.

Try also
```
 init 0 
```

No, that didn't work either. Still the same thing. I've looked at the logs, but to be honest they don't mean anything to me. There are hundreds of entries for a boot and shutdown, and at shutdown time no errors that I can see.

---

### Post by banceu_sergiu_ione on 2016-08-25
Since you have a new install, I would suggest a new install without LVM/crypt on disk ( cuz you have  it, right? ). Also have a checksum of iso file before doing it. See if goes.
Or you can try to open a [bug report]("https://wiki.ubuntu.com/Lubuntu/Bugs")
In case nobody else have an idea of how you could troubleshoot it.

---

### Post by steveminchington on 2016-08-26
> **banceu_sergiu_ione said:**
> Since you have a new install, I would suggest a new install without LVM/crypt on disk ( cuz you have  it, right? ). Also have a checksum of iso file before doing it. See if goes.
Or you can try to open a [bug report]("https://wiki.ubuntu.com/Lubuntu/Bugs")
In case nobody else have an idea of how you could troubleshoot it.

LVM yes but no encryption. That sounds like a good plan - I will do it over the weekend and report back. Thanks.

---

### Post by steveminchington on 2016-08-28
I have done a complete reinstall doing the following:

1 Ran checksum on the iso file which was OK
2 Used a brand new unused usb memory stick to make the boot drive (formatted fat32)
3 Deleted all partitions on the ssd and did the install using 'normal' partitioning scheme instead of LVM
4 Ran updates after install

This time the installer ran in OEM mode for some reason and I didn't have a choice to do it any other way, so after the install was complete I added myself as a user and deleted the oem user account. (the oem setup didn't work)

So, did it shut down this time... NO! It hasn't made any difference. I have tried all the same shutdown, poweroff and systemctl commands as before but none work. The only one that works is pm-hibernate which puts it to sleep and it boots back to where it was from there.
The only difference I see is there are no file system errors at shutdown, it reaches shutdown point but won't power off. Not a big deal at the end of the day, but I will raise it as a bug report.

Steve

---


---
title: "Slow Startup (3 Min.)"
date: 2007-11-23
forum: General Help
---

### Post by Detobu on 2007-11-23
I just freshly installed 7.10, but it takes like 3 minutes to boot up. The laptops isnt really that old, so I'm wondering if this is normal.

---

### Post by GavinZac on 2007-11-23
It isn't normal.

Can you post your specs?

---

### Post by Detobu on 2007-11-23
Here ya go.

AMD Mobile Sempron 2.0 GHz
512 Mb ram
60 GB hardrive
ATI Radeon Xpress 200M

---

### Post by LinuxGuy1234 on 2007-11-23
> **Detobu said:**
> I just freshly installed 7.10, but it takes like 3 minutes to boot up. The laptops isnt really that old, so I'm wondering if this is normal.

In your grub.conf remove:
splash from the kernel line like so after you are done:
kernel /boot/vmlinuz-2.6.22-14-generic ro quiet

(if so remove quiet at the end of every Ubuntu entry that boots Ubuntu)

---

### Post by Detobu on 2007-11-23
if a boot chart would help anyone diagnose my problem here it is.

[http://img249.imageshack.us/img249/3636/gutsy200711231ti7.png]("http://img249.imageshack.us/img249/3636/gutsy200711231ti7.png")

---

### Post by chrisccoulson on 2007-11-23
Can you post the output of
```
cat /etc/usplash.conf
```

And also tell us the resolution supported by your monitor

---

### Post by Detobu on 2007-11-23
> **chrisccoulson said:**
> Can you post the output of
```
cat /etc/usplash.conf
```

And also tell us the resolution supported by your monitor

the output is 
```
# Usplash configuration file
xres=1280
yres=1024
```

and the res of my monitor is 1280 x 800

---

### Post by chrisccoulson on 2007-11-23
Try editing the contents of /etc/usplash.conf so that it reads
```
# Usplash configuration file
xres=1280
yres=800
```

Then do

```
sudo update-usplash-theme usplash-theme-ubuntu
```

Let me know if you have any success. If it works, please open a bug report on Launchpad against usplash. You're not the first person to post here with long boot up times in Gutsy.

---

### Post by Detobu on 2007-11-23
> **chrisccoulson said:**
> Try editing the contents of /etc/usplash.conf so that it reads
```
# Usplash configuration file
xres=1280
yres=800
```

Then do

```
sudo update-usplash-theme usplash-theme-ubuntu
```

Let me know if you have any success. If it works, please open a bug report on Launchpad against usplash. You're not the first person to post here with long boot up times in Gutsy.

Thanks so much. Gusty now boots up in 25 secs rather than over 3 min!

---

### Post by chrisccoulson on 2007-11-24
No probs. FWIW, I think that your problem is related to [bug 150930]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930"), which is currently marked as In Progress

---

### Post by gambothell on 2008-04-04
I had the same problem on my HP (Compaq) nc6000. It took over 3 minutes to boot gusty. Now it boots normally. Thanks all for the great support.:)

---

### Post by Skyleth on 2008-04-05
Worked for me on my nc6000 as well!  Thanks.

---


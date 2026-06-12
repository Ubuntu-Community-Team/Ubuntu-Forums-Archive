---
title: "Problem ripping DVDs."
date: 2016-10-07
forum: General Help
---

### Post by Robert_Gaines on 2016-10-07
I've been ripping my DVDs to h264 files to build a private video library, but just recently I am only able to rip half the DVD. DVD rip gives me some error relating to disc corruption and HandBrake just finishes half way with no error. EVERY DVD I try is doing this. They play fine on stand alone players. I tried checking the DVD decoding libraries, but everything is find. This is driving me nuts. I was sailing smoothly, but now I can only rip half the disc. I don't think it is the drive because it is stopping on chapter boundaries. It's not perfectly half, but it is stopping part way along chapter boundaries. It doesn't matter if it is a store bought DVD or one I made on my stand alone DVD recorder. I'm using Ubuntu 16.04. VLC also just plays part way then stops. I think it is the DVD decoding libraries, but I don't know what to do about it.

---

### Post by DuckHook on 2016-10-07
It is also perfectly possible that it is your DVD drive. DVD lasers wear out with time and the older drives are especially prone to doing so. Your symptoms are typical of the burning laser dying after getting too hot halfway through a write. Reading lasers are usually fine because a different laser is used: one that is not as intense and runs at lower frequency. Do not rule out HW. In any case, the usual rule when trying to track down such issues is to look at your logs. The last few lines of dmesg or syslog just after a failed burn will usually tell you something.

---

### Post by DuckHook on 2016-10-07
My bad. I re-read your post and notice that the operation dies while ripping.

Please post results of:```
df -h
``````
cat /etc/fstab
``````
free -h
```

---

### Post by howefield on 2016-10-08
> **Robert_Gaines said:**
> DVD rip gives me some error relating to disc corruption and HandBrake just finishes half way with no error.

Can you supply the exact error message ?

---

### Post by colmax on 2016-10-08
Have you tried a different codec ie. mpeg4
Just to see if hardware is at fault
Cheers

---


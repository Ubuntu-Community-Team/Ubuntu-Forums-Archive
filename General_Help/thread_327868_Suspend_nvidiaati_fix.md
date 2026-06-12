---
title: "Suspend nvidia/ati fix"
date: 2006-12-29
forum: General Help
---

### Post by David Corrales on 2006-12-29
Hi everyone. I just found out that a *single* change in a text file has enabled both my PC's -a desktop with Nvidia and an Inspiron 9300 laptop with Ati- to successfully resume after suspending to ram, using binary/proprietary drivers.
Edit the file **/etc/default/acpi-support** and change the line:
```

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

```
to
```

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

```
reboot X (or the whole computer) and try suspend to ram.
Hope it helps you :cool:

---

### Post by Rizado on 2006-12-30
Doesn't work for me :neutral: Same old black screen. Are you sure you haven't changed anything else?

I have a 6600gt.

EDIT: Forgot to mention it but it might be very important. I have 9746 driver from nvidia.com

---

### Post by David Corrales on 2006-12-31
I added the **Option         "NvAGP" "1"** to my Device section.

---

### Post by vprasaj on 2008-06-11
David Corrales, THANK YOU, THANK YOU, THANK YOU, ...\\:D/[-o<

It finally works!!! :guitar::guitar:

It's ALIVE, it's ALIVE!!! :lolflag:

I couldn't suspend on my machine till today and I use linux on it for 3 years.

Thank you again...

---


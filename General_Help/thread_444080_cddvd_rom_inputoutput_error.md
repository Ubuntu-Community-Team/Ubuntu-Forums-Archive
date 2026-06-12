---
title: "cd/dvd rom input/output error"
date: 2007-05-15
forum: General Help
---

### Post by peter360 on 2007-05-15
After inserting a music CD into my cd/dvd rom I was able to play music from it using Sound Juicer.  However, when I tried

$  dd if=/dev/hdc

I got
dd: reading `/dev/hdc': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.016303 seconds, 0.0 kB/s

:( 

Here are some lines from dmesg in case it helps
[17179576.900000] Probing IDE interface ide1...
[17179577.636000] hdc: GCR-8483B, ATAPI CD/DVD-ROM drive

Can someone tell me what I did wrong?  I am runningUbuntu 4.1.1-13ubuntu5.  Thanks.

---

### Post by MoLE on 2007-05-22
I think you may have forgotten two things with the dd command.  Because dd expects unrestricted access to the raw device, you need to run it as root.  You also need to have an output for the command as well - eg: if you were wanting to write to a file, thus:
```

$  sudo dd if=/dev/hdc of=/home/user/discimage.iso

```

---


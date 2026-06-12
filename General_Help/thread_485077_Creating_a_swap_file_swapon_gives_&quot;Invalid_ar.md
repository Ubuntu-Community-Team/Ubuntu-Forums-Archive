---
title: "Creating a swap file: swapon gives &quot;Invalid argument&quot;"
date: 2007-06-26
forum: General Help
---

### Post by mvsjes2 on 2007-06-26
I have a diskless feisty system setup with nfs boot. I currently have no swap file, and have been working fine with 512meg ram. I would like to have a swap file created for safety, and when I see it's in use I'll add more ram. So even though it's over nfs (100gb connection) I don't mind if it doesn't perform well.

sh-3.2$ sudo dd if=/dev/zero of=/swapfile bs=1024 count=131072
131072+0 records in
131072+0 records out
134217728 bytes (134 MB) copied, 14.689 seconds, 9.1 MB/s

sh-3.2$ sudo chmod 0600 /swapfile

sh-3.2$ sudo mkswap /swapfile
Setting up swapspace version 1, size = 134213 kB
no label, UUID=65d3d58a-1f1c-477d-b5c2-bdffdc0175f9

sh-3.2$ sudo swapon /swapfile
swapon: /swapfile: Invalid argument

I can't figure out why I'm getting this last error. Anyone?

---

### Post by mbeierl on 2007-06-26
I just cut-n-pasted your output into a terminal here and did not get that error.  You've retried the command, yes?

---

### Post by mvsjes2 on 2007-06-26
Thanks for trying. Yes, I pasted what I had tried.

I wonder if Linux doesn't support a swapfile if it's on a filesystem mounted over an nfs connection?

---

### Post by mbeierl on 2007-06-26
DOH!  I didn't read that part.  No I don't think it can do swap over nfs.  That's probably just a bad idea all around.  nfs isn't always 100% reliable.

---

### Post by mvsjes2 on 2007-06-27
Understood, although if I loose nfs my root fs is gone too, making losing the swap drive a minor problem.

---


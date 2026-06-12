---
title: "Poor NFS Performance"
date: 2014-08-24
forum: General Help
---

### Post by AntiMattR on 2014-08-24
Hi all.

I just built a new NAS (Ubuntu Server 14.04) and I am trying to copy the stuff from my old NAS (Ubuntu Server 11.10) to the new one and the NFS performance is very disappointing.  The old NAS could always sustain a few hundred Mbit/sec over NFS to my client machines but as I am copying data to the new server I seem to be averaging only about 140Mbit/sec (17.5 MB/sec).  

The CPU cores on both boxes are largely idle and the gigabit link of course is only about 14% utilized.

Any ideas on what might be wrong and how I can speed this up?

Thanks!

---

### Post by SeijiSensei on 2014-08-24
Here's a couple of widely-used speedups for NFS:

Use async in the NFS options on the server.

Use "rsize=32768,wsize=32768" in the options on the client.

---

### Post by AntiMattR on 2014-08-24
Thanks.  Progress!  I am now up to 190 MBit/sec.

---

### Post by nerdtron on 2014-08-24
Are you transferring thousands of small files? I find them usually slow to transfer.

---

### Post by AntiMattR on 2014-08-24
A lot of the data I am copying right now is in Apple Sparse Bundle images.  A Mac sees them as a single file but they are stored on the filesystem as a folder that is composed of 8MB "bands".  That may be contributing to the slow transfer...

---

### Post by SeijiSensei on 2014-08-25
Can you create a compressed archive of those files and just ship that over the wire?

Since my earlier suggestions seemed to help, you can try bumping up the rsize and wsize parameters to 65536 and see if that helps.  I'm not sure what the maximum should be.  I just know that the default value of 8192 bytes was designed to work with the original 10 megabit Ethernet standard.  With current speeds at 100 or 1000 Mbit, you can use larger blocks; I just don't know how large.  On wired 100BaseT connections I've used 65536.

---

### Post by nerdtron on 2014-08-25
8MB files should be transferred fast enough. I'm pertaining to thousands of files with about ~10KB each. Compressing them to a single file and transferring is much much faster.

---


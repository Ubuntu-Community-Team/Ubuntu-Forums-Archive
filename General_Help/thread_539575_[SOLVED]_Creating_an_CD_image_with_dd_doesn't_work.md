---
title: "[SOLVED] Creating an CD image with dd doesn't work (Input/output error)"
date: 2007-08-31
forum: General Help
---

### Post by Ledah on 2007-08-31
Hi,
when I try to create an image file with dd like ```
dd if=/dev/hdc of=/home/X/image.iso
``` the CD drive starts reading, but a second later it stops and I get the message ```
dd: reading `/dev/hdc': Input/output error
32+0 records in
32+0 records out
16384 bytes (16 kB) copied, 4.59305 seconds, 3.6 kB/s

```
The last line varies at every try.

Also it doesn't work with sudo or another CD drive (hdd). I've got no idea, what's wrong.

---

### Post by HermanAB on 2007-08-31
Hmm, 'dd' is not good at handling errors.  There are other versions called 'ddrescue' and 'dd_rescue' respectively. You can try those and you can also try the good old kitty 'cat'.

Otherwise, use 'k3b'.  It is the best CD/DVD program for Linux and is sponsored by Mandriva Linux.

Cheers,

Herman

---

### Post by Ledah on 2007-08-31
There must be a bigger problem.
I tried all of them, but none could create a working image. dd_rescue was reading and reading and reading ...
ddrescue was getting slower and slower with reading the cd and k3b (which I already tried before) created a flawed image.

---

### Post by Ledah on 2007-09-01
*bump*

---

### Post by Ledah on 2007-09-03
*bump*

---

### Post by Ledah on 2007-09-05
*bump*

---

### Post by banewman on 2007-09-05
Have you considered that your cd player is dying? Not a solution I know but that is where I would be looking next. :)

---

### Post by Ledah on 2007-09-05
Sure, but then both, the DVD drive and the CD-RW drive would be broken. DVD's/CD's can be read, CD's can be burned. The only thing which doewsn't work is creating images.

---

### Post by banewman on 2007-09-08
As a check, open synaptic package manager and do a search for -    iso-9660
If this isn't installed that will be your problem. Package name is "genisoimage". :)

---

### Post by Ledah on 2007-09-08
The package is installed ;)
Well, I reinstalled my Kubuntu (some other problems, too) and updated to Gutsy (just for fun, I know the risk) and the problem is still there. 

The problem is really tricky and annoying.

---

### Post by Ledah on 2007-09-13
*bump* :)

---

### Post by Ledah on 2007-09-15
*bump*

---

### Post by Ledah on 2007-09-20
*bump*

---

### Post by maybeway36 on 2007-09-20
I think the CD might be scratched. It could also be a drive problem.
What CD is it you want to make an ISO of?

---

### Post by Ledah on 2007-09-20
The different CDs I tried aren't scratched. The drives are ok.
Well, I try to backup my PSX CDs (only the non copy protected). So I tried a data CD and that works. 

Weird. If there would be a copy protection, I would say that this is the problem, but there is none :-k

---

### Post by Ledah on 2007-09-21
[Solved!]("http://ubuntuforums.org/showthread.php?t=545546")

---


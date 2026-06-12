---
title: "Pentium 4 vs Celeron"
date: 2008-01-30
forum: General Help
---

### Post by vamp4life666 on 2008-01-30
I have a 2.0Ghz celeron (Dell box) that is doing an awful job as a rendering node in my render farm since I'm using 3ds max which is designed for the Pentium4.

I have a 1.6Ghz Pentium4 that I am using as a Samba file server running Gutsy 7.10 server edition.

I am thinking about switching the two so the P4 is rendering and the celeron is the file server. 

I'm petty sure the switch would be simple enough, but I am concerned that the celeron won't run the ubuntu 7.1 server very well.

Anybody run gutsy on a celeron and happy with its performance?

---

### Post by information_entropy on 2008-01-30
The primary limit on the speed of a file server is the speed of the hard drive and the speed of the network connection.  

I am currently running a P3 Tualatin based file server and it about the same speed as a P4 one.
I tested the difference transferring a bunch of big files and found little if any.


On the other hand,
If I recall correctly,

Your 2Ghz Celeron is most likely a Northwood-128  which uses a 1.52 V core.

The 1.6 Ghz P4 could be either a Willamette-256 which uses a 1.7 V core,
or a  Northwood-512 which uses a 1.52 V core

You need to verify that both of your motherboards understand the difference.
Some early P4 motherboards designed for the 1.7 V core do not support the 1.52 V core

This could result in catastrophic failure of CPU/Motherboard/Your digital life

---

### Post by articpenguin on 2008-01-30
early pentium 4s had problems as the netburst architecture was new. I had a p4 1.4GHz that had 256KB cache and my p3 933Mhz outperformed it. My p3 is the coppermine core.

---

### Post by vamp4life666 on 2008-01-31
To clarify I wasn not planning on switching the processors. I was planning on switching the drives. If nessary reinstaing the respective OS(s). My concern is that Gutsy will not run very well on the celeron processor, and I was hoping someone could confim or rebute my concerns.

MG

---

### Post by arsenic23 on 2008-01-31
You don't have anything to worry about.  You could do what your talking about with 1/2 the CPU power the processor has.

---


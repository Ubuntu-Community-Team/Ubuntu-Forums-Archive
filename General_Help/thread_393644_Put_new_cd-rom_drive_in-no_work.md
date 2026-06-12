---
title: "Put new cd-rom drive in-no work"
date: 2007-03-26
forum: General Help
---

### Post by DougieFresh4U on 2007-03-26
I changed cd drives, installed one that will write. I hear it working but nothing appears on screen. I plugged the plugs the same as they were in old one. So how do I make computer recognize? ):P

---

### Post by djrobthaman on 2007-03-26
You're probably going to have to manually edit your fstab file.  Or maybe there's an easy way to get it done.  But any time I've had problems mounting any sort of drive I've had to fix it that way.

---

### Post by dcstar on 2007-03-26
> **DougieFresh4U said:**
> I changed cd drives, installed one that will write. I hear it working but nothing appears on screen. I plugged the plugs the same as they were in old one. So how do I make computer recognize? ):P

Make sure the Master/Slave/Single drive jumpers on the new hardware are set the same as your existing hardware.

Also make sure your BIOS identifies the new drive correctly.

---

### Post by DougieFresh4U on 2007-03-27
When I open K3b it has the mane of drive identified- Plextor etc. etc., I really have no clue what to check next :confused:

---

### Post by DougieFresh4U on 2007-03-29
Got it o boot from cd and read cd's. But when I tried to erase cd using K3b,nada. I have posted screen shot of debugging report

---

### Post by taurus on 2007-03-29
I assume you are using CD-RW!  What is the error message from k3b when you try to erase a CD?

---

### Post by DougieFresh4U on 2007-03-29
> **taurus said:**
> I assume you are using CD-RW!  What is the error message from k3b when you try to erase a CD?

The cd says: Memorex CD-RW right on it!! What is that one line that says SCSI driver not there?

---

### Post by taurus on 2007-03-29
Memorex!  I had a lot of trouble with that brand so I dumped it and now only use Verbatim.

Are you trying to erase it so you can burn something to it?

---

### Post by DougieFresh4U on 2007-03-29
Check this out. Actually I'm trying it out so I can burn a new Xubuntu-Feisty disc for my sisters!!

---

### Post by taurus on 2007-03-29
See if you can burn the ISO file with k3b.

---


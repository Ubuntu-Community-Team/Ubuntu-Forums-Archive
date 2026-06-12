---
title: "Downgrading video card drivers"
date: 2013-01-10
forum: General Help
---

### Post by Zen_Clark on 2013-01-10
I recently upgraded to 12.10, and now the video card driver has been crashing when I try to start [_UFO:AI_]("http://ufoai.org/wiki/News"). The game worked perfectly fine before I upgraded, and several other people have reported the same problem after switching to the latest version of Ubuntu. Is there a way I can revert the video card driver I am using to the previous version I was using before I upgraded?

Broken drivers really make me regret switching to 12.10.

---

### Post by Mark Phelps on 2013-01-10
What's your make and model video card?  Need to know that before providing specific advice.

---

### Post by Zen_Clark on 2013-01-10
I have a Compaq Presario A940NR, with an Intel Graphics Media Accelerator X3100.

---

### Post by Mark Phelps on 2013-01-31
Unfortunately, Intel drivers, unlike AMD and Nvidia, are bundled with the kernel and are not made available in Additional Drivers.  Thus, it's not a simple matter of installing them from there.

You can try reading through the pages starting at the link below to see if Intel has any other drivers you can download:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng")

---

### Post by kurja on 2013-02-01
How about downgrading the kernel, then?

---

### Post by Mark Phelps on 2013-02-01
> **kurja said:**
> How about downgrading the kernel, then?

Not a good idea and fraught with problems.  But ... if you want to try this, then start a new thread with that as the title -- as folks familiar with how to do that will see that thread and respond.

---


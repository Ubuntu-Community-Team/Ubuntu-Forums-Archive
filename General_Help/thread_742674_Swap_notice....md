---
title: "Swap notice..."
date: 2008-04-01
forum: General Help
---

### Post by CM Xtasy on 2008-04-01
I have 2gb of RAM, and my swap file is 1024mb.  When I disable swap, I feel like the OS is running faster.  Does disabling swap really make it faster, or am I just imagining things?

---

### Post by NightwishFan on 2008-04-01
I would think it would not make it any faster. My swap is almost never used anyway.

---

### Post by ryanhaigh on 2008-04-01
You should check how much swap is being used when you are doing something 'intensive', I think you will find that it seldom uses much at all, there are ways to make the system prefer not to use swap (search the forum/google for swappieness) but it is always a good idea to have some available, I have only ever really touched swap once when editing a HUGE image in the Gimp (took about 10 minutes to save the picture and used 1.4GB of swap). After that my computer was VERY sluggish but a quick ```
sudo swapoff && sudo swapon /dev/sda2
``` fixed that up and I was back to full speed in no time.

---

### Post by CM Xtasy on 2008-04-01
> **ryanhaigh said:**
> You should check how much swap is being used when you are doing something 'intensive', I think you will find that it seldom uses much at all, there are ways to make the system prefer not to use swap (search the forum/google for swappieness) but it is always a good idea to have some available, I have only ever really touched swap once when editing a HUGE image in the Gimp (took about 10 minutes to save the picture and used 1.4GB of swap). After that my computer was VERY sluggish but a quick ```
sudo swapoff && sudo swapon /dev/sda2
``` fixed that up and I was back to full speed in no time.

It's when I'm not doing anything is when I notice the change!  Firefox starts up faster with swapoff, panels respond faster, and everything seems faster in general.  I'm sure I'm not using any swap because I have 2gb of RAM.  What size should my swap partition be if I have 2gb?

---

### Post by NightwishFan on 2008-04-02
Your size is ok I think, but if you use more than that of ram it could cause problems with suspending I think. I have a 1.8gb swap I think for 895mb of ram. My system is speedy because my hard drive is fast.

---


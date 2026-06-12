---
title: "Ubuntu displays my CPU wrongly!"
date: 2006-10-31
forum: General Help
---

### Post by gejr on 2006-10-31
Hey,

The default cpu frequency monitor (the one you can add to gnome-panels) switches between 600mhz and 1.7 ghz. I just realized that conky shows 600mghz too. Although I should have 1.7 ghz! Is it possible that Ubuntu hasn't configured my cpu correctly and is running at only 6000mhz? or is it just something wrong with the settings of these two apps? In that case..how to fix it?

Please help me..this is really bugging me!

-gejr

---

### Post by ltmon on 2006-10-31
Hi,

Ubuntu may be dynamically scaling your frequency in order to save power.  For example, mine scale between 996MHz and 1800Mhz... which is just fine because it's always running at it's fastest when I need it and it's saving power the rest of the time.

This should happen if you have a processor that supports frequency scaling.

What processor do you have?

---

### Post by gejr on 2006-10-31
you're probably right. Ive never heard of such behaviour from a processor:)

I'm embarrassed to say I'm not really sure what kind of processor this is. I am so new to linux, and I haven't had windows on this computer. It's a Fujitsu Siemens Amilo 1450 laptop, that's the only thing I know :)

Not sure how to check what kind of processor I have in this OS. I'm trying to debug all the fancy stuff in System -> Administration -> Device Manager, but I'm failing :)

---

### Post by tenjin on 2006-10-31
Hi,

I'm pretty sure you have a scaling processor, and so you would expect to see the processor set at the lowest speed for most of the time.

It only ramps up when you need it.

Cheers

D.

---

### Post by David Corrales on 2006-10-31
> **gejr said:**
> you're probably right. Ive never heard of such behaviour from a processor:)

I'm embarrassed to say I'm not really sure what kind of processor this is. I am so new to linux, and I haven't had windows on this computer. It's a Fujitsu Siemens Amilo 1450 laptop, that's the only thing I know :)

Not sure how to check what kind of processor I have in this OS. I'm trying to debug all the fancy stuff in System -> Administration -> Device Manager, but I'm failing :)

You can use the following command to learn some more info about your processor: **cat /proc/cpuinfo**

As a side note, I don't know why the heck isn't this info showed on the Device Manager application :rolleyes:

---


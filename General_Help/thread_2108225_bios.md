---
title: "bios"
date: 2013-01-24
forum: General Help
---

### Post by bodhi linux on 2013-01-24
I got old desktop pc.I canot boot from dvd drive even if i setup bios to do it.Evry time show me some MBA  boot manager,and after 30 sec massage is "network boot faild,press any key to reboot".I wont flash BIOS.How cant i make this.I have download BIOS,and i have 3.5 disket.Is this somekind of protection beacuse pc is from some company?

---

### Post by prodigy_ on 2013-01-24
Are you sure the DVD drive is OK?

---

### Post by SlugSlug on 2013-01-24
& are you sure you burnt the ISO correctly?

[http://www.ubuntu.com/download/help/burn-a-dvd-on-windows](http://www.ubuntu.com/download/help/burn-a-dvd-on-windows)

---

### Post by prodigy_ on 2013-01-24
Anyway if you have a USB thumb drive and really only need a quick workaround you could make a bootable USB stick: [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)

---

### Post by bodhi linux on 2013-01-24
I have 10 linux distros dvd's.Evrything works on other PC's.I know setup BIOS.I think the something is wrong with BIOS( or motherboard).PC is very old(12g) and come from some company.I think they have one Pc connect with ware to 10 pc's and every of them boot from major PC.If i disconnect wire - PC canot boot.This is my teory.When i put hard disc out,nothing changes.I found on net pictures how look MBA boot manager,but in my screen is missing options for boot,missing 50%.Beacuse that i think the smoething wrong with BIOS or the BIOS is modified.I have BIOS access,but does not want listen to me.

---

### Post by prodigy_ on 2013-01-24
> **bodhi linux said:**
> Evrything works on other PC's.
You mean you actually tested the DVD drive with some other PC and it worked?

---

### Post by coldraven on 2013-01-24
+1 for prodigy
Try cleaning the lens on the DVD drive.
Whatever you use, do it VERY gently. The lens is sprung mounted and very delicate.
I use a cotton bud and methylated spirit but a bit of spit might do the job.
Very gently stroke the lens a few times and try booting again.

---

### Post by bodhi linux on 2013-01-24
Problem solved !!!!!!!
With removing some card who look like card for conncect wire internet but got picture of phone with X(not for phone wire),boot from dvd working.I never see something lika that and beacuse i got wi fi and my a not pay attention on she.Thank you all !!!!!!

---

### Post by grahammechanical on 2013-01-24
> beacuse pc is from some company?

I think that this is correct. The machine may be set up to boot over a network. I used to work for a high street store and the tills were computers but they used something called PXE boot.

[http://en.wikipedia.org/wiki/Preboot_Execution_Environment]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment")

The base unit of these tills could be used as a base unit of a desktop computer but something would have to be changed to get the machine to look somewhere else for an OS other than the Network that it is not now attached to.

> "network boot faild,press any key to reboot".

I am glad that you made progress. Regards.

---


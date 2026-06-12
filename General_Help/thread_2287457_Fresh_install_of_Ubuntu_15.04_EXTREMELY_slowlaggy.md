---
title: "Fresh install of Ubuntu 15.04 EXTREMELY slow/laggy"
date: 2015-07-19
forum: General Help
---

### Post by humanoverdrive on 2015-07-19
I have a fresh install of Ubuntu 15.04 and the performance of the device is deplorable, and not for a lack of hardware specs.  I have experienced much better performance on older devices, and this is driving me nuts.  Windows are slow to respond, videos barely play (although the audio is fine), text I type often shows up only a few seconds after I type it.... it's almost unusable.  I have tried searching for an answer, and I haven't found anything that has worked.

Here is the hardware I'm working with: 
Processor: Intel Core i7-2640M CPU @ 2.80GHz
RAM: 16GB
Graphics card: AMD Radeon HD 6730M/6770M/7690M XT

Per other similar posts, I have also changed the graphics driver to fglrx-updates, one of the proprietary AMD drivers.  This has not helped at all.

Any assistance that could be provided would be greatly appreciated.  Please let me know if there is any other information I can provide that would help.

---

### Post by humanoverdrive on 2015-07-20
Bueller... Bueller...

Come on, over a day old and 178 views, and no one has any ideas??? I could really use some help.

---

### Post by Joe_Martin on 2015-07-21
Your specs can more than handle 15.04.  What about installing a lighter weight like ubuntu mate or xubuntu and then gauge response times.  I use ubuntu mate and it's the fastest, most responsive flavor I have used yet.

---

### Post by buzzingrobot on 2015-07-21
You've provided little data to go on. The issues you do mention are all video related. Are there other instances of sluggishness that are not video-related?

Incorrect/misconfigured drivers would be one thing to look at.  if you've used "Additional Drivers" be sure to reboot to enable the new driver. If the machine also has Intel video, reset your BIOS to use it, reboot and see if the sluggishness persists.  If it does, then it probably is not a video or a video driver issue.  If the sluggishness goes away, that points to the AMD configuration.

---

### Post by humanoverdrive on 2015-07-21
> **Joe_Martin said:**
> Your specs can more than handle 15.04.  What about installing a lighter weight like ubuntu mate or xubuntu and then gauge response times.

Well like you said, my system should be able to handle the full version of Ubuntu without any issue, so something must be going on, I'm thinking perhaps something to do with the graphics card. I'd prefer to use standard Ubuntu over a slimmed down version.

Any thoughts as to how I might be able to fix whatever is going on with my system so that it responds appropriately with a standard Ubuntu install?

---

### Post by Vladlenin5000 on 2015-07-21
> **humanoverdrive said:**
> Well like you said, my system should be able to handle the full version of Ubuntu without any issue, so something must be going on, I'm thinking perhaps something to do with the graphics card. I'd prefer to use standard Ubuntu over a slimmed down version.

Indeed, you should use the standard Ubuntu. It works beautifully on mine  with similar specs (except graphics, I've a better one by Nvidia).

>  Any thoughts as to how I might be able to fix whatever is going on with my system so that it responds appropriately with a standard Ubuntu install?

Considering you already tried with the proprietary drivers, I advise you to carefully read and understand what's implied in post #10.
Other possibility is the drive where you installed. A not-so-old HDD will always be sluggish, a typical 5400rpm 2.5" for notebooks/MiniPCs even worse. No i7 or any amount of RAM will change that.

---

### Post by howefield on 2015-07-21
Try running top which is installed in a standard default installation (or my preferred htop, which isn't) in a terminal to see if any rogue processes are running amok.

```
top
```

---

### Post by humanoverdrive on 2015-07-21
> **buzzingrobot said:**
> You've provided little data to go on. The issues you do mention are all video related. Are there other instances of sluggishness that are not video-related?

Programs sometimes stop responding and I get that dialogue asking me if I want to wait or if I want to force quit, but I guess that could possibly be video related too.  Other than that, the system seems pretty good except that that when I run VirtualBox with a Windows guest, that can be pretty sluggish too, but that’s also visualization, so somewhat to be expected.

> **buzzingrobot said:**
> Incorrect/misconfigured drivers would be one thing to look at.  if  you've used "Additional Drivers" be sure to reboot to enable the new  driver. If the machine also has Intel video, reset your BIOS to use it,  reboot and see if the sluggishness persists.

Like I said in my original post, I did indeed switch to the proprietary AMD video driver in Additional Drivers, and yes, I have rebooted since then.  As for the Intel video, I'm not sure if that is something I do have. How would I check? And how would I go about "resetting my BIOS" to use it?

Thanks for your insights!

---

### Post by humanoverdrive on 2015-07-21
> **Vladlenin5000 said:**
> Considering you already tried with the  proprietary drivers, I advise you to carefully read and understand  what's implied in post #10.

Which post? Your post was only #6, so there's no post #10 for me to reference! haha


> **Vladlenin5000 said:**
> Other possibility is the drive where you installed. A not-so-old HDD  will always be sluggish, a typical 5400rpm 2.5" for notebooks/MiniPCs  even worse. No i7 or any amount of RAM will change that.

Is there a terminal command or something else that you know if whereby I would be able to check/test the max RPM of my HDD?

---

### Post by humanoverdrive on 2015-07-21
> **howefield said:**
> Try running top which is installed in a standard default installation (or my preferred htop, which isn't) in a terminal to see if any rogue processes are running amok.

```
top
```

Nothing stands out as being a CPU hog, although I did run

```
sudo cpufreq-set -g performance
```

and that did seem to help things a bit.  It's still not that great, but it is slightly better.

---

### Post by buzzingrobot on 2015-07-21
> **humanoverdrive said:**
>   As for the Intel video, I'm not sure if that is something I do have. How would I check? And how would I go about "resetting my BIOS" to use it?



Intel CPU's have an onboard video capacity. It's enabled/disabled via the system's BIOS configuration menu. (Note that laptops sometimes don't allow this to be done manually but default to Intel video and then switch to the discrete AMD or Nvidia video card when demand requires. This is done to conserve battery life and prevent excess heat generation.)

---

### Post by Vladlenin5000 on 2015-07-21
> **humanoverdrive said:**
> Which post? Your post was only #6, so there's no post #10 for me to reference! haha

My mistake. I meant #4




Is there a terminal command or something else that you know if whereby I would be able to check/test the max RPM of my HDD?

No need... If you're using a HDD it will be sluggish no matter what, the bottleneck in otherwise high-end desktop or notebooks is quite noticeable.
However... Your case still feels more like video related. Please post at least your notebook brand/model.

---

### Post by amoun on 2015-07-21
Hi 

Were you using 14.04 LTS before and was that OK. I ask as I have an old ASUS 900 EEPC 900Mh celeron and no graphics to speak of.

I had been running Hardy 8.04 for 6 years and finally risked 14.04 and everything is fine.

---

### Post by howefield on 2015-07-22
> **humanoverdrive said:**
> Is there a terminal command or something else that you know if whereby I would be able to check/test the max RPM of my HDD?

You would probably be wasting your time worrying about the hard drive, with the rest of the hardware pretty decent, the hard drive is unlikely to be a fossil barely capable of turning and even if it was comparatively slow, it is unlikely to make the system as unusable as you describe.

You could look in the Disks utility for the device make/model, a quick internet search will likely give the drive specifications as one of the first links.

---

### Post by humanoverdrive on 2015-07-24
> **amoun said:**
> Were you using 14.04 LTS before and was that OK.This is a new to me machine.  I bought it second hand off work for a steal. Ran windows great, put Ubuntu 15.04 on here and it's preforming horribly.

---

### Post by Vladlenin5000 on 2015-07-24
> **humanoverdrive said:**
> This is a new to me machine.  I bought it second hand off work for a steal. Ran windows great, put Ubuntu 15.04 on here and it's preforming horribly.

Brand/model?
Laptop/desktop?

---

### Post by humanoverdrive on 2015-07-24
> **Vladlenin5000 said:**
> Brand/model?
Laptop/desktop?

Dell Precision M4600 laptop

---

### Post by Vladlenin5000 on 2015-07-24
Thank you.
Here are the detailed specifications according to the manufacturer: [http://i.dell.com/sites/doccontent/shared-content/data-sheets/en/Documents/precision-m4600-spec-sheet.pdf](http://i.dell.com/sites/doccontent/shared-content/data-sheets/en/Documents/precision-m4600-spec-sheet.pdf)

A few details stand out:
1. It was sold (in selected regions) with Ubuntu and RHEL besides Windows 7 so we know it's _100% supported_ and due to that fact alone, we also know it _should_ be working beautifully (given the _original_ specs);
2. You mentioned the graphics card as being "AMD Radeon HD 6730M/6770M/7690M XT" and yet the specs sheet says it's either a "AMD FirePro M5950 Mobility Pro with 1GB GDDR5 dedicated memory" or a couple of Nvidias... -> Are you absolutely sure about your hardware? I mean sure as in checked with Windows and that's what came up... Either way it's good news because...
3. No hybrid graphics (but either one of the three possible graphics cards _will_ require proprietary drivers).
4. In storage option we find that one of the options is a "7200rpm 320GB FIPS Certified _Self Encrypting_ Drive" and I'm really not sure if this has good support in Linux. All the other options should be fine but - again - any HDD will be a bottleneck for the system and the newer the OS is, the more noticeable that will be. If available consider replacing it with a SSD (or adding the optional SS Mini-Card).

Besides the aforementioned details nothing else stands out. Your machine should "fly" with Ubuntu so either something is wrong with it (faulty hardware, replaced/added mismatched hardware, ...) or something is wrong with your installation.

---


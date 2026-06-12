---
title: "Problem with Restricted Driver"
date: 2008-06-05
forum: General Help
---

### Post by tmapj on 2008-06-05
OK here's my problem. I have a restricted driver that is a graphics accelerator called "GeForce Go 7300." It works fine when I load generic Ubuntu kernel but not when I load the kernel that is optimized for my Processor. When I try to load it in ubuntu-rt (the ubuntu kernel optimized for my processor) it shows the loading screen but then loads to a blank screen with no sound whatsoever. Even if I press all the keys on the key board or press several at once with my hands on the keyboard it still makes no sound and nothing comes up on the screen.

Now you may be asking, "Why not just use generic ubuntu kernel?". Well the problem with generic ubuntu is that i have frequent crashes, freezes and errors.

If anyone knows anything about this problem please let me know. Your input will be much appreciated.

By the way my system is a laptop; its a Dell Inspiron E1505
Thanks.

---

### Post by forestpixie on 2008-06-05
Try ot install the driver - if for instance you used the hardware driver/restricted driver tool to install the nvidia gnereic driver - install the rt version with that kernel

For example I have
linux-restricted-modules-2.6.24-18-generic - installed with
linux-image-2.6.24-18-generic


If you have
linux-image-2.6.24-18-rt   - you need
linux-restricted-modules-2.6.24-18-rt

I would run the generic version and work out what you need to install then try to install them from the root prompt of recovery mode in the rt install.

Just so you know - I haven't actually done this, but it's probable what I would do in your situation.

---

### Post by kpkeerthi on 2008-06-05
Enable universe, multiverse and backports repositories from System -> Admin -> Software Sources and Install these two packages using synaptic. 

[B]linux-rt
linux-backports-modules-hardy-rt[/B]

These are the meta packages that guarantee you get the latest kernel from rt branch available in the repository, along with the required kernel modules and restricted modules.

---

### Post by tmapj on 2008-06-05
delete

---

### Post by tmapj on 2008-06-05
> **forestpixie said:**
> Try ot install the driver - if for instance you used the hardware driver/restricted driver tool to install the nvidia gnereic driver - install the rt version with that kernel

For example I have
linux-restricted-modules-2.6.24-18-generic - installed with
linux-image-2.6.24-18-generic


If you have
linux-image-2.6.24-18-rt   - you need
linux-restricted-modules-2.6.24-18-rt

I would run the generic version and work out what you need to install then try to install them from the root prompt of recovery mode in the rt install.

Just so you know - I haven't actually done this, but it's probable what I would do in your situation.

I'm sorry I'm not sure what it is you're asking me to do.

---

### Post by forestpixie on 2008-06-05
> **kpkeerthi said:**
> Enable universe, multiverse and backports repositories from System -> Admin -> Software Sources and Install these two packages using synaptic. 

[B]linux-rt
linux-backports-modules-hardy-rt[/B]

These are the meta packages that guarantee you get the latest kernel from rt branch available in the repository, along with the required kernel modules and restricted modules.

Make sure that you have the repos enabled in software sources and using synaptic search for the 2 packages and mark for install

---

### Post by tmapj on 2008-06-05
> **kpkeerthi said:**
> Enable universe, multiverse and backports repositories from System -> Admin -> Software Sources and Install these two packages using synaptic. 

[B]linux-rt
linux-backports-modules-hardy-rt[/B]

These are the meta packages that guarantee you get the latest kernel from rt branch available in the repository, along with the required kernel modules and restricted modules.

Now I have my display screwed up on both ubuntu-generic kernel and ubuntu rt kernel. Two screwed up displays in place of one perfect display and one non-existent display.

---

### Post by tmapj on 2008-06-05
OK now generic is working again, and so is ubuntu-rt. Now, however, ubuntu-rt doesnt have my graphics accelerator listed under Hardware Drivers. I know its not working because i tried playing some games that work under generic and they are extremely slow under rt.

---

### Post by forestpixie on 2008-06-05
Question first - have you ever had the rt kernel working with a nvidia driver.

Edit there did appear to be a bug with a slightly older -rt kernel with some nvidia cards - have a look

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130)

---

### Post by tmapj on 2008-06-05
> **forestpixie said:**
> Question first - have you ever had the rt kernel working with a nvidia driver.

Edit there did appear to be a bug with a slightly older -rt kernel with some nvidia cards - have a look

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197130)

For your first question: no, I'm new to Linux.

In reference to your link: thanks; they have fixes for many cards, but not mine.

---

### Post by forestpixie on 2008-06-06
Try using envy with the -rt then. you can install it from synaptic

---

### Post by tmapj on 2008-06-06
> **forestpixie said:**
> Try using envy with the -rt then. you can install it from synaptic

I'm sorry, what do you mean use envy with the rt?

---

### Post by forestpixie on 2008-06-06
Look in synaptic for envy - you need the gtk version for gnome. Install it - there will be a tool in system tools - you can use it to donload and install the driver for your card.

---

### Post by tmapj on 2008-06-06
> **forestpixie said:**
> Look in synaptic for envy - you need the gtk version for gnome. Install it - there will be a tool in system tools - you can use it to donload and install the driver for your card.

I did as you told me. It loaded in low resolution mode and the card still didn't show up under "Hardware Drivers".

---

### Post by forestpixie on 2008-06-06
You used envy and it didn't download and install the driver? If that is the case then I'm afraid I have no idea then.

---

### Post by tmapj on 2008-06-06
> **forestpixie said:**
> You used envy and it didn't download and install the driver? If that is the case then I'm afraid I have no idea then.

Well it tried to download and install the driver, but there was an error at the end.

---

### Post by forestpixie on 2008-06-06
It would be useful to know what the error was - run it again and try and copy the error and paste it here.

---

### Post by briandu on 2008-06-06
Will you please follow this exactly

[http://ubuntuforums.org/showthread.p...80#post5064980]("http://ubuntuforums.org/showthread.php?p=5064980#post5064980") msg #430

and prob should disappear

---

### Post by tmapj on 2008-06-06
> **briandu said:**
> Will you please follow this exactly

[http://ubuntuforums.org/showthread.p...80#post5064980]("http://ubuntuforums.org/showthread.php?p=5064980#post5064980") msg #430

and prob should disappear

Thanks. Where do I download the NVIDIA driver from?

---

### Post by tmapj on 2008-06-06
> **forestpixie said:**
> It would be useful to know what the error was - run it again and try and copy the error and paste it here.

UGH. It wont let me copy it.

---

### Post by forestpixie on 2008-06-06
> **tmapj said:**
> UGH. It wont let me copy it.

Follow briandu now - you can get the driver from the nvidia site - make sure you get a suitbale drive for your card - afaik there are only a few choices anyway.

If the file you download has a different name bear that in mind when running briandu's commands.

Good luck

---

### Post by tmapj on 2008-06-06
> **forestpixie said:**
> Follow briandu now - you can get the driver from the nvidia site - make sure you get a suitbale drive for your card - afaik there are only a few choices anyway.

If the file you download has a different name bear that in mind when running briandu's commands.

Good luck

A driver for my card isn't listed at the NVIDIA site. There are many similar cards. Should I download one of them?

---

### Post by forestpixie on 2008-06-07
The drivers are in series - 9 series etc - you need 7 series I believe

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by doorknob60 on 2008-06-07
Yeah, that would be 7 series. unfortunately, the driver download seems to be not workking *again*. I'll see if I can find it in a different section of the site (It worked last time). Here: [http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html) THat one works for me geforce 5200 :O and my Geforce go 6150, so it should have no problem with yours.

---

### Post by tmapj on 2008-06-11
> **doorknob60 said:**
> Yeah, that would be 7 series. unfortunately, the driver download seems to be not workking *again*. I'll see if I can find it in a different section of the site (It worked last time). Here: [http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html) THat one works for me geforce 5200 :O and my Geforce go 6150, so it should have no problem with yours.

Could you please help me with installing that driver? I don't quite understand what it is they want me to do.

---


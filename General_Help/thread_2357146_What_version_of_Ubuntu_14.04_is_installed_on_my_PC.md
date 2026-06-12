---
title: "What version of Ubuntu 14.04 is installed on my PC?"
date: 2017-03-30
forum: General Help
---

### Post by alexwaltz on 2017-03-30
Is there a settings panel that would tell me whether I have the 64-bit PC (AMD64) desktop image or the 32-bit PC (i386) desktop image version of Ubuntu 14.04 installed on my PC.

I would like to do a reinstall of the OS and I remember the last time I did this, I picked the wrong version to download.

My PC is listed as a Intel® Core™2 Quad CPU Q8300 @ 2.50GHz × 4 with a 64-bit OS type.

Thank you

---

### Post by howefield on 2017-03-30
Try Systems Settings > Details > Overview

or if you want the detail of the installation media used, try the terminal command..

```
cat /var/log/installer/media-info
```

---

### Post by alexwaltz on 2017-03-30
> **howefield said:**
> Try Systems Settings > Details > Overview

or if you want the detail of the installation media used, try the terminal command..

```
cat /var/log/installer/media-info
```

When I go into overview, it just shows Ubuntu 14.04 LTS along with the information that I listed above.

When I run the terminal command that you provided, I get the error cat: /var/log/installer/media-info: No such file or directory

Is there any other way to determine if I installed the AMD64 or i386 version?  I figured 50% chance of getting it right, so I downloaded the i386 version, but after 5 hours, it hasn't finished installing and I remember the last time, it only took about 20 minutes.

Thank you

---

### Post by cariboo on 2017-03-30
try:

```
uname -a
```

if your are using a 64bit install the result should look something like this:

```
uname -a
Linux alexis 4.10.0-15-generic #17-Ubuntu SMP Fri Mar 24 17:51:38 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mörgæs on 2017-03-30
Regardless of what you have now you should install a 64 bit version for this hardware.

---

### Post by howefield on 2017-03-31
To add to cariboos post, the -m flag can narrow the output down for you..

```
uname -m
```

Depending on your web browser, the "About" menu option may also tell you.. eg in Chromium > About

```
Version 56.0.2924.76 Built on Ubuntu , running on Ubuntu 17.04 (64-bit)
```

I'm sure Firefox used to report the architecture but it doesn't seem to now.

---

### Post by alexwaltz on 2017-04-03
> **howefield said:**
> To add to cariboos post, the -m flag can narrow the output down for you..

```
uname -m
```

Depending on your web browser, the "About" menu option may also tell you.. eg in Chromium > About

```
Version 56.0.2924.76 Built on Ubuntu , running on Ubuntu 17.04 (64-bit)
```

I'm sure Firefox used to report the architecture but it doesn't seem to now.

I'm really at a loss as to what I should be installing.  Below is the output of uname -a and uname -m.  Unless I mixed up my downloads, I believe I have tried both the AMD64 version and the i386 desktop version at the the URL [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/) .  The install takes a long time to finish, but at the end, when I try and install Chrome browser from the Google website, I get the error  Wrong Architecture AMD64.

Would someone be able to confirm which version of Ubuntu 14.04 I should install from the URL [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/) and I will be happy to try again tonight when I get home.

The output from the 2 uname commands are:

administrator@M900:~$ uname -a
Linux M900 4.4.0-71-generic #92~14.04.1-Ubuntu SMP Fri Mar 24 15:24:34 UTC 2017 i686 i686 i686 GNU/Linux
administrator@M900:~$ uname -m
i686
administrator@M900:~$

---

### Post by vasa1 on 2017-04-03
> **howefield said:**
> ...
I'm sure Firefox used to report the architecture but it doesn't seem to now.
With Firefox, about:support may show that:```
User Agent 	Mozilla/5.0 (X11; _Linux x86_64_; rv:52.0) Gecko/20100101 Firefox/52.0
```

---

### Post by howefield on 2017-04-03
> **alexwaltz said:**
> I'm really at a loss as to what I should be installing.

You are currently running a 32 bit operating system. That's the answer to your original question.

As to what you "should" install, that would depend on the hardware capabilities.

The following command should tell you whether or not the processor is 64 bit capable.

```
lscpu | grep "CPU op-mode(s)"
```

You can install 32 bit or 64 bit into a 64 bit capable machine but only 32 bit in a 32 bit capable machine.

---

### Post by alexwaltz on 2017-04-03
> **howefield said:**
> You are currently running a 32 bit operating system. That's the answer to your original question.

As to what you "should" install, that would depend on the hardware capabilities.

The following command should tell you whether or not the processor is 64 bit capable.

```
lscpu | grep "CPU op-mode(s)"
```

You can install 32 bit or 64 bit into a 64 bit capable machine but only 32 bit in a 32 bit capable machine.

Thank you, I think this should have been my original question.  Below is the output from the command that you provided.  Based on it, what version of Ubuntu 14.04 should I download from the URL [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/) , 64-bit PC (AMD64) desktop image or 32-bit PC (i386) desktop image

administrator@M900:~$ lscpu | grep "CPU op-mode(s)"
CPU op-mode(s):        32-bit, 64-bit

Thank you

---

### Post by howefield on 2017-04-03
> **alexwaltz said:**
> Based on it, what version of Ubuntu 14.04 should I download from the URL [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/) , 64-bit PC (AMD64) desktop image or 32-bit PC (i386) desktop image

Well, the processor would appear to be able to handle both 32 bit and 64 bit operating systems, but it would be good to know the rest of the machine specs, is this a ThinkCentre M9OO, do you have a link to the specifications ?

If not, you can get them by installing the inxi package and running

```
inxi -c 5 -b
```

I'd be a little worried by you comment about the install taking a long time to finish but my preference would always be to install 64 bit where possible with the proviso unless RAM is very limited.

---

### Post by alexwaltz on 2017-04-03
> **howefield said:**
> Well, the processor would appear to be able to handle both 32 bit and 64 bit operating systems, but it would be good to know the rest of the machine specs, is this a ThinkCentre M9OO, do you have a link to the specifications ?

If not, you can get them by installing the inxi package and running

```
inxi -c 5 -b
```

I'd be a little worried by you comment about the install taking a long time to finish but my preference would always be to install 64 bit where possible with the proviso unless RAM is very limited.

The PC is an M900 and its specs would be available here [http://shop.lenovo.com/us/en/desktops/thinkcentre/m-series-towers/m900/](http://shop.lenovo.com/us/en/desktops/thinkcentre/m-series-towers/m900/)

---

### Post by kansasnoob on 2017-04-03
> when I try and install Chrome browser from the Google website, I get the error Wrong Architecture AMD64.


Chrome browser is no longer available for i386 (32 bit) Linux operating systems.

---

### Post by howefield on 2017-04-04
> **alexwaltz said:**
> The PC is an M900 and its specs would be available here

Well, the specs on that page probably aren't exactly the specifications that you have in your machine as much of it is "up to" however, even with the lowest specs of that machine I'd expect 64 bit to run sweetly on it. I'd suggest creating a 64 bit live media and running it for an hour or two just to be happy, then install it.

---

### Post by alexwaltz on 2017-04-04
> **howefield said:**
> Well, the specs on that page probably aren't exactly the specifications that you have in your machine as much of it is "up to" however, even with the lowest specs of that machine I'd expect 64 bit to run sweetly on it. I'd suggest creating a 64 bit live media and running it for an hour or two just to be happy, then install it.

Everything installed perfectly today and the install took no more than 30 minutes.  What I noticed was that when I boot of the USB key, there are two options.  One is Legacy and one is UFI (or something like that).  I can't recall which option I selected as the fact that there are two options and which one I select causing the slowness didn't occur to me until after the install was completed.

But, in any case, it is AMD64 that I need to install on this PC and that allows me to install Google Chrome from the Google website.

Thank you for your help.

---

### Post by howefield on 2017-04-04
> **alexwaltz said:**
> Thank you for your help.

You're welcome, well done and glad you got it sussed. Feel free to mark the thread as solved.

---


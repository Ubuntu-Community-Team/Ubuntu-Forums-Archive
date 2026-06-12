---
title: "Two serious problems with ubuntu in Dell LATITUDE E5450"
date: 2015-03-21
forum: General Help
---

### Post by Ibrahim_Beliki on 2015-03-21
Hello,
For my new job, I've been given a brand new DELL LATITUDE E5450 laptop .
It included a Windows OS but I've uninstalled and installed Ubuntu instead.
Since then, I met two main problems:
1. When I press any key, I suddenly get it repeated non-stop until I press any key thet stop it from repeating.
For example: when I press "k" in the terminal, I get kkkkkkkkkkkkk........... until I press any key that stops it.
This occurs in random times, without any known trigger that causes it.
Re-installing ubuntu didn't solve the problem. (I also don't know whether it would've happened with the Windows OS because I didn't even use Windows, I installed Ubuntu from the first moment)

What are the possible reasons for that? The technician said I need to replace the motherboard with one another, but I'm not sure about that.

2. When I connect the computer with an external screen (Samsung screen in that case), using VDI, some characters from the screen "dissapear": in the terminal, in the header of each application, etc.
I attach 2 screenshots to show you what it's about. I have to say that in the 2 weeks before I re-installed ubuntu, I haven't had such a problem. It started to happen since I re-installed ubuntu. On the other hand, I'm not sure that re-installing ubuntu now is what I want to do.. 

Please help me, I can't work properly without a normal screen. 

Thanks in advance,

Regards,
Ibrahim.

---

### Post by PhilGil on 2015-03-21
I think these problems are unrelated. I believe the technician is right about the keyboard problem, it's likely a faulty keyboard or controller on the motherboard and you'll need to have the laptop repaired. 

What version of Ubuntu are you using? Your graphics problem is most likely caused by needing to update your graphics drivers (the video drivers included in Ubuntu releases aren't always compatible with the newest chipsets). This can be fixed, but it's important to find out what graphics hardware you have. Run the following command in the terminal and report back:

```
$ lspci | grep VGA
```

---

### Post by mörgæs on 2015-03-22
The first problem is easy to investigate. How does it work in a live boot of, say Ubuntu 15.04 beta?

---

### Post by Ibrahim_Beliki on 2015-04-04
> **PhilGil said:**
> I think these problems are unrelated. I believe the technician is right about the keyboard problem, it's likely a faulty keyboard or controller on the motherboard and you'll need to have the laptop repaired. 

What version of Ubuntu are you using? Your graphics problem is most likely caused by needing to update your graphics drivers (the video drivers included in Ubuntu releases aren't always compatible with the newest chipsets). This can be fixed, but it's important to find out what graphics hardware you have. Run the following command in the terminal and report back:

```
$ lspci | grep VGA
```

Hi Phil,
I use ubuntu 14.04.

the result of running that command is:
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)

---

### Post by pissedoffdude on 2015-04-04
Hey there,

First off, that is awesome that they let you choose your OS! 

Your keyboard issue is not due to a faulty motherboard (see [http://www.reddit.com/r/linux/comments/2sg27n/psa_do_not_buy_a_dell_latitude_e74xxe64xxe545xx/](http://www.reddit.com/r/linux/comments/2sg27n/psa_do_not_buy_a_dell_latitude_e74xxe64xxe545xx/))

You might be able to 'resolve' it by downgrading your bios, but I would consider doing more investigation since this is a work issued computer, or would you consider 14.04 if you really want to run Ubuntu?

See [http://www.ubuntu.com/certification/hardware/201409-15488/](http://www.ubuntu.com/certification/hardware/201409-15488/)

If you install 14.04, dell provides an official package for you: [http://www.dell.com/support/home/il/en/ildhs1/Drivers/DriversDetails?driverId=03CD1](http://www.dell.com/support/home/il/en/ildhs1/Drivers/DriversDetails?driverId=03CD1)

---

### Post by PhilGil on 2015-04-04
> **pissedoffdude said:**
> Your keyboard issue is not due to a faulty motherboard (see [http://www.reddit.com/r/linux/comments/2sg27n/psa_do_not_buy_a_dell_latitude_e74xxe64xxe545xx/](http://www.reddit.com/r/linux/comments/2sg27n/psa_do_not_buy_a_dell_latitude_e74xxe64xxe545xx/))
Good catch. I would have never expected it to be a software or firmware issue.

> **pissedoffdude said:**
> You might be able to 'resolve' it by downgrading your bios, but I would consider doing more investigation since this is a work issued computer, or would you consider 14.04 if you really want to run Ubuntu?The OP is running 14.04, so I think he's good there.

> **pissedoffdude said:**
> If you install 14.04, dell provides an official package for you: [http://www.dell.com/support/home/il/en/ildhs1/Drivers/DriversDetails?driverId=03CD1](http://www.dell.com/support/home/il/en/ildhs1/Drivers/DriversDetails?driverId=03CD1)The OP should definitely install this. Not sure it's going to fix the video issue, though.

Ibrahim, I would take mörgæs advice to test a live CD/USB of 15.04 and see if the video driver problem is corrected. If it is then you'll need to upgrade your kernel. Not sure of the process as I use older, recycled machines and haven't run into this problem yet.

---

### Post by Ibrahim_Beliki on 2015-04-06
> **PhilGil said:**
> Good catch. I would have never expected it to be a software or firmware issue.

The OP is running 14.04, so I think he's good there.

The OP should definitely install this. Not sure it's going to fix the video issue, though.

Ibrahim, I would take mörgæs advice to test a live CD/USB of 15.04 and see if the video driver problem is corrected. If it is then you'll need to upgrade your kernel. Not sure of the process as I use older, recycled machines and haven't run into this problem yet.


Hi,
I couldn't install the driver package of dell. I have a dell package driver which opens it and shows me a warning message(attached here).
when I try to install, it starts preparing for install but it gets stuck for hours.. it never installs the package.

i'm not sure to what version should I downgrade the BIOS and whether I want to take a risk and do that.. :/

---

### Post by pissedoffdude on 2015-04-07
Hmm, I'd say follow the instructions as they are posted on that dell website.  If that doesn't work, contact their support since they claim that driver is for 14.04

---

### Post by Ching-Yi on 2015-09-01
I'm using Ubuntu 14.04LTS and Dell E5450.
I have the same problem, but it occurs only when I re-open my screen and in the login page.

---

### Post by sandyd on 2015-09-01
Is this Intel HD 5500?
If so, see [here]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1432194") for bug, try enabling proposed in Ubuntu Software Sources and doing an upgrade.

Few other bugs for broadwell that I scrolled past while reading, some about graphics after suspend, so you may want to check on that as well after you have gotten the text to appear normally.

---

### Post by mörgæs on 2015-09-03
In case other people see the thread: If starting from scratch then installing 15.04 is probably an easier approach than trying to fix 14.04.

---


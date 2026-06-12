---
title: "AMD RX480 Hot!!"
date: 2019-02-04
forum: General Help
---

### Post by tlatch89 on 2019-02-04
When booting into Ubuntu and using no programs whatsoever my GPU temperature climbs up to 78-80C and hangs out there.

The fan stays around 750-850RPM regardless of temperature. In Windows the card idles at the same RPM but around 40C temp.

I'm not sure if the fan is kicking on/off causing it to stay around that temp. When watching HD videos on YouTube the temp stays the same.

Using the default Drivers because the AMD drivers blow up my entire installation, and still don't fix the idle temp issue.

[ATTACH=CONFIG]282402[/ATTACH]

I did find this: [https://github.com/marazmista/radeon-profile](https://github.com/marazmista/radeon-profile) - But am unsure how to actually install it

I read that AMD themselves are supposed to be updating drivers soon with a GUI, but like I said whenever I try to use their drivers my entire UBUNTU installation messes up.

Any help would be appreciated, this is the only issue I have. The room gets stuffy lol and the fan doesn't even ramp up.

---

### Post by oldrocker99 on 2019-02-04
The radeon open-source drivers are far superior to the fairly buggy, or disastrously buggy, AMD/ATI proprietary drivers, as you have found.  

With nVidia, it's the opposite; the Noveau open-source nVidia drivers work fine, but the proprietary nVidia drivers are pretty much required.

As far as the heat problem, I really don't know. That link points to source code, which is frankly beyond your ability to compile at present, no offense intended. All I can recommend is to blow dust out and check your airflow. 

Perhaps someone else can help with the heat problem, which is not present using Windows.

---

### Post by tlatch89 on 2019-02-04
Thanks for the reply!

I did notice in Windows the GPU fan spins a little over 1,000RPM at idle, then, of course, increases RPM greatly for gaming.

In Ubuntu the Fan just hovers around 800RPM regardless of temp. When I do a cold boot I can see the GPU temp climbing from 40C to 80C at idle.

It's almost like the fan isn't even spinning, then when it hits 80C, it turns on, and off, etc.

Thanks again for the response.

---

### Post by QIII on 2019-02-04
> **oldrocker99 said:**
> The radeon open-source drivers are far superior to the fairly buggy, or disastrously buggy, AMD/ATI proprietary drivers, as you have found.

I am not sure this is at all true.  AMD works closely with Canonical in the development of their *_open source_* AMDGPU driver, which is done on Ubuntu, just as they did with fglrx.  It may be true that driver support is a step behind the very newest hardware, but the AMDGPU driver is exceptionally good.

The Radeon driver is also very good, but it is engineered back into a black box.

The problem comes with older hardware that is not supported by the AMDGPU driver, for which Radeon is the only choice.

@tlatch89:  Which release of Ubuntu are you using and what kernel?  What do you mean by "messes up"?

---

### Post by tlatch89 on 2019-02-05
I was able to use this guide: [https://iandw.net/2014/10/12/fancontrol-under-ubuntu-14-04-resolving-usrsbinpwmconfig-there-are-no-pwm-capable-sensor-modules-installed/](https://iandw.net/2014/10/12/fancontrol-under-ubuntu-14-04-resolving-usrsbinpwmconfig-there-are-no-pwm-capable-sensor-modules-installed/)

With lm-sensors and FANCONTROL.

Had trouble getting pwmconfig to start but the above link shows you how.

Created a nice little fan curve and still using the default Ubuntu drivers. Hoping AMD comes out with their GUI and better drivers here soon..

Thanks!

---

### Post by QIII on 2019-02-05
Are you actually running 14.04?  If so, that is likely the source of your problems.  AMD already has "better drivers", but AMDGPU works only with 16.04 and higher.

In more recent releases the "default Ubuntu driver" is AMDGPU for supported hardware.  AMDGPU is open source.

Please note the date on your article.

---

### Post by tlatch89 on 2019-02-05
> **QIII said:**
> Are you actually running 14.04?  If so, that is likely the source of your problems.  AMD already has "better drivers", but AMDGPU works only with 16.04 and higher.

In more recent releases the "default Ubuntu driver" is AMDGPU for supported hardware.  AMDGPU is open source.

Please note the date on your article.

18.04. The article is old but it was able to fix the issues I was having with "pwmconfig".

I was able to get a fan curve using lm-sensors and fancontrol.

The default amdgpu as well as the proprietary AMD drivers did not change fan RPM from 800rpm (way too low for my small case) regardless of temp.

Also the proprietary AMD gpu drivers would break my entire ubuntu install when I tried to remove them and go back to open-source drivers.

Works great now though!

---

### Post by QIII on 2019-02-05
If you installed Ubuntu 18.04 with a supported GPU (yours should be) on board, then AMDGPU (open source) would have been installed as the default at OS installation.  That is how it works now.  AMDGPU is the default for supported GPUs, Radeon is installed only if the AMDGPU does not support your GPU -- and that happens primarily with older hardware prior to GCN 1.1.  If you removed it, I would expect that you would have had problems.

AMDGPU-PRO is the proprietary overlay to the AMDGPU driver.

I'm not sure what you were encountering.  You still haven't said what "messed up" is.  I use AMDGPU + PRO and things work fine.
What temperatures were you encountering?

---

### Post by tlatch89 on 2019-02-15
1. On the fresh Ubuntu installation my GPU fan would stay at a low RPM or **OFF** and heat up to 77C at idle doing nothing. (issue in OP)

2. I installed **lm-sensors **and **fancontrol **via the terminal and was able to create a custom fan curve for the GPU.
    - The fan keeps now keeps the GPU around ~40c at idle and ramps up RPM slowly when doing GPU-related heavy tasks.
    - It did not seem to use a fan curve with either the freshly updated Ubuntu installation nor with the proprietary AMD GPU drivers installed.
    - **It works great now and original problem is solved.**

To respond to your comment about the AMDGPU-PRO drivers working fine. Maybe so.. I may try reinstalling them when they do an update. It could just be something with my GPU, it is fairly new (2017 - RX 480 8GB).

The other issue I had when using proprietary AMD drivers was the boot up process changed a bit (brighter colors on Ubuntu boot screen), and I could hear the driver changing when starting Ubuntu.

Keeping in mind I do also boot Windows 10 on a separate main drive, and Windows has its own drivers. With the current working setup on default drivers and a couple edits it seems to boot cleaner and gets the job done for all I need it for.

---


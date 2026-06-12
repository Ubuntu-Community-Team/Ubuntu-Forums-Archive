---
title: "Stuck in login loop"
date: 2016-02-14
forum: General Help
---

### Post by blue_fox on 2016-02-14
Hi,

I use Ubuntu 15.10 on my HP laptop for some time now but a few days ago it got stuck in the login screen (lightdm) and every time I tried to log in it returned to the login screen. It seems I'm not the only one with this problem and there seem to be multiple causes and solutions.
[I]
I did ctrl + alt + F1 and logged in and tried to set gdm instead of lightdm as 'login screen' (sudo dpkg-reconfigure gdm). But things got worse: my PC boots, shows as usual (before showing the graphical login screen) shortly a terminal but then after a short black period a graphical login starts flashing at around 1-2fps. It's nearly impossible to log in as the text is shown for only a very short period (I think around 1/5s). Keypresses also aren't received during the blackout period.

So, in short, my PC is now an expensive flashlight :). A reinstall is always a solution of course, but I prefer not to reinstall and reconfigure the software and desktops I have. Regarding hardware, I'm sure 15.10 can run on my PC as on a second partition I have 15.10 installed, fully updated and upgraded. I installed this as a back-up OS and also use it to run kdenlive.

I have multiple desktops installed (KDE, LXDE, due-to-old-graphics-not-working Unity and some others). Changing the desktop choice didn't change antyhing to the login loop.

I hope someone can help me to solve this problem? Is it maybe possible to change the login back to lightdm without the OS booted (e.g. changing files)?[/I]

Update: I was able to reset the 'login screen' to lightdm by using the recovery mode. So this issue is solved, and I'll try to fix the login loop too.

---

### Post by jetimms on 2016-02-20
I'm experiencing the exact same issues, to the letter, except with Ubuntu 14.04 as of three or four days ago. As I haven't figured anything out, I have nothing to add to help, except that before getting to this problem was preceeded with not being able to see anything at all upon booting, requiring removing my nVidia GPU and attaching a VGA cable to my mobo.

---

### Post by jetimms on 2016-02-20
By the way, I did find the following. I did not help me, but it might solve your issue.

[http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

update:

[http://stackoverflow.com/questions/29041513/experiencing-infinite-login-loop-after-ubuntu-update](http://stackoverflow.com/questions/29041513/experiencing-infinite-login-loop-after-ubuntu-update)

This mentions checking ls -lah /var/crash from Alt+Ctrl+F1 (tty1), which led to me finding kernel crashes, among other things caused by trying to use gdm.

Which led to this:

[http://stackoverflow.com/questions/29041513/experiencing-infinite-login-loop-after-ubuntu-update](http://stackoverflow.com/questions/29041513/experiencing-infinite-login-loop-after-ubuntu-update)

... that says some have had success with downgrading (in recovery mode) to 3.13.0-74 since the bug may have been introduced in -75. I tried that, but it did not work.

update:
I tried apt-get update and apt-get upgrade, where it did do some work on my kernel, but it did not fix the issue. I still shows the login screen anew after logging into the GUI.

---

### Post by deadflowr on 2016-02-20
> **jetimms said:**
> 

... that says some have had success with downgrading (in recovery mode) to 3.13.0-74 since the bug may have been introduced in -75. I tried that, but it did not work.

Maybe try updating to the current kernel 3.13.0-77
> update:
I tried apt-get update and apt-get upgrade, where it did do some work on my kernel, but it did not fix the issue. I still shows the login screen anew after logging into the GUI.

apt-get upgrade will only update the existing kernel.
Rare that that would fix things like this.
You need to run dist-upgrade to install the latest kernel.

That aside,
It is unclear if either poster has either moved the .Xauthority file or changed the owner and group of said file.

As far as any lightdm problems, you can try logging in as a guest.
If the same thing happens in a guest session, then lightdm is bust.
If not, ignore lightdm as a source of the problem.

---

### Post by jetimms on 2016-02-21
Hey deadflower.

I forgot to mention that I'm on 3.13.0-77, currently. I tend to mindlessly run Ubuntu Upgrader, so I cannot say what I installed. Also, your hint about Guest giving the same result means lightdm is a good clue for myself that's what mine is doing. I can't speak for the OP. I did do a dpkg-reconfigure lightdm from tty1, but did not remove and reinstall. I guess there's no hurt in trying.

Thanks for the hints!

update:
I went to tty and did apt-get remove, apt-get purge, apt-get lightdm and dpkg-reconfigure lightdm, but Guest is still looping.

---

### Post by jetimms on 2016-02-23
tldr; Fixed by getting latest Nvidia Geforce GPU driver.

I'm running a Nvidia GTX 960 so I downloaded it to a USB stick from my windows box:
[http://www.geforce.com/drivers/results/98373#](http://www.geforce.com/drivers/results/98373#)

After installing that driver, I'm back up and running.

Since you're on a laptop, that is probably no help at all to you unless you have an Nvida GPU on it, OP. Sorry about that, but maybe it will help someone else.

Better yet, I hope you have it fixed already!

---

### Post by blue_fox on 2016-02-25
Thank you for all the helpful answers!

The problem seemed to be related to either a boot problem or not enough space on my hard disk.
I used boot-repair, booted from my other partition and also made some space on the home and system partitions.
After fixing some weird internet connection problems it's running again!

So it wasn't a graphics problem (I use however a very old Geforce Go 7400 Nvidia GPU).

---

### Post by jetimms on 2016-02-29
From the looks of it, there's not just one cause to this bug.

Glad to hear you got it working!

---


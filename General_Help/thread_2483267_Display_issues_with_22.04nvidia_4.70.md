---
title: "Display issues with 22.04/nvidia 4.70"
date: 2023-01-24
forum: General Help
---

### Post by m-knichel on 2023-01-24
I have been running 20.04 since it came out.  Last week I installed 22.04 onto a different partition.  All was going fine for a while.  THen my display started going off and I am not able to wake it up. I have to press/hold the power button.  This has caused my profile in xfce to get corrupt on top of still happening.
I tried to load the previous version 20.04 from grub, but when I get the login screen and enter u/p it just circles back to the login screen.  I suspect it is due to preferences in my account that are now set for 22.04.
I want to reset my user account so I can continue using 20.04 as it didn't have this display issue.
How to I go about getting my account reset so I can use 20.04?

---

### Post by #&amp;thj^% on 2023-01-24
Have you tried selecting 20.04 from A Bios boot menu. Like <F+12 or enter> at first start.
```
efibootmgr
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0003,0001,0000,2001,2002,2003
Boot0000* openSUSE
Boot0001* opensuse-secureboot
Boot0003* arch
Boot0004* kaisen
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network

```

---

### Post by m-knichel on 2023-01-24
No, both version on same sdd.

---

### Post by #&amp;thj^% on 2023-01-24
Ok when 20.04 circles back to the login screen Press <F2> login through tty or the terminal prompt.
Now remove the nvidia driver.
When you say you suspect it is due to preferences in your account,>> several hard shutdowns are most likely for what your going through.

---

### Post by m-knichel on 2023-01-24
So do I reinstall it after (if I can even login)?

---

### Post by #&amp;thj^% on 2023-01-24
Just depends, have you tried yet?
firsts thing first :)

---

### Post by m-knichel on 2023-01-24
I just tried and still stuck in login loop.
I did ctrl+alt+F2 and logged in
sudo apt remove nvidia-driver-470
reboot
no joy.

---

### Post by #&amp;thj^% on 2023-01-24
Sorry to hear that, I assume you have back-ups for a reinstall right?
We could keep diving down the rabbit hole, and may get lucky.
Best bet and suggestion now is a re-install.....

---

### Post by MAFoElffen on 2023-01-24
After doing 
```

sudo apt remove --purge nvidia

```
Then on first boot after, use the nomodeset boot option at editing the grub boot screen, as a kernel boot parameter. Then on bot, install your NVidia drivers... Unfortunately, myself owning and running NVidia on my hardware, these kinds of things have become second nature. LOL 

You didn't mention which NVidia GPU you are running(?)
```

sudo lspci | grep -i 'vga'

```

---

### Post by m-knichel on 2023-01-24
GPU is :
01:00.0 VGA compatible controller: NVIDIA Corporation GP106BM [GeForce GTX 1060 Mobile 6GB] (rev a1)

When I tried to purge nvidia, got "package nvidia is not installed"
tab line completion shows:
nvidia-dkms-470
nvidia-kernel-common-470
nvidia-utils-470
nvidia-settings
nvidia-compute-utils-470

So, to clarify, I was not having this problem before installing 22.04.
I was booting 20.04 just fine, never lost display.
I installed 22.04 to second partition.  Started having display issues (screens went black had to force shutdown).
Tried loading 20.04 again and have login loop only when trying 20.04.

UPDATE:
I decided to try the Advanced settings for ubuntu from grub and see that there are 2 kernels 5.15.0-57 & 58.  So I tried to boot 57.  My second monitor isn't detected when using 57 but it is when using 58.  Not sure what that means if anything.

---

### Post by monkeybrain20122 on 2023-01-24
22.04 on Wayland?

---

### Post by m-knichel on 2023-01-25
I am fairly certain as I don't recall changing and Wayland is default in 22.04.  22.04 is where my display goes out and I have to force a restart pressing & holding power button.  20.04 is is where I am stuck in a login loop.
I will verify when I get home from work tonight.

---

### Post by Holger_Gehrke on 2023-01-25
The title says '[xubuntu]'. XUbuntu uses XFCE. XFCE doesn't yet support Wayland -> m-knichel can't be using Wayland unless the title is wrong ...

Holger

---

### Post by #&amp;thj^% on 2023-01-25
> **Holger_Gehrke said:**
> The title says '[xubuntu]'. XUbuntu uses XFCE. XFCE doesn't yet support Wayland -> m-knichel can't be using Wayland unless the title is wrong ...

Holger

+1 My thought's exactly!
@ m-knichel I guess you decided to dive down the rabbit hole after all. :(
With a new install you would now be productive. (Nothing wrong with learning though)

---

### Post by m-knichel on 2023-01-25
I am indeed using XFCE, so I gess it is time to boot to USB.. :(

---

### Post by #&amp;thj^% on 2023-01-25
If I may add my 2 cents worth, if your going to duel boot on the same drive, disable or un-install os-prober, and have each install use the installed grub for that install only.
Or use a VM to use a second OS with it.
BTW If you stay with 20.4 you'll use a bit more stable DE XFCE 4.16 with 22.04 It will get bumped to XFCE 4.18 just freshly release.
```
xfce4-session:
  Installed: 4.18.0-1
  Candidate: 4.18.0-1
  Version table:
 *** 4.18.0-1 500
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status
     4.16.0-1 500
        500 http://deb.debian.org/debian bullseye/main amd64 Packages

```

---

### Post by m-knichel on 2023-01-30
UPDATE:
I have re-installed 22.04 formatting the existing / partition.  Still have 20.04 on other part. It has been running for a few days just fine.  Not much use each day, but still...
Today I was on it for 3 hours.  I still experience a random display crash where my screens go black and ALL I can do is force a restart (power button).
Tonight it happend while I was in an Online meeting teaching  a class.  Funny thing was when my screen went black, I could still talk with the participance for a minute then lost everything (audio & video).  I rebooted and rejoined for the second half of class and was fine.
Would sill like to figure this out.  Wonder If I should reinstall 20.04 instead...

---

### Post by #&amp;thj^% on 2023-01-31
If I was having this problem on 22.04 and not on 20.04, I know what my choice would be.
Stable Rules, random crash's suck.

---

### Post by m-knichel on 2023-02-05
I reinstalled 20.04 and after a day or 2, same problem showed up.  I guess it was coincidence... Time for new laptop.

---


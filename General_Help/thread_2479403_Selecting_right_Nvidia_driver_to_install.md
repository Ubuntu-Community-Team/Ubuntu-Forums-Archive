---
title: "Selecting right Nvidia driver to install"
date: 2022-09-23
forum: General Help
---

### Post by sniper8752 on 2022-09-23
I am trying to monitor my Nvidia card temp.  I am following a tutorial that says I need to switch to the proprietary driver version.  Which one do I select, and why are there so many for my card? 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291067&stc=1[/IMG]

---

### Post by scriber on 2022-09-23
Pick the first one 5.15
Why are there so many different drivers ? well some people need them I guess but choose the 5.15 one and you should be fine.

---

### Post by SeijiSensei on 2022-09-23
People with older hardware need older drivers.

---

### Post by aug7744 on 2022-09-24
[https://www.nvidia.com/en-us/geforce/drivers](https://www.nvidia.com/en-us/geforce/drivers)

After disable nouveau driver

Run the commands below

sudo apt install pkg-config
sudo apt install build-essential
sudo apt install libglvnd-dev
sudo apt install libglvnd-dev:i386
sudo apt install dkms

After run the command in directory with the Nvidia binary driver.
sudo sh ./*.run --no-backup --no-nouveau-check --disable-nouveau --install-libglvnd --no-peermem

---

### Post by TheFu on 2022-09-24
Without knowing the exact nvidia card, we cannot say which driver you should choose.  Latest only works for the latest versions.  I have a few 3+ yr old nvidia GPUs. They use different drivers and never the latest anymore.

---

### Post by oldfred on 2022-09-24
Best not to download from nVidia directly. You have to reinstall with every kernel update. The Ubuntu version is automatically updated.

You can use the nVidia site to check which driver is current for your system.
Often nVidia releases newer driver that has newer features for new cards, but may work on older card. It just will not add much if anything as new hardware features are not in older card.

Best to install from Ubuntu.
If you already have a nVidia driver you must purge it first or you get conflicts.
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

Usually one driver or the other is recommended.

---

### Post by Yellow Pasque on 2022-09-24
> why are there so many for my card? 
Your card is supported by a few generations of nvidia drivers, and some people prefer older drivers if they run into older problems, so Ubuntu keeps them available. They also have server versions of the drivers that depend on other packages if you're running a server. I agree that it's somewhat confusing. In practical terms, most desktop users would just want the latest nvidia proprietary driver that's officially supported, but Ubuntu is becoming more focused on server deployments nowadays.

The fact that this is a mobile chips suggests you have a hybrid graphics setup (Intel/Nvidia). So beware, that you may have to use commands like 'prime-select' to control which GPU you want to use.

> **TheFu said:**
> Without knowing the exact nvidia card, we cannot say which driver you should choose.

It's right there in the screenshot: GeForce GTX 960M (GM107M chip).

---

### Post by TheFu on 2022-09-24
> **Yellow Pasque said:**
> It's right there in the screenshot: GeForce GTX 960M (GM107M chip).

Missed that - I seldom look at screenshots - bad eyesight.  Looks like the first option as  scriber suggested is "tested" and the latest. Good advice.

[https://www.nvidia.com/Download/driverResults.aspx/193095/en-us/](https://www.nvidia.com/Download/driverResults.aspx/193095/en-us/) says to use 515.76 

For 16.04-20.04, we used to be able to just run
```
$ sudo ubuntu-drivers autoinstall
```

But sometime later, Canonical decided to deprecate the autoinstall option for some reason. Think that was in the 22.04 release notes, but I don't really remember.

Did I miss the kernel and release too? The driver version and kernel are connected.  For example, my GT 1030 is using the 470 driver because 5.4.x kernels aren't supported with the newer drivers.

---

### Post by sniper8752 on 2022-09-26
uname -r returns the following: 5.4.0-126-generic

---

### Post by sniper8752 on 2022-09-26
> **oldfred said:**
> Best not to download from nVidia directly. You have to reinstall with every kernel update. The Ubuntu version is automatically updated.

You can use the nVidia site to check which driver is current for your system.
Often nVidia releases newer driver that has newer features for new cards, but may work on older card. It just will not add much if anything as new hardware features are not in older card.

Best to install from Ubuntu.
If you already have a nVidia driver you must purge it first or you get conflicts.
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

Usually one driver or the other is recommended.

This worked perfect, thank you!

---

### Post by TheFu on 2022-09-26
> **sniper8752 said:**
> This worked perfect, thank you!

a) please mark the thread as solved to help the community. "Thread Tools" link/button near the top of the page.
b) Seems all the posts after the 1st reply weren't really needed. Bet if you check the installed driver, it is that same version. 515.xx.

---

### Post by Yellow Pasque on 2022-09-26
> **TheFu said:**
> b) Seems all the posts after the 1st reply weren't really needed.

There's nothing wrong with clarification.

---


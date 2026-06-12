---
title: "How do I remove manually installed Nvidia driver to upgrade 10.04 LTS to 12.04 LTS"
date: 2012-10-24
forum: General Help
---

### Post by Cavsfan on 2012-10-24
I am wanting to upgrade my Lucid LTS install to Precise LTS and I have to remove the manually installed Nvidia driver 304.60 to do so.

I have installed many drivers with these instructions with great success: 
[[COLOR=blue]_http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

I just need to know how to remove it and install the nouveau driver before I upgrade.
For starters I am guessing that after I get rid of the driver I unblacklist the stuff that the page above says to.

I also installed a script that installs the driver into a kernel when one is installed via these instructions:
[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

I know I just delete the script the driver and all that was created from that last page.

Any knowledgeable help is greatly appreciated. :)

---

### Post by dino99 on 2012-10-24
do you know that ubuntu is made for humans ? :P

you dont need to tweak/blacklist or else, the wise system make it for you without you need to know about it; thats magic dont you ?

simply purge nvidia, then install nouveau, thats it  :P

---

### Post by Cavsfan on 2012-10-24
> **Cavsfan said:**
> Any **_*knowledgeable help*_** is greatly appreciated. :)

> **dino99 said:**
> do you know that ubuntu is made for humans ? :P

you dont need to tweak/blacklist or else, the wise system make it for you without you need to know about it; thats magic dont you ?

simply purge nvidia, then install nouveau, thats it  :P

How do I simply purge nvidia? It was manually installed... 
Nothing starting with "nvidia" shows in SPM and the driver is built into the kernel. :roll:

---

### Post by bogan on 2012-10-24
Hi!, **Cavsfan,**

I do not see why you want to purge 304.60 in order to upgrade to Precise.

304.48 and later are DKMS compliant so no longer is it necessary to re-install the nvidia driver after an update or upgrade [ provided DKMS is installed].

I have just the other day updated from 12.04.1 to 12.10 with nvidia 304.51 installed, and it went straight forwardly without any need to alter anything after re-booting.

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-10-24
> **bogan said:**
> Hi!, **Cavsfan,**

I do not see why you want to purge 304.60 in order to upgrade to Precise.

304.48 and later are DKMS compliant so no longer is it necessary to re-install the nvidia driver after an update or upgrade [ provided DKMS is installed].

I have just the other day updated from 12.04.1 to 12.10 with nvidia 304.51 installed, and it went straight forwardly without any need to alter anything after re-booting.

Chao!, **bogan.**

Hi **bogan**!

I have read that before doing an upgrade you should remove any manually installed video driver and install the nouveau driver.

If you look in that first link I posted I purged everything nvidia* off of my system.
Downloaded the driver from Nvidia and booted into recovery mode in a root shell.
I entered **telinint 3** to stop the x server (this is what the driver installation said I had to do).
Then got into the Downloads directory and entered **sudo sh nvidia_driver_name** and it installed.
This worked excellent in Lucid and I used it at least a dozen times.
I would just like to know how to get rid of the driver as it is built into the kernel with the script in the 2nd link in my first post.
Then install the nouveau driver.
I am being patient with this as it is my main install and I don't want to take any chances of looking at a black screen.
However, I have other systems on here and could re-install the driver but, I want to upgrade 10.04 to 12.04 via CLI **sudo do-release-upgrade**.

It is already set to only do LTS upgrades and since 12.04.1 came out it shows in update manager.
Thanks! :D

---

### Post by Cavsfan on 2012-10-24
I believe I found it. I maneuvered to where my driver is /etc/src/ and in terminal entered:
**sudo sh NVIDIA-Linux-x86_64-304.60.run --uninstall **

It worked. Now before I reboot I just have to install the other driver.
I am doing this on a separate Lucid install.
I'll post back when I am done.

Through all the searching, all I have found is a clean install fixing the issue of uninstalling the manually installed Nvidia driver.

That is not what I want. Hopefully this is the solution.

I got the other Nvidia driver uninstalled and installed nvidia-common to be able to install version 173.14.22 and I am back up.
Almost there, Tomorrow I'll figure out how to install the nouveau driver. :D

---

### Post by Cavsfan on 2012-10-25
I also had to remove the newest kernel:
```
sudo apt-get purge linux-headers-2.6.32-44 linux-headers-2.6.32-44-generic linux-image-2.6.32-44-generic
```Then re-install that and everything else it took with it:
```
sudo apt-get install linux-headers-2.6.32-44 linux-headers-2.6.32-44-generic linux-image-2.6.32-44-generic linux-headers-generic linux-image-generic nvidia-common
```Then it booted fine. 
Slowly but surely this will work. :D

---

### Post by bogan on 2012-10-25
Hi!, **Cavsfan**,

If you are reverting to nouveau I suggest that in addition to deleting any blacklists you entered in /etc/modprobe.d/blacklists.conf, you also check out all the other files in the folder.

I found I had three files I did not realise were there, all blacklisting nouveau, they were installed by nvidia-installer, nvidia-current and nvidia-current-updates [x-swat].

All had names begining with "nvidia" so maybe they were removed if you purged nvidia* and not nvidia-*, or by nvidiaxxx.run --uninstall, -perhaps not, they wern't in my case.

Chao!,** bogan.**

---

### Post by Cavsfan on 2012-10-25
> **bogan said:**
> Hi!, **Cavsfan**,

If you are reverting to nouveau I suggest that in addition to deleting any blacklists you entered in /etc/modprobe.d/blacklists.conf, you also check out all the other files in the folder.

I found I had three files I did not realise were there, all blacklisting nouveau, they were installed by nvidia-installer, nvidia-current and nvidia-current-updates [x-swat].

All had names begining with "nvidia" so maybe they were removed if you purged nvidia* and not nvidia-*, or by nvidiaxxx.run --uninstall, -perhaps not, they wern't in my case.

Chao!,** bogan.**

Thanks for the advice **bogan**! I forgot to unblacklist them. I'll do that now.
Thanks again! :)

Here is what I had blacklisted:
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

---

### Post by Cavsfan on 2012-10-25
Found this will work to install the nouveau driver:

2) Open the terminal and type the following commands:
```
sudo update-alternatives --config gl_conf
```(and select the alternative provided by [COLOR=Red]mesa[/COLOR])

```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old

```and restart your computer.

I believe that does it. I am going to try an upgrade on this 2nd Lucid install before I attempt it on the good one. :D
I'm not if a big hurry but, if this works I will resolve this thread and use it on my main Lucid install.

---

### Post by Cavsfan on 2012-10-27
I should have listened to you **bogan**! The above didn't work and left me with a black screen.
I had to go into safe mode and download the Nvidia driver 304.43 and install it.
Then I went in to Synaptic and installed **nvidia-current-updates** and **nvidia-settings-updates** which were 304.43 and rebooted.

Then when I upgraded from Lucid to Precise, everything went smooth as silk. :D

I just wanted to test that out as I have always done clean installs after backing everything up.
But, I have been told upgrades from LTS versions work well and this one sure did. :D

Now I am ready to do the real upgrade but, I have until April 2013 to do it.

Thanks for the help!

---


---
title: "Random freezes in Ubuntu 13.10 using Ubuntu (default) desktop"
date: 2013-10-24
forum: General Help
---

### Post by yhereincv on 2013-10-24
Hello, my system randomly freezes when I login with the Ubuntu (default) desktop but does not when I use the Gnome flashback (no effects) desktop. I haven't login using the regular Gnome flashback desktop.
The freezes happen doing simple things.
It did also happen with Ubuntu 13.04
I have an Nvidia GeForce GT 240 (GT 215) video card
I did a system test and what got tested passed
Memory 7.8 GiB
Processor Intel Pentium(R) D CPU 3.20GHz x 2
Graphics Gallium 0.4 on NVA3
OS type 64-bit
Disk 23.6 GB

I gotta say it is very frustrating and almost to the point of not using Linux for a few months

Hope you can provide some good guidelines and I thank you beforehand for your help

---

### Post by fantab on 2013-10-24
If you have installed any proprietory drivers (with Additional Drivers), uninstall them and see how 13.10 behaves.

Check the logs and report back if you see any Errors (EE) and Warnings (WW)
you can find logs in /var/log

Also post the output of the following command:
```
dmesg
```
If the output is very long then post it [**HERE**]("http://paste.ubuntu.com/") and paste here just the link from the address bar.

---

### Post by VMC on 2013-10-24
> **yhereincv said:**
> Hello, my system randomly freezes when I login with the Ubuntu (default) desktop but does not when I use the Gnome flashback (no effects) desktop. I haven't login using the regular Gnome flashback desktop.
The freezes happen doing simple things.
It did also happen with Ubuntu 13.04
I have an **Nvidia GeForce GT 240 (GT 215) video card**
I did a system test and what got tested passed
Memory 7.8 GiB
Processor Intel Pentium(R) D CPU 3.20GHz x 2
Graphics Gallium 0.4 on NVA3
OS type 64-bit
Disk 23.6 GB

I have a _**[bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1242767")**_ on this issue. Go there and click "me too" to confirm, so the developers will take a closer look.
They acknowledge its a *nouveau* issue, but it needs to be fixed. Installing nvidia drivers doesn't solve the *nouveau* issue.

---

### Post by yhereincv on 2013-10-24
Here is some info for "fantab" suggestions:

The dmesg output when logged in with the Ubuntu (default) desktop is at:  [http://paste.ubuntu.com/6298409/](http://paste.ubuntu.com/6298409/)
The dmesg output when looged in with Gnmove fallback (no effectos) desktop is at: [http://paste.ubuntu.com/6298423/](http://paste.ubuntu.com/6298423/)

No error or warning messages found in /var/log

My Ubuntu 3.10 was reinstalled 2 days ago from a DVD and it was an out-of-the-box installation. If any proprietary drivers were installed, they were installed automatically.

Hopefully this can help fix this problem.
Thanks

---

### Post by yhereincv on 2013-10-24
I reposted in "bugs" as suggested by "VMC"
Thanks

---

### Post by VMC on 2013-10-24
yhereincv, you need to click "[this bug effects me too]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1242767/+affectsmetoo")", so it is confirmed. Thanks.

---

### Post by yhereincv on 2013-10-29
Short story: My problem appears to be fixed: I installed the Nvidia-current display driver and removed the Nouveau display driver.
 

 Long story: To remove the &#8220;Nouveau display driver&#8221; first install the &#8220;Nvidia-Current&#8221; display driver.
 I ran into trouble because I removed the Nouveau -specific kernel DRM services -runtime and the &#8220;system settings&#8221; stopped working. Then I ran into more trouble because I removed the Nouveau display driver before installing the Nvidia-Current. Somehow I was able to go to a shell and installed the Nvidia-current driver with sudo apt-get -install nvidia-current (or something like that). That made the graphics work but still the &#8220;system settings&#8221; did not work. I reinstalled the Nouveau -specific kernel DRM services -runtime and the &#8220;system settings' still did not work. I found out that I needed to install or reinstall de Gnome-Control-Center and I did using &#8220;sudo apt-get -reinstall gnome-control-center&#8221; or &#8220;sudo apt-get -install gnome-control-center&#8221;.  Since I kept uninstalling and reinstalling the &#8220;runtime&#8221;, the &#8220;reinstall&#8221; worked at one point but then it didn't so I finally used the &#8220;install&#8221;. My system has been working fine since then and has not frozen.

---


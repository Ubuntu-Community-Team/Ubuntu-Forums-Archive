---
title: "New HTPC - Ubuntu 18.04 - Crash/Freeze"
date: 2018-12-16
forum: General Help
---

### Post by kamm747 on 2018-12-16
I've just build a new HTPC. 

Motherboard - Gigabyte B450 AORUS M
CPU - AMD Ryzen R5 2400G 3.6GHZ
RAM - 8GB 2X4GB - Kingston HyperX Fury DDR4 2666 PC4-21300
SSD - SSD Crucial MX500 M.2 500GB
HDD - WD 2TB Green

I've installed Ubuntu 18.04

I'm experiencing freezes mainly when watching videos, both on VLC and Kodi. Often at around 15 minutes or so into a movie (can be earlier or later) the screen will completely freeze as though I've pressed pause. The computer is completely unresponsive to mouse and keyboard, however I can shell in from a remote computer. Nothing seems strange with Top and all temps seem normal. 

Strangely I've had no crashes whatsoever when watching films on Netflix or BBC iPlayer through Firefox.

How should I debug this?

---

### Post by TheFu on 2018-12-17
I would check the log files by booting from alternate media, after the failure, and look for oddness.  If I guessed, it would be in the GPU drivers where I started, based on the description. It would be good to gather some information about the video driver.  **$ sudo lshw -C video** will have that info. The driver version is important too.

Did you OC the Ryzen at all? Many people do. 
Is the system stable for a week doing lots of work, but not doing video playback?  
Did you burn-in the system to ensure the RAM is ok?  
Is the RAM approved by the CPU and MB vendors at the speeds used?

I've got a Ryzen 5 2600 sitting in the hallway waiting to be put into a new build.  I looked at the Gigabyte MB, but decided against it for some reason, probably had realtek NIC (boo).  Did get a B450 from Asus ROG Strix with an Intel GigE NIC instead.  I'm not planning to use it for any video viewing, might not even leave a $40 GPU installed if it will boot without it. Mine will be a VM server and accessed remotely almost always.

---

### Post by oldfred on 2018-12-17
Some with new ryzen has some issues.
       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)
Asus Prime X399-A  with AMD Ryzen 1950X  Ubuntu 16.04.3
[https://ubuntuforums.org/showthread.php?t=2380798](https://ubuntuforums.org/showthread.php?t=2380798)

---

### Post by CatKiller on 2018-12-17
That definitely sounds graphics stack related to me. The AMD graphics stack has been under heavy development lately, so you might be able to find a backport of some of that, which might help.

You could also launch vlc from the command line to see if you get useful terminal output at the point that it freezes. You might then be able to use some combination of launch options to bypass whatever the problematic path turns out to be.

---

### Post by QIII on 2018-12-17
A problem in the graphics stack would present immediately.  The fact that this occurs after some period of use might be more indicative of a thermal issue.

What are you using for cooling?

---

### Post by kamm747 on 2018-12-22
Thanks for all the replies above and apologies for not responding, I'm subscribed to this thread, but didn't receive any email notifications.

Anyway, after scouring the internet, I eventually came across a suggestion to update the kernel and add Mesa drivers. Updating the kernel didn't work for me, but adding Mesa drivers did. It's been nearly a week and no more crashes since.

This is what I did (credit to OMG! Ubuntu! -  [https://www.omgubuntu.co.uk/2018/06/mesa-18-1-1-ubuntu-18-04-ppa](https://www.omgubuntu.co.uk/2018/06/mesa-18-1-1-ubuntu-18-04-ppa).)

```
sudo add-apt-repository ppa:ubuntu-x-swat/updates
sudo apt dist-upgrade
reboot
glxinfo | grep "OpenGL version"
```

---


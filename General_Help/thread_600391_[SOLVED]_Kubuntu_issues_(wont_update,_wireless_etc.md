---
title: "[SOLVED] Kubuntu issues (wont update, wireless etc etc)"
date: 2007-11-02
forum: General Help
---

### Post by Matticus on 2007-11-02
I have kubuntu installed on my laptop, as well as ubuntu, both sharing the same swap and storage partitions.

Anyways, when I first installed kubuntu the screen res would only go up to 800x600 (I wanted 1024x768), so I went through the xorg setup, and set the monitor display to medium, I dont actually think I changed anything else, but now on the login screen my mouse has a big black sqaure around it, not such a big deal as it goes away after login.

It also wont upgrade from 7.04 to 7.10 even though 7.04 has all its updates.

My wireless wont work, ndiswrapper is install, the drivers are installed and hardware is present, it just doesnt start up, if i modprobe ndiswrapper, the network manager can see my networks, but cant connect, and after reboot it cant see the wireless networks again. The frontend for ndiswrapper wont open, just starts to load then nothing, so I installed the drivers by ndiswrapper -i filename.inf. The card worked fine under windows, and works fine using ubuntu.

Also I dont know what I have done with either updates or xorg, but things are taking an age to load. For seemingly no reason.

As I havn't really done anything on kubuntu, do you think a complete reinstall is in order.
Also currently both /homes are on the root drives, do you think it would be a good idea to shrink down both root (kubuntu and ubuntu) partitions slightly, and use my storage drive as /home for both instead? Is it easier said than done though?

---

### Post by Matticus on 2007-11-02
Right well I got rid of kubuntu and reformated/partitioned everything, and reinstalled ubuntu fiesty, and am currently upgrading to gutsy.

So its technically solved. Ah well maybe I will try again sometime when I'm a little more linux savvy.

---


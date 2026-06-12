---
title: "Tired of signing into Google Account in Chrome..."
date: 2020-11-10
forum: General Help
---

### Post by dbee on 2020-11-10
My travel HP stream freezes quite often. I have to restart it and then sign into my Google account in chrome everytime.

I'm the only one that uses this computer. Also, since the email and password are autocompleted, there really isn't any point in me just clicking the 'submit' button on both pages from a security point of view.

How do I sign in automatically to Google with chrome on xubuntu?

While i'm at it, how do i get rid of the 'Default Keyring' password modal box on boot?

---

### Post by TheFu on 2020-11-10
Why not fix the root cause of the freeze?

I don't use Chrome, but I do use Chromium. It seems that Google has changed some settings since the last time and is forcing logins much more often. A few months ago, I could simply run chromium and be auto-logged in. That isn't happening anymore.

BTW, if you have gmail tied to any important accounts, I'd strongly urge you not to store any Google credentials so there are automatic logins of any sort.  There are always software bugs in all browsers that can lead to stored credentials being taken.  Just this week, a Chinese hacking competition was able to pwn Chrome, Firefox, Safari, QEMU, ESXi, Docker and a number of other high-profile software, including Win10.  [https://www.theregister.com/2020/11/09/tianfu_cup/](https://www.theregister.com/2020/11/09/tianfu_cup/)

Laptop freezes are often caused by low RAM situations.  A mix of user training and tuned swap storage can make a huge difference.  I've had issues with low-RAM laptops freezing. The solution was to place a 4.1G swap partition on the spinning HDD and to watch RAM+Swap use more carefully.  Chrome is a hog, but so is Firefox and thunderbird.  At the onset of the system slowing, if I notice the issue quickly enough, I can close thunderbird which frees up 500 MB+ RAM, then selectively close some tabs in the browser.  Memory use drops and the slow down ends. All is good.

---

### Post by dbee on 2020-11-17
> **TheFu said:**
> Why not fix the root cause of the freeze?

I don't use Chrome, but I do use Chromium. It seems that Google has changed some settings since the last time and is forcing logins much more often. A few months ago, I could simply run chromium and be auto-logged in. That isn't happening anymore.

BTW, if you have gmail tied to any important accounts, I'd strongly urge you not to store any Google credentials so there are automatic logins of any sort.  There are always software bugs in all browsers that can lead to stored credentials being taken.  Just this week, a Chinese hacking competition was able to pwn Chrome, Firefox, Safari, QEMU, ESXi, Docker and a number of other high-profile software, including Win10.  [https://www.theregister.com/2020/11/09/tianfu_cup/](https://www.theregister.com/2020/11/09/tianfu_cup/)

Laptop freezes are often caused by low RAM situations.  A mix of user training and tuned swap storage can make a huge difference.  I've had issues with low-RAM laptops freezing. The solution was to place a 4.1G swap partition on the spinning HDD and to watch RAM+Swap use more carefully.  Chrome is a hog, but so is Firefox and thunderbird.  At the onset of the system slowing, if I notice the issue quickly enough, I can close thunderbird which frees up 500 MB+ RAM, then selectively close some tabs in the browser.  Memory use drops and the slow down ends. All is good.

Thanks, TheFu

So it's impossible then? Yeah. Fixed the RAM and storage issue I believe. At least i hope so anyway. 

Never used Thunderbird. Uninstalled it just in case. Reset */swapfile* to 4GB (recommended max). Should help with low RAM system. Then deleted */var/lib/docker/overlay2* which released 6.5GB of harddrive. Also installed microsd and moved all git files to mounted card.

If anyone is having a similar issue, documented most of it ...

[https://ubuntuforums.org/showthread.php?t=2453566]("https://ubuntuforums.org/showthread.php?t=2453566")

---


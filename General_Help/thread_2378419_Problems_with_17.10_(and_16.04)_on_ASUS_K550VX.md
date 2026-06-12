---
title: "Problems with 17.10 (and 16.04) on ASUS K550VX"
date: 2017-11-23
forum: General Help
---

### Post by yomy on 2017-11-23
Hello. First time posting on forums.


I got a new laptop yesterday - ASUS K550VX / I7-7700HQ / GTX950M
I've had multiple problems from the start, and I'll try to explain the best I can.


pre-start:
Cleaned the SSD, removed all partitions, intending to dual-boot Windows 10 and Ubuntu 16.04.
Windows 10 setup worked fine, no issues.


1st problem solved:
I started by trying to install Ubuntu 16.04, but the setup wouldn't start - was stuck at Ubuntu logo with dots.
Thinking something was wrong with installation, I got 17.10 on a different usb drive and tried again, with the same problem reoccurring.
After some research, I successfuly started the setup with "nomodeset" flag, and got trough the installation of 17.10. (albeit with low resolution and tabbbing to get to the next button)


2nd problem partially solved:
After installing and booting, it felt sluggish, and i checked the syslog, just to see it filling up with errors indefinetely. Browsing again, the problem looked similar to this:
[https://askubuntu.com/questions/748078/nvidia-geforce-930m-driver-and-pci-bus-error](https://askubuntu.com/questions/748078/nvidia-geforce-930m-driver-and-pci-bus-error)
First, I installed the nvidia drivers from graphic-drivers PPA, and chosen the oldest one, and after several reboots, and trying all the listed drivers with different experiences of UI sluggishness, the newer driver loaded. However, the syslog was still filling up with the same error (reaching a couple of GB by now, I purged the log).
Finally the error stopped appearing with pci=nomsi flag during boot. Now I'm not sure if this can pose any problems for the continual use of the system or not. Never before have I dabbled with boot options, and usually everything worked.


3rd problem solved, but 4th problem occurred:
After everything from above I thought I've finished with setting it up. But I was not that lucky. After trying to download something over the wifi (a file of ~500mb), around 150mb of downloading the connection would just freeze. - looks connected from the UI, but cannot disconnect/turn off wifi, ping returned nothing.
More research - found this: [https://askubuntu.com/questions/872313/wireless-issues-on-16-04-with-rtl8821ae-asus-e202s/955012](https://askubuntu.com/questions/872313/wireless-issues-on-16-04-with-rtl8821ae-asus-e202s/955012)
Followed the first answer and confirming the wifi card was rtl8821ae, and compiled and installed rtlwifi_new from git repo, rebooted and the wifi worked correctly, downloading now worked.


4th problem:
Now everything seems fine, except immediately after logging in, my fan goes to max speed. Processor looks idle in top / and in ui system monitor. No errors or anything worth noticing in logs.


Now this is the time that after 6 hours I had to take a break. My original idea was to get 16.04 installed and use the laptop normally, but seems it's not that easy.
Now I'm thinking of replacing the laptop, but all of the replacements I could get from the store are with the same gtx950m card, and I fear I'm gonna get stuck with the same problems all over again.


Any help would be very much appreciated.

---

### Post by Yellow Pasque on 2017-11-23
If you use pci=noaer instead of pci=nomsi, does the fan work better?

---

### Post by yomy on 2017-11-24
Thank you for the suggestion, I'll try that today after work. If it does not yield with a satisfactory result, I'll probably return the laptop.
**EDIT: **Tried it, error log started filling up with errors again. Finally returned the laptop and will get a different one. It's too much unlucky moments to justify trying to make it work.

---


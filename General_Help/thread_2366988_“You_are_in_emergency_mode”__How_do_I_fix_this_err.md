---
title: "“You are in emergency mode” / How do I fix this error?"
date: 2017-07-24
forum: General Help
---

### Post by jhsheridan on 2017-07-24
System: Dell XPS 15 9560 
Ubuntu Version: Ubuntu Gnome 17.05

  
I've been using my Ubuntu install for about 2 weeks now with little  to no issues. This morning I booted up and was greeted with this screen:

  
[IMG]https://i.stack.imgur.com/QIRDS.jpg[/IMG]


  If I try to press enter or ctrl+D, it just prints the following, and doesn't allow me to type any commands:
  
[IMG]https://i.stack.imgur.com/6UVH0.jpg[/IMG]


  I booted up with a live USB of Ubuntu and typed in "journalctl -xb"  which gave me thousands of lines of output. I assume the ones  highlighted in red were the problematic ones. They included:
  
[LIST]
[*]"ubuntu-gnome kernel: ACPI Error Namespace lookup failure, AE_NOT_FOUND ACPI Error: 1 table load failures, 12 successful" 
[*]"ubuntu-gnome networkmanager: ((devices/nm-device.c:970)): assertion '' failed" 
[*]"ubuntu-gnome kernel: ath10k_pci: Could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin'" 
[*]"ubuntu-gnome kernel: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e0 device [8086:a110] error status/mask=00001000/00002000 Replay Timer Timeout 
[/LIST]
  I've tried to include all the information I had so far. If I can upload anything else, I'm happy to do that.


  Does anyone have any ideas as to what I can do?

---

### Post by #&amp;thj^% on 2017-07-24
Try this workaround to add "pci=noaer" to your kernel command line:

1) edit /etc/default/grub and and add **pci=noaer** to the line starting with GRUB_CMDLINE_LINUX_DEFAULT. It will look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"
```
2) run "sudo update-grub"
3) reboot

---

### Post by jhsheridan on 2017-07-24
I tried adding this from the grub boot menu just to get it booted, but it didn't work.

I don't know how I can add this and run "sudo update-grub" from the OS because, as I stated in my original post, I can't run any commands from that error screen. I just get line after line of what is shown in the second screenshot I attached.

---

### Post by #&amp;thj^% on 2017-07-24
Well it was worth a shot...just trying to help.;)
Do you have a recovery mode from grub selection?
This may be meaningless but you could drop to command prompt from there.

---

### Post by #&amp;thj^% on 2017-07-24
Might be useful if you can get to TTY session and check:
```
journalctl -b

```
As I have no problems with similar Specs.
```
inxi -S
System:    Host: me-750-417c Kernel: 4.10.0-29-generic x86_64 (64 bit)
           Desktop: Gnome 3.24.2 Distro: Ubuntu 17.04

```
And do you have a hybrid GPU?
```
inxi -G
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: X.Org 1.19.3 drivers: modesetting,nvidia
           Resolution: 1360x768@60.02hz, 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 381.22

```
And one final thought is your Bios updated to latest available?
Good Luck.

---

### Post by jhsheridan on 2017-07-24
So I do have a recovery mode option to drop into a root shell, but it says everything is read only. I've tried using sudo, but I still get the same error. It just always says it's a read only filesystem.

When I try inxi from the root shell, it says it's not installed. I do know I have the NVIDIA graphics card, and I'm running the proprietary drivers.

I'll try to update the bios, but I think I have the most recent. Is it okay to update this from my windows partition?

Thanks so much for your help.

---

### Post by #&amp;thj^% on 2017-07-24
> **jhsheridan said:**
> 
I'll try to update the bios, but I think I have the most recent. Is it okay to update this from my windows partition?

Thanks so much for your help.
Yes that would be fine from the Windows partition.:D
Well I wish i was actually helpful here, but your welcome.
Just out of curiosity< Is this only a Intel Graphics machine or do you also have the Nvidia GPU?

---

### Post by jhsheridan on 2017-07-24
Looks like the bios is up to date, so that's not it. I have the NVIDIA GPU

---

### Post by #&amp;thj^% on 2017-07-24
Is that what is getting booted to as default then? (Nvidia)

---

### Post by deadflowr on 2017-07-24
You should still have the last kernel installed from before this debacle happened.
You can try booting into that if you need to, as you try troubleshooting problems.

(In the grub boot menu select Advanced Options then select the older kernel (not the recovery mode option)
That should allow you to at least run a functional desktop and make it easier to figure out.

---

### Post by jhsheridan on 2017-07-24
1fallen - I'm not sure. How do I find out?

 deadflowr - I am able to boot into the old kernel using your suggestion. I'm just not sure where to proceed from here.

Sorry if these questions are elementary. I haven't used Linux in about 8 years. I'm just coming back from Mac. These kind of stability issues are what made be leave Linux the first time around, and I hope I'm not headed down that road again. I'm just very, very frustrated.

---

### Post by deadflowr on 2017-07-24
By doing what I suggested it will allow you to post back anything asked for easier, like the commands 1fallen posted (or will post).
(It's better to post the output from the commands than screenshots, since screenshots tend to be limited in what they tell anyone)

One to do would be since it was mentioned you do not have inxi installed, you can go ahead and install that:
```
sudo apt install inxi
```
which may help determine a few things.

Just off the cuff.

---

### Post by #&amp;thj^% on 2017-07-24
> **deadflowr said:**
> By doing what I suggested it will allow you to post back anything asked for easier, like the commands 1fallen posted (or will post).
(It's better to post the output from the commands than screenshots, since screenshots tend to be limited in what they tell anyone)

One to do would be since it was mentioned you do not have inxi installed, you can go ahead and install that:
```
sudo apt install inxi
```
which may help determine a few things.

Just off the cuff.

+1 deadflowr hates it when I beat around the bush.:) (Jokingly)
Yes and after that is installed return the output form the terminal:
```
inxi -G
```
And no worries there are No Dumb questions here just Dumb answers.:D
This new kernel update sure has had a impact on more than a handful of users lately.(Just my own observations here FTR)

---


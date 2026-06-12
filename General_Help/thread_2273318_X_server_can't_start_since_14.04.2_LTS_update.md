---
title: "X server can't start since 14.04.2 LTS update"
date: 2015-04-12
forum: General Help
---

### Post by thomas50 on 2015-04-12
Hi,
I have an AsusZenbook Prime UX31A and I've been happily running Ubuntu on it since I bought it two or three years ago. Being a linux user since 10yr+, I know my way around the system, but here I have to admit that I'm out of my depth.
 
I had postponed updating for a while, and when I finally said "yes" to aptitude about a week ago the update had an unpleasant side-effect: X is now unavailable and says "Fatal server error: (EE) no screens found [...]" in /var/log/Xorg.0.log as well as if I try to run startx. To make matters worse, I also have lost all network interfaces (except the loopback).

After some pretty intense googling and forum reading I still have not reached any results in fixing this. My observations so far are:
- /var/log/Xorg.0.log reveals that a) X can't load modules (intel, fbdev, vesa, ...) and can't open /dev/dri/card0, and b) "Devices detected, but none match those in the config file.". Someone suggested uninstalling and reinstalling Xorg, but I want to get the networking to work again before attempting that.
- booting on a live usb stick, 14.04.2 LTS works fine (X works, networking works, everything looks fine) so there should be no major support issues with my hw

Regarding the networking: 
- >sudo services networking restart is ineffective, (as the only interface around is the lo...)
- /etc/network/interfaces contained only the loopback (why??) and editing the file manually to add at least eth0 + restart did not help.

Any help with troubleshooting this would be greatly appreciated. Attached are dumps/copies of lspci, lsusb, /var/logs/Xorg.0.log, /etc/network/interfaces, ifconfig. 
[ATTACH]261238[/ATTACH]
Thanks

---

### Post by dino99 on 2015-04-12
nowadays the kernel deals directly with X, so xorg.conf is most of the time a problem source. You does not need one, except for multi-screens config
lot of issues often comes from the backported packages (due to version conflicts most of the time) and third party packages (ppa) can also result to the same madness.
booting into recovery mode, then you should be able to do some maintenance from the terminal: like deactivating some 'extra' sources, purging ppa (ppa-purge) and updating

if you still have the stock kernel installed (not one backported) then try to boot with it, and remove 'quiet splash' to see the boot process warnings/erros

---

### Post by thomas50 on 2015-04-12
Thanks for your response. Regarding xorg.conf I did an mv xorg.conf xorg.conf.bak but it changed nothing. 
I have done nothing exotic to the kernel, so it shoud be the stock kernel, right?
My key trouble right now is that I can't connect to internet, even by wired ethernet.

---

### Post by thomas50 on 2015-04-13
>  [...] remove 'quiet splash' to see the boot process warnings/erros

First message is "error: no video mode activated"

Most of the posts I found about this message were about a bug in ubuntu 11 or 12 where this appeared from time to time without any real problem. However, here is it seems relevant, as X does not start.  
Another odd thing is that I still don't get a grub with (a timeout) menu although the quiet splash option is removed and the [COLOR=#000000][FONT=monospace]GRUB_TIMEOUT[/FONT][/COLOR] is set to 10 sec. What's wrong with my [/etc/default/grub file]("http://pastebin.com/iVYmPhPe")?

---

### Post by thomas50 on 2015-04-13
[Here is the boot.log]("http://pastebin.com/nnwwbPtw")
I don't see anything really shocking here. Some fails for bluetooth and Samba server. And one fatal alert about the module "cuse", whatever that is...
Anyone, any ideas?

---

### Post by thomas50 on 2015-04-13
Ok, I finally got it straight with grub; I commented out the 
[...]
#GRUB_HIDDEN_TIMEOUT=0#GRUB_HIDDEN_TIMEOUT_QUIET=true
[...]
options to get access to a classic grub menu. From there I did some experiments, trying to boot into recovery mode of the 3-18-0-48. failsafeX still failed miserably, and activate network failed as well. Then I tried doing a standard boot with one of the older versions around (dont recall the exact version number, but it doesn't matter too much now) and that did the trick! I got back to the GUI login, and I got back the networking. So now I'm trying to figure out what to do next and how to fix this mess. Clearly it was the last update that f***ed up my config, and I need to unscrew what was screwed up. To be continued.

---


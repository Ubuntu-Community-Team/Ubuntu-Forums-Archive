---
title: "xawtv Problems"
date: 2005-08-27
forum: General Help
---

### Post by Aypok on 2005-08-27
Hi,

I'm running into some difficulties when using xawtv. The card is a Hauppauge WinTV PCI card, Bt878 (rev 17), and seems to be detected correctly. However, when I run "xawtv", I get the following error and a black display:

```
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
WARNING: v4l-conf is compiled without DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
``` 

With the last line being repeated everytime I attempt to interact with xawtv.

I've come across this error (or one very similar) before, when I compiled and installed xawtv on Slackware 10.1 (I installed this version via apt-get). I fixed that by enabling the DGA module in the xorg.conf file, yet that seems to have no effect on this version.

I've tried all the switches and options that seem appropriate ("-fb", "-nodga", etc), read through the man page for it, and googled - all with no useful outcome.

I even decided to install and try TV-Time, but that just gives me a blue screen.

Also, when I press the escape key to kill xawtv, just before the window closes I see the image that should be showing - but only for a split-second.

I booted back into the Slackware 10.1 install that I have for this machine and the TV card works fine with xawtv, so the card is not at fault. Can anyone help me correct what is?

Thanks.


Aypok...

---

### Post by arnieboy on 2005-08-27
[QUOTE=Aypok]Hi,

I'm running into some difficulties when using xawtv. The card is a Hauppauge WinTV PCI card, Bt878 (rev 17), and seems to be detected correctly. However, when I run "xawtv", I get the following error and a black display:

```
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
WARNING: v4l-conf is compiled without DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument
``` 

With the last line being repeated everytime I attempt to interact with xawtv.

I've come across this error (or one very similar) before, when I compiled and installed xawtv on Slackware 10.1 (I installed this version via apt-get). I fixed that by enabling the DGA module in the xorg.conf file, yet that seems to have no effect on this version.

I've tried all the switches and options that seem appropriate ("-fb", "-nodga", etc), read through the man page for it, and googled - all with no useful outcome.

I even decided to install and try TV-Time, but that just gives me a blue screen.

Also, when I press the escape key to kill xawtv, just before the window closes I see the image that should be showing - but only for a split-second.

I booted back into the Slackware 10.1 install that I have for this machine and the TV card works fine with xawtv, so the card is not at fault. Can anyone help me correct what is?

Thanks.


Aypok...[/QUOTE]
if DGA is still enabled in xorg.conf then do the following:
```
sudo apt-get remove v4l-conf
```
followed by:
```
sudo apt-get install v4l-conf
```
let me know if this solves your problem.

---

### Post by Aypok on 2005-08-28
Thanks for replying. Unfortunately, it didn't seem to make any difference.

I did finally get it to work, though. I decided to try feeding "v4l-conf" the framebuffer address with the -a switch. Why didn't I do that before? I had no idea how to find the address. A quick grep of the Xorg log fixed that.

If anyone else is having this problem, try the following:

```
grep framebuffer /var/log/Xorg.0.log
``` 

Which should return something like: (The value at the end will most likely be different)

```
(--) MGA(0): Linear framebuffer at 0xCD000000
``` 

Now run "v4l-conf" and pass it the address from above ("0xCD000000"), thusly:

```
sudo v4l-conf -a 0xCD000000
``` 

Try running "xawtv" again and it should magically be fixed :)


Aypok...

---


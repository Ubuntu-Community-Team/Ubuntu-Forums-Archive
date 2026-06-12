---
title: "Could not install ubuntu 14.04 should I go back to 13.10?"
date: 2014-07-27
forum: General Help
---

### Post by AlyssaVS on 2014-07-27
I have tried three fresh installs of 14.04 on my older laptop and each have resulted in the same problem. Everything appears normal (after a long boot) but I cannot open applications or it takes an extremely long time for them to open... and then they crash. The latest error message is:

Sorry Ubuntu has experienced an internal error
Executable path
 /usr/bin/unity-control-center
Package
 unity-control-center 14.04.3+14.04.20140604-Oubuntu1
Problem type
 Crash
Title
 unity-control-center crashed with signal 7 in elf_machine_rela_relative()
ApportVersion
 2.14.1-Oubuntu3.2
Architecture
 amd64
CoreDump
 unity

It goes on from there. I am a novice user so none of this makes sense to me. I guess my question is... Should I revert back to 13.10 since I had no problems with it on that particular laptop? Or if not 13.10, is there another version that is better or even a different OS (suitable for more novice users) that I should try?

It is a:
 Toshiba Satellite A305 -PSAG4U
 Intel Core 2 Duo T8100 at 2.1 GHz
 4GB
 64 Bit, 2048 MB, DDR2
 AMD/ATI Mobility Radeon HD 3450/3470

Thank you!

---

### Post by QIII on 2014-07-27
Hello!

In short:  No, don't go back.  13.10 has passed its End of Life and is no longer supported.

Let's go back a bit.  

How are you installing?  DVD or thumb drive?  Did you confirm the md5sum to ensure that the .iso file was good?  

We'll work from there when we know at least that much.

---

### Post by AlyssaVS on 2014-07-27
Hi! Thanks for the reply!

Ok, duly noted. Won't go back. :) I installed from a DVD. Did not confirm the md5sum. Actually never heard of that.

---

### Post by ajgreeny on 2014-07-27
I also note that your graphic card is asn older ATI/AMD that is no longer supported by the proprietary fglrx driver, so if you have had that in the past you will now have to remove it completely, as well as any /etc/X11/xorg.conf file that it may have produced when it was installed.  If there is no xorg.conf file do not be concerned as it has not been needed nor made by the default system for some years now.

The open source radeon driver is the only one available to you now.

---

### Post by grahammechanical on 2014-07-27
The CPU and Memory size (RAM) are acceptable. If you install without ticking "install third party software" the installer will not setup a proprietary video driver. It will use the open source video driver. That might get around this problem. You can always install Ubuntu Restricted Extras from the software centre to get that third party software after Ubuntu has been installed.

Another thing to consider. Is Ubuntu running with a fall back open source video driver? Go to System Settings>Details and see what graphic driver is being used. If it says Gallium 0.4 llvmpipe then that is the reason for the apparent slowness of operation. Go to Software and Updates>Additional Drivers tab and wait until the utility offers some video drivers and select the open source video driver and then reboot.

Regards.

---

### Post by egeezer on 2014-07-27
If you purchased a ready-made DVD, the md5sum is probably good.  However, it you downloaded it as an iso file, you can check the sum by typing into a terminal 
```
$ cd ~/Downloads
```
That gives you a new prompt, at which you need to type:
```
$ md5sum (followed by the title of the iso)
```

You can find the correct md5sum to check against at the Ubuntu releases page.

---

### Post by AlyssaVS on 2014-07-27
Hi and thanks guys! I reinstalled leaving out the third party software. It is definitely still slow but I was actually able to get into System settings this time to check which graphics driver is in use. It is the Gallium 0.4 but there were no additional drivers available under Software and Updates. Is there another way I can get the open source video driver?

Also how do I determine if "[COLOR=#000000]the proprietary fglrx driver" or any "[/COLOR][COLOR=#000000]/etc/X11/xorg.conf file" are present and how would I go about safely removing them?

Thank you very much for your help![/COLOR]

> **egeezer said:**
> If you purchased a ready-made DVD, the md5sum is probably good.  However, it you downloaded it as an iso file, you can check the sum by typing into a terminal 
```
$ cd ~/Downloads
```
That gives you a new prompt, at which you need to type:
```
$ md5sum (followed by the title of the iso)
```

You can find the correct md5sum to check against at the Ubuntu releases page.

Hi there! Yep it checks out. I've reinstalled leaving out third party software but still very slow. Am now trying to find the open source video driver the gentlemen above talked about.

Gotta say, it's fun learning about this stuff even though it's because I'm having difficulties. :)

Thanks for your help!

Oops sorry if I made a bad assumption in that last post with "gentlemen."  :(

---

### Post by egeezer on 2014-07-27
Old ATI graphics are an endless pain for Ubuntu (I have one system with them myself).  Do try grahammechanical's suggestions:

Go to System Settings>Details and see what graphic driver is being  used. If it says Gallium 0.4 llvmpipe then that is the reason for the  apparent slowness of operation. Go to Software and Updates>Additional  Drivers tab and wait until the utility offers some video drivers and  select the open source video driver and then reboot.

Glad you're having fun learning.  I'm still learning too, and it's been 5 years so far.

---

### Post by AlyssaVS on 2014-07-27
Hi egeezer. Yeah I already tried that but it said "no additional drivers available."

---


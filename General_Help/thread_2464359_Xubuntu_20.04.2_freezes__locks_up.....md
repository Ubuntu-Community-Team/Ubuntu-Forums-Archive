---
title: "Xubuntu 20.04.2 freezes / locks up...."
date: 2021-06-30
forum: General Help
---

### Post by Furycd001 on 2021-06-30
HI guys..

I have a Lenovo ideadpad 330 laptop that is randomly freezing / locking up. *CTRL+ALT+F_WHATEVER* does not work & sometimes I can move the mouse cursor, but do nothing else. I can do nothing but hold down the power button to hard reboot the laptop. Here is the laptops specs & the output of *journalctl -b-1*. Many thanks in advance for replying & helping....

**LAPTOP:** Lenovo ideapad 330-15ARR
**OS:** Xubuntu 20.04.2 LTS
**KERNEL:** x86_64 Linux 5.4.0-67-generic
**CPU:** AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx @ 8x 2GHz
**GPU:** AMD RAVEN (DRM 3.35.0, 5.4.0-67-generic, LLVM 11.0.0)

[**journalctl -b-1 > prevboot.txt**]("https://paste.ubuntu.com/p/TTR2bWjTzf/")

---

### Post by Furycd001 on 2021-06-30
I should mention that these freezes / lockups also happened in 18.04.2. In 20.04.2 they happen way less, but they still happen a few times a day. I DID NOT do a fresh 20.04.2 install, rather I just upgraded directly from 18.04.5. Anyway the system is mainly left as default from the install apart from a screen tearing fix, some screen brightness adjustments in power management settings & this line below added to grub when trying to fix these freezes / lockups..

```
 GRUB_CMDLINE_LINUX_DEFAULT="idel=nomwait" 
```

A freeze can happen even when I have very little open. Sometimes I can be looking at a document in libreoffce, copying files in thunar or watching a 1080p youtube video in firefox. With only firefox (4-tabs) & xfce4-terminal (htop) open the laptop is using 1.66G/7.39G. This seems a lot higher than any of my other xfce installs. I've also noticed that whenever the battery is charging it will constantly switch between charging & discharging every couple of minutes or so. Not sure if this is related, but never had or seen this problem before. Again any help appreciated & many thanks in advanced for replying & for helping....

---

### Post by Furycd001 on 2021-11-18
HI guys.. I'm still having problems with this laptop. It's fully updated & currently running Xubuntu 20.04.3 LTS with kernel 5.4.0-89-generic.

[**Here is the output from dmesg**]("https://termbin.com/h0qg") && [**here is the output from journalctl for the previous boot....**]("https://termbin.com/1qaxk")

---

### Post by vmpx on 2021-11-18
> **How to fix Ubuntu 18.04 freeze after boot when NVIDIA card installed**

Replace in GRUB menu for 18.04 ”quiet splash” with ”quiet splash     nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
After that freeze should be gone.                                       
This is also applicable on Ubuntu 20.04.

Another alternative for shut down:
> Alt+SysReg (print key) + REISUB

---

### Post by Furycd001 on 2021-11-18
Thanks for the heads up. I'm going to try this right now....

---

### Post by pacau on 2021-11-18
Hello
I am very interested in the conclusion of this.
I faced the same issue with 20.04. Updating to 21.10 was even worse: freezes happened after opening a few windows (firefox, thunderbird, openoffice...). Not even possible to switch to console mode. (I am running on Samsung R730, intel core i3, Nvidia.)
I went back to 18.04 and no more freeze ! (this back up was quite painful because I had to install some software manually. E.g my emails were broken by the back up to a previous version of thunderbird, that changed the database in between versions).
Thanks
Pascal

---

### Post by pqwoerituytrueiwoq on 2021-11-18
try installing linux-image-generic-hwe-20.04 and then reboot and see if that helps

---

### Post by Furycd001 on 2021-11-19
> **vmpx said:**
> This is also applicable on Ubuntu 20.04.

Another alternative for shut down:

This along with blacklisting amdgpu seems to have done the trick. Going to mark this as solved now....

---

### Post by pacau on 2021-11-19
I am a bit confused. Does that trick fix freeze at boot step or does it fix freezes during normal operation ?
Thanks

---

### Post by vmpx on 2021-11-19
It (this trick) fixes freezes during normal operation.

---

### Post by pacau on 2021-11-20
Thanks. I'll give it a try.

---

### Post by pacau on 2021-12-02
Indeed, nomodeset change in the grub removes the issue of freezes. 
But the HDMI is then no longer working for external screens. Another minor drawback is that only holding the power button can turn off the computer.

---

### Post by The Cog on 2021-12-02
It may be worth trying Ctrl-Alt-Del (to switch to a TTY) followed by Ctrl-Alt-Del (to reboot). I think this is probably more gentle, and gives the OS time to shut down more cleanly.

---

### Post by vmpx on 2021-12-02
This is the original message:
```
 **How to fix Ubuntu 18.04 freeze after boot when NVIDIA card installed**
  In this quick guide I will show how one could easily fix that annoying freeze after Ubuntu 18.04 installation. Should be noted that it is funny that driver
   used during the installation works absolutely fine, but one that you will use after installation is done &#8212; will keep you crashing.
    1. Start the computer. After the bios keep pressing &#8216;E&#8217; or &#8216;ESC&#8217; to initiate grub.
    2. On the grub screen click select &#8216;*Ubuntu&#8217; and press &#8216;E&#8217;

   3. Find the line that starts with &#8216;linux&#8217; and remove &#8216;quite splash&#8217; and type &#8216;nomodeset&#8217; at the end of the line.

   4. Press &#8216;F10&#8217; and boot. The screen resolution should be really bad as we just disabled all graphic drivers. The good news &#8212; freeze is now gone.

   5. On the last step we need to fix it once and forever. Open terminal and run:
sudo vi /etc/default/grub

   Find the line
$ GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;

   and add &#8216;nomodeset&#8217;, so at the end it will look like the following:
$ GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash nomodeset&#8221;

   Pass the changes to the grub by running command:
sudo update-grub2

   6. You are all set. Now it is good time to install correct NVIDIA drivers. For example from here.

```
I think number 6. is important when one has to install the NIVIDIA driver.

---

### Post by T6&amp;sfpER35% on 2021-12-02
This is probably not the answer , but just an observation iv'e noticed. My xubuntu also used to freeze up randomly after a month or two of use. (keyboard mouse everything)
The longer i use it the worse it gets. Now iv'e done a couple of fresh installs to "fix it" , but always after install i'd put conky on.
Now the last time i fresh installed i decided to leave conky and see what it does ...it's been 3 months now without a single freeze (touch wood)
So yea i'll see how it goes now .

---


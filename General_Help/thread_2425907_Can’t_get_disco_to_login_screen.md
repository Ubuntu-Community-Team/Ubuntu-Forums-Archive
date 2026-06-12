---
title: "Can’t get disco to login screen"
date: 2019-09-01
forum: General Help
---

### Post by augray on 2019-09-01
I have a new Lenovo with Disco Dingo on it. Before that I had Cosmic Cuttlefish on it. On cosmic, when I would reboot the laptop, it would sometimes get &#8220;stuck.&#8221; I would usually &#8220;solve&#8221; this by power cycling until it successfully launched. When Disco came out, I updated, hoping the issue would be fixed. Unfortunately, it persisted. I just put up with it until a little over a week ago when I had to reboot, and haven&#8217;t been able to get to the launch screen since.


The &#8220;freeze&#8221; happens as follows:
1. I power up
2. I enter my disk decryption password, and the decryption appears to succeed
3. I get to the load screen with &#8220;ubuntu&#8221; over the colored loading dots. It sometimes appears to freeze here, but if I wait long enough, it seems to always get past it.
4. The screen for black, and stays black no matter how long I leave it.


I&#8217;m a long time Ubuntu user and software engineer, but the boot process and many other &#8220;low-level&#8221; OS details are a bit of a black box to me, so I don&#8217;t really know how to proceed. Especially since I can&#8217;t even figure out how to boot into any kind of recovery mode to poke around.


FWIW, I vaguely remember trying to look into this when I was on cosmic, and thinking it may have something to do with the graphics card, so if it helps I have an Nvidia Geforce GTX.


So, what next (either debugging, resolving)?

---

### Post by oldfred on 2019-09-02
Have you installed the correct nVidia driver from Ubuntu repository or ppa?
       dkms status 
    
Have you updated UEFI from Lenovo and if SSD SSD firmware?

What model Lenovo? 
Most brands have issues common across models. Lenovo seems to have a million models all different as few posts show similar issues.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please only copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by augray on 2019-09-07
Thank you so much for your response! I seem to be in a good state now, let me describe my process for you and posterity:

1. I tried using the USB I installed from to boot, but could not (yes I tweaked the UEFI settings to select it as the first boot device).
2. UNRELATED BREAKTHROUGH: I found I could disable the Ubuntu load screen after disk decrypt by using the function keys. The mentioned being unable to connect to some service I can't recall anymore. But the main upside was this allowed me (for some reason) to get to the login screen. Sadly, when I tried to log in, I got back to a frozen black screen :-(
3. UNRELATED BREAKTHROUGH 2: Next time I got to the login screen, I checked the available settings before logging in, and saw "Ubuntu on Wayland" as an option. Duck-duck-going that showed that it was an alternative to X Windows, which suggested to me that it might help since the problem seemed like it could be graphics related. I tried, and it worked!
4. Once in my desktop environment, I popped open terminal and tried `dkms status` as you suggested, but it gave me nothing, just returned right away. This gave even more credence to the idea that it might be driver-related.
5. Some more duck-duck-going got me to [this post]("http://forums.lenovo.com/t5/Other-Linux-Discussions/Lenovo-Legion-Y520-Linux-Support/m-p/4254214#M11935"), which suggested cleaning out nvidia drivers, reinstalling them, and updating. I did that!
6. Before shutting down to check whether this worked, I [edited my grub configs]("https://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry#148097") to not get skipped (set timeout to 10) so I could enter recovery mode if needed.
7. I checked my syslog around the time when I had been constantly getting stuck, and it was chock full of nouveau errors (apparently it's an alternative driver for the GPU I had switched to when experiencing similar problems on cosmic with the default drivers).
8. Rebooting, everything worked as expected, and I could log in to write this post!

FWIW:
GPU: GP107M [GeForce GTX 1050 Ti Mobile]
Working driver: nvidia, 418.56, 5.0.0-27-generic, x86_64
Laptop Model: Lenovo Legion Y530-15ICH

---


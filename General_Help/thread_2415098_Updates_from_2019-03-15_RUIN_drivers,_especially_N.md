---
title: "Updates from 2019-03-15 RUIN drivers, especially NVIDIA."
date: 2019-03-19
forum: General Help
---

### Post by nerv-agent on 2019-03-19
I'm on Ubuntu 16.04 LTS. I updated last Friday and all sorts of drivers got messed up. The wifi stopped working, but I fixed that.  

Now NVIDIA is completely screwed up! I am STUCK using the Intel GPU on this thing. I don't recall what NVIDIA GPU I use, and I can't find out since my system can't detect it anymore! I think it was a Nvidia Quadro M620 but I'm not sure, I can't find the receipt for my computer. 

I updated the NVIDIA drivers, and it DID NOTHING.  

Here are the fail directions I followed:  [URL="https://devtalk.nvidia.com/default/topic/1032882/linux/nvidia-settings-error-unable-to-load-info-from-any-available-system/"]
https://devtalk.nvidia.com/default/topic/1032882/linux/nvidia-settings-error-unable-to-load-info-from-any-available-system/[/URL]  [URL="https://askubuntu.com/questions/935929/cant-switch-to-nvidia-graphics-card-on-ubuntu-16-04"]
https://askubuntu.com/questions/935929/cant-switch-to-nvidia-graphics-card-on-ubuntu-16-04[/URL]

```
sudo prime-select nvidia
[sudo] password for owner: 
Info: the current GL alternatives in use are: ['mesa', 'mesa']
Info: the current EGL alternatives in use are: ['mesa-egl', 'mesa-egl']
Info: selecting nvidia-384 for the nvidia profile
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in manual mode
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in manual mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in manual mode
```

```
nvidia-settings

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system
```

I even disabled secure boot in my BIOS. DOES NOTHING.  

I have to go to work early tomorrow and I don't have time to stay up way past midnight trying to figure out this hot mess. How do I get my NVIDIA GPU working again? I can't be the only one who got screwed over by last Friday's update.  

At this point I'm seriously considering going back to Windows 7 for anything gaming or media related.

---

### Post by nerv-agent on 2019-03-21
I've been scouring Google entering any command line I can find only to find that they do nothing.

If my understanding is correct, a new kernel update happened on March 10th, a few days before the epic fail update.

Could it be that the kernel was updated and not compatible? If so, how do I roll back to a previous kernel?

---

### Post by nerv-agent on 2019-03-21
I rolled back from 5.0 to 4.4, and all that did was kill the wifi. So I'm back on 5.0.  Any help would be nice.

If anything, anyone else who is having the same issue will know what "solutions"** don't work** according to this thread.

---

### Post by ubname on 2019-03-22
Hi, what do you mean with "5.0" ? The kernel?
If so it is, is 5.0 kernel already available for Ubuntu 16.04, that sound strange...

---

### Post by mc4man on 2019-03-22
There was a proposed kernel update for the 4.4 kernel that [broke nvidia drivers]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1573508"). This was fixed in Ubuntu's repo's 340 & 384 nvidia driver packages so the proposed kernel, (4.4.0.143.151) was promoted a few days ago & patched nvidia driver packages made available.

However any newer nvidia packages like from the graphics driver ppa have not been patched and will not work with 4.4.0.143.xx kernel. (be it in 14.04 or 16.04
In that case, on 16.04, one should use the linux-generic-hwe-16.04 kernel, currently 4.15.0.46.67 It works fine with any nvidia driver newer that 384
(- here on 16.04 using the 415 nvidia driver from ppa with the 4.15.0.46.67 kernel, no issues.

Or any 14.04/16.04 4.4.x kernel user can continue to use the previous 4.4.x kernel (4.4.0.142.148

---

### Post by nerv-agent on 2019-03-24
A quick recap of what happened was on that Friday night, I updated and got a bunch of errors.  

I restarted only to find that my wifi wasn't working.  After hours of scouring Google on a mobile device (very eye straining) I saw some websites mentioning installing the latest kernel to fix the issue. So I downloaded the ISO files on my cell phone, transferred the ISOs to my computer via USB link, and installed the kernel under the root account.  The problem still wasn't solved, so I kept searching and found the command line "rfkill unblock all". This restored the wifi.  

A few days later I tried to play RetroArch using the NVIDIA GPU, only to start getting the problems I mentioned before.  I did roll back to a 4.4 Kernel, but the NVIDIA GPU still couldn't be detected and the wifi got killed again, even after running "rfkill unblock all". So I had to revert back to the 5.0 kernel.

I'm stuck. The only solution I have is extreme: install Windows 7 on an external drive and use that temporarily while I nuke my current Ubuntu install, do a fresh reinstall of Ubuntu, then migrate back from Windows. And there is the possible problem that if I run Ubuntu updates during that process, the wifi and NVIDIA GPU could be rendered unusable again. An alternative to this extreme measure would be nice.

---

### Post by Autodave on 2019-03-24
When you first installed the Nvidia driver, where did you get it from?

---

### Post by nerv-agent on 2019-03-25
I usually install the NVIDIA drivers and updates from Ubuntu system updates.  NVIDIA 384 is also on my computer. I loaded it and got the same failtastic result.

---

### Post by nerv-agent on 2019-03-28
Because I'm out of ideas, if I upgrade from Ubuntu 16.04 LTS to 18.10, will my personal files and documents still be intact? Or will the upgrade wipe out everything?

---


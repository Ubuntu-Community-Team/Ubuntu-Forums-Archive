---
title: "Oversized Display Stuck"
date: 2021-01-11
forum: General Help
---

### Post by thusspokelong on 2021-01-11
Software: Ubuntu 20.04.1 LTS 
Hardware: MSI Laptop GT Series GT780DXR

Problem: Running fine for years, latest up date has made my display too large for the monitor. 

What I've Tried: Settings > Displays > Resolution. However, there is only one selection possible for Resolution 640x480 (4:3) so I cannot change it to anything else? Before this latest update I had a huge list of resolution options now just 640x480 (4:3). Changing fractional scaling on or off does nothing. 

Any help would be greatly appreciated. 

:)

**inxi -G**
Graphics:
  Device-1: NVIDIA GF114M [GeForce GTX 570M] 
  driver: N/A 
  Display: x11 server: X.Org 1.20.8 
  driver: fbdev,nouveau 
  unloaded: modesetting,vesa 
  resolution: 640x480~73Hz 
  OpenGL: 
  renderer: llvmpipe (LLVM 10.0.0 256 bits) 
  v: 3.3 Mesa 20.0.8

**uname -r **
5.8.0-36-generic

---

### Post by #&amp;thj^% on 2021-01-11
Please include this:
```
inxi -G
```
I'm guessing you jumped to kernel 5.8
```
uname -r
```

---

### Post by thusspokelong on 2021-01-11
Thanks!

Graphics:
  Device-1: NVIDIA GF114M [GeForce GTX 570M] 
  driver: N/A 
  Display: x11 server: X.Org 1.20.8 
  driver: fbdev,nouveau 
  unloaded: modesetting,vesa 
  resolution: 640x480~73Hz 
  OpenGL: 
  renderer: llvmpipe (LLVM 10.0.0 256 bits) 
  v: 3.3 Mesa 20.0.8

---

### Post by #&amp;thj^% on 2021-01-11
The one you forgot as well:
```
uname -r
```

---

### Post by thusspokelong on 2021-01-11
Sorry, thought that was your sig or something: 

uname -r 
5.8.0-36-generic

---

### Post by #&amp;thj^% on 2021-01-11
No Worries. :)
Yep "5.8.0-36-generic", it has some issues currently.
Could you as a test first, boot to an older kernel probably 5.4, and report back if this was better?

---

### Post by thusspokelong on 2021-01-11
> boot to an older kernel probably 5.4
Restarted, held shift, grub kernal advanced ubuntu selected older kernal 5.4 

Still all giant sized, still 640x480 (4:3) as the only Resolution option

---

### Post by #&amp;thj^% on 2021-01-11
Did you ever install any driver for nvidia chip?

---

### Post by thusspokelong on 2021-01-11
Not certain. Nothing recent.

---

### Post by thusspokelong on 2021-01-11
Just checked drivers. I did have an Nvidia driver installed. When I try and change it, it says "offline error cannot download change whilst offline (257)" or some such. Even though I am 1000% online and connected. Can browse. Can send email.

---

### Post by #&amp;thj^% on 2021-01-11
Starting to see breakage now with Nvidia as we speak....give me second to see if any relevant info comes in.
I'm assuming your still booted to kernel 5.4 if so stay there.

---

### Post by #&amp;thj^% on 2021-01-11
> **thusspokelong said:**
> Just checked drivers. I did have an Nvidia driver installed. When I try and change it, it says "offline error cannot download change whilst offline (257)" or some such. Even though I am 1000% online and connected. Can browse. Can send email.

Bingo....Thought so, please read and follow my previous post. :KS

---

### Post by thusspokelong on 2021-01-11
Still in kernal 5.4

---

### Post by #&amp;thj^% on 2021-01-11
This command will remove the proprietary Nvidia driver:
```

sudo dpkg -P $(dpkg -l | grep nvidia-driver | awk '{print $2}')
sudo apt autoremove
```
Then:
```
sudo apt install xserver-xorg-video-nouveau
```
it's probably already installed but for good measure we install again.
Now remember the the kernel this was done on and boot to that, for the reboot I'm asking you to do now. (Ready Go ;))

---

### Post by thusspokelong on 2021-01-11
Ran code. 
Errors Cannot remove that which is not installed
Restarted, used grub kernal 5.4 as before 
Display is still jumbo sized, still had nvidia installed even though code said it was not 
Cannot change driver, says offline

---

### Post by #&amp;thj^% on 2021-01-11
This is a stubborn one, we might have to repeat this again on kernel 5.8 "**says offline**"
This time when selecting kernel 5.4 just arrow down to it and hit key "e" will take you grub and the line that reads like
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"

```
Add this "**nogpumanager**" IE:
```
GRUB_CMDLINE_LINUX_DEFAULT="**[B]nogpumanager**[/B] quiet"
```
Then hit <F10> to resume. 
Now how is it.

---

### Post by thusspokelong on 2021-01-11
[work took over, will try this later tonight, thanks for the help!]

---

### Post by thusspokelong on 2021-01-12
1fallen,

Thanks for all the help. I tried to change the grub code or whatever as per your instructions but was unable to. Restarted into 5.8 recovery mode and that allowed me to to change drivers to default. Jumbo sized screen was now normal. But could no longer change drivers back to nvidia and without the nvidia drivers the visuals are poor, albeit functional. Friend demanded that that I switch to Pop OS so I'm gonna try that. I backup everything to an external harddrive so switching to a new OS is no biggie. 

You can consider this case closed. 

Best,
Thusspoke

---


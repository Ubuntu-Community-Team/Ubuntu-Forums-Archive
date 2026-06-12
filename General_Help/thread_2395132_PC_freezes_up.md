---
title: "PC freezes up?"
date: 2018-06-27
forum: General Help
---

### Post by dannyk2 on 2018-06-27
I have a fairly new desktop computer with 16GB of memory plus a 1TB hard drive and i'm running Ubuntu MATE 18.04, 64bit. My problem is that the PC regularly freezes up solid. I cannot even use the keyboard or the terminal when this happens. The only way i can do anything is to shut the computer down via the mains power supply and then restart the machine. Hope someone can help me out with this as i am not very tech savvy. Thanks all

---

### Post by NM5TF on 2018-06-27
when you say "freezes up" does your monitor also freeze with the screen tearing......everything is shrunk into a diagonal...

do you have an nvidia graphics card ???

can you post the output of this command:

```
inxi -G
```

you may need to install inxi first....the output should look something like this:  

```
[tommy@tommy ~]$ inxi -G
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: X.Org 1.20.0
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: N/A version: N/A

```

---

### Post by dannyk2 on 2018-06-27
Hi NM5TF
I've run the code ```
inxi -G
```
And this was the output:

Graphics:  Card: Intel HD Graphics 630
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version:

---

### Post by NM5TF on 2018-06-28
have you tried updating your display driver..... Display Server: X.Org 1.20.0 is the latest stable release....your's is older at 1.19.6....

you  might also try adding [COLOR="#FF0000"]nomodeset[/COLOR] to the linux kernel at boot time...do you know how to do this ???

my web research shows there were/are numerous problems with the Intel  HD Graphics 630 chipset.....

tommy

---

### Post by dannyk2 on 2018-06-28
Hi NM5TF  I shall try and update the latest display driver but as far as 'nomodeset' is concerned i haven't got a clue?

---

### Post by kazakore on 2018-06-28
Adding kernel options for boot:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

I've no idea where you would get Xorg 1.20 though.....

---

### Post by NM5TF on 2018-06-28
> **dannyk2 said:**
> Hi NM5TF  I shall try and update the latest display driver but as far as 'nomodeset' is concerned i haven't got a clue?

I just PM'd you with details...

tommy

---

### Post by dannyk2 on 2018-06-28
Hi NM5TF  I did as you suggested and when the "GNU GRUB" menu appeared on the screen i scrolled down to the "Linux" line and at the end of this line was, "quiet splash $vt_handoff" so after "$vt_handoff" i pressed SPACE and then typed nomodeset then pressed the F10 key to boot the system using the parameters i had just added. I rebooted the PC but the mouse seemed to be sticking and was really awkward to use. The tool bar at the top of the screen was really slow to appear. So i rebooted the machine and everything seems to be back to normal and the machine has not stopped and freezed up yet!  Shall just have to carry on until the machine freezes up again.  Just like to say a big thank you for all the help and Advice

---


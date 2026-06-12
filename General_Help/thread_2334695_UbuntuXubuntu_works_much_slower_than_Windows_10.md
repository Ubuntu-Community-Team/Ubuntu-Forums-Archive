---
title: "Ubuntu/Xubuntu works much slower than Windows 10"
date: 2016-08-21
forum: General Help
---

### Post by shadowatyy on 2016-08-21
I've installed Windows 10 and Ubuntu 16.04 (also tried Xubuntu 16.04/14.04) on my brand new laptop i5 6200u/8gb/gt940m/240gb. I have problem with ubuntu performance, which doesn't occur on windows, where everything i've tried works just fine. On ubuntu I feel lagging when just typing - e. g. in codeblocks or in chromium.

 In gtkperf i receive very different results - once it's like 2,5s and next time 20-30s (!).

 I tried reinstalling ubuntu couple of times, with swap and without it. Also on empty ssd - with no effect at all. Memtest - no errors, ssd benchmarks - fine, cpu benchmarks - common results (benchmarking under windows).

I wonder if someone can tell me what causes my problems - thanks in advance!

---

### Post by fizikz on 2016-08-21
Are the graphics drivers installed?

---

### Post by shadowatyy on 2016-08-21
Yeah, i tried both proprietary and some downloaded from nvidia website. Also - i tried running laptop with lower resolution - nothing's changed.

---

### Post by Geoffrey_Arndt on 2016-08-22
Can you provide "detailed" description of your video install steps?   Especially the initial install of proprietary drivers - 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/](http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/)

---

### Post by shadowatyy on 2016-08-22
To be sure i did everything again, reinstalled xubuntu and installed driver using instructions from help.ubuntu.com. But after that, i tried to open nvidia settings:

```

 sudo nvidia-settings
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.


```

And when i open it there's no option to switch between graphics.

Also:

```
 sudo nvidia-detector
none

```

Update: Now i got

```


** Message: PRIME: is it supported? yes



```

and i see PRIME-profiles in nvidia settings but when i change it and reboot it comes back to intel.

---

### Post by Geoffrey_Arndt on 2016-08-24
Have you tried this to do the initial installs correctly, and then to switch between gpu drivers . . ?

[http://ubuntuhandbook.org/index.php/2016/04/switch-intel-nvidia-graphics-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/04/switch-intel-nvidia-graphics-ubuntu-16-04/)

---

### Post by T2uiYKb7 on 2016-08-25
**@[[COLOR=#000000]shadowatyy[/COLOR]]("https://ubuntuforums.org/member.php?u=2041718")**

What's the performance like without the proprietary Nvidia drivers?

I understand demanding games need those drivers but can you just use the normal built in drivers and see how the performance is for normal non-gaming stuff?

Just so we can eliminate any other possibility.

It's not ideal but outside of gaming the kernel driver should run everything quickly (including HD video.)
[B]
I don't want to sound like a Linux fan boy but this genuinely is very unusual,[/B] I've run Xubuntu on ancient, low spec machines and had no lag while typing and doing basic stuff.

---


---
title: "inxi not detecting monitor resolution correctly when scaling factor applied"
date: 2017-12-01
forum: General Help
---

### Post by Nick Payne on 2017-12-01
I'm running 17.10 with Gnome desktop and Wayland. I have two 80cm monitors, a Dell U3011 @2560x1600 resolution and 100% scaling, and an Eizo EV3237  @3840x2160 resolution and 150% scaling (so that UI elements are approximately the same size on both monitors). When I run inxi -F I see:

```
nick@Nick-Ubuntu:~$ inxi -F
System:    Host: Nick-Ubuntu Kernel: 4.14.2-041402-generic x86_64 bits: 64 Desktop: Gnome 3.26.1
           Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: ASUSTeK model: P9X79 LE v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 4801 date: 07/24/2014
CPU:       Quad core Intel Core i7-3820 (-HT-MCP-) cache: 10240 KB
           clock speeds: max: 3800 MHz 1: 3602 MHz 2: 3602 MHz 3: 3602 MHz 4: 3602 MHz 5: 3602 MHz 6: 3602 MHz
           7: 3602 MHz 8: 3602 MHz
Graphics:  Card: NVIDIA GP107GL [Quadro P1000]
           Display Server: wayland (X.Org 1.19.5 ) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 2560x1600@59.94hz, 2560x1440@59.96hz
           OpenGL: renderer: NV137 version: 4.3 Mesa 17.2.2
```

inxi is showing the Eizo resolution as 2560x1440, which happens to be the actual resolution or 3840x2160 divided by the scaling factor of 1.5.

---

### Post by again? on 2017-12-01
inxi is just a bash script which may not have Wayland support yet.
Does it work in the xorg session.
You can download and test the latest github version.
[https://github.com/smxi/inxi](https://github.com/smxi/inxi)
or open an issue.

Have a read of this post from a few months ago.
[https://techpatterns.com/forums/about2590.html](https://techpatterns.com/forums/about2590.html)

---

### Post by user232 on 2017-12-02
inxi is showing the data correctly. It is showing the x screen display dimensions, not the physical screen pixel dimensions. I don't believe, though I'm not certain, that information is even available using the various screen dimension tools inxi uses. So basically your issue is noting that inxi -G is working correctly, as intended.   

 There's no wayland issue, that is also working correctly. Though it should be noted that it's still early days in Wayland so there are not very many wayland specific reporting tools, but those will appear over time once Wayland stops piggybacking on Xorg.   

 The language a program is written in has nothing to do with anything. Technically speaking, inxi is actually Gawk wrapped by Bash, and certainly has nothing to do with Xorg tools reporting what inxi is then passing along correctly to the user.  

 An appropriate issue would be for example on inxi github to see if there is any way to access the technical literal pixel dimensions of the output. My guess is that there is not, but that is why it would not be a bad issue to post. Note that you'd have to present data showing that in fact, that information is available, in for example glxinfo or various other things, like xrandr output, etc. Obviously, if the information isn't available, inxi can't supply it. It would be up to the issue poster to present data that shows this can be done, using various tools available, like glxinfo, xrandr, etc.

---

### Post by again? on 2017-12-02
> **user232 said:**
> inxi is showing the data correctly. It is showing the x screen display dimensions, not the physical screen pixel dimensions. I don't believe, though I'm not certain, that information is even available using the various screen dimension tools inxi uses. So basically your issue is noting that inxi -G is working correctly, as intended.   

 There's no wayland issue, that is also working correctly. Though it should be noted that it's still early days in Wayland so there are not very many wayland specific reporting tools, but those will appear over time once Wayland stops piggybacking on Xorg.   

 The language a program is written in has nothing to do with anything. Technically speaking, inxi is actually Gawk wrapped by Bash, and certainly has nothing to do with Xorg tools reporting what inxi is then passing along correctly to the user.  

 An appropriate issue would be for example on inxi github to see if there is any way to access the technical literal pixel dimensions of the output. My guess is that there is not, but that is why it would not be a bad issue to post. Note that you'd have to present data showing that in fact, that information is available, in for example glxinfo or various other things, like xrandr output, etc. Obviously, if the information isn't available, inxi can't supply it. It would be up to the issue poster to present data that shows this can be done, using various tools available, like glxinfo, xrandr, etc.

Thought it was worthwhile mentioning it was a single bash script because then it makes it a trivial matter to try the github version, I was not demeaning the language it is written in. 
You connected with inxi in any way?

---

### Post by vasa1 on 2017-12-02
> **guber2 said:**
> ...
You connected with inxi in any way?
And if you are, thanks for inxi! It's a great tool :)

---


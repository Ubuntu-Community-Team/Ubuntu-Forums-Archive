---
title: "How do I make my screen full screen"
date: 2012-11-01
forum: General Help
---

### Post by mschultz0009 on 2012-11-01
Hello All, just downloaded Ubuntu and have no idea how to make it full screen like windows. Thanks Mike

---

### Post by GreatDanton on 2012-11-01
1. You can double click on the top bar of the window and the application will become full screen.

2. Press f11

Hope this helps.

---

### Post by nothingspecial on 2012-11-01
F11

---

### Post by dannyboy79 on 2012-11-01
could you elaborate more. DO you mean you have a bad resolution? are you askling how to make a window fullscreen? We need specifics.

Could you put this command into a terminal and post back what it reuturns, it will tell your video card

```
lspci -v
```

---

### Post by mschultz0009 on 2012-11-01
I think I need to rephrase my question. how do I get rid of other windows? my browser is on the left and I have a blank window or the right and a big empty same at the bottom. Just want my browser to fill entire screen. Thanks

---

### Post by dannyboy79 on 2012-11-01
the little box in one of the top corners that has 2 little boxes in it, or you can double click the top bar and it should make that window full screen

---

### Post by mschultz0009 on 2012-11-02
Dumd ? how do I get to the terminal. I was trying to find it so i could change some settings on my own, but no luck

---

### Post by Champlin93 on 2012-11-02
What distribution are you using? (Ubuntu, Xubuntu, etc). 
We are really having trouble figuring out what you are asking. If you mean you want to maximize a window then it would be the middle of the three buttons on the top left (or top right depending on your distribution or desktop environment). If you mean fullscreen then F11 is your answer.

---

### Post by Wim Sturkenboom on 2012-11-02
> **mschultz0009 said:**
> I think I need to rephrase my question. how do I get rid of other windows? my browser is on the left and I have a blank window or the right and a big empty same at the bottom. Just want my browser to fill entire screen. Thanks
Just guessing that it's a resolution issue. Can you describe more accurately what you see? Is the bar in the top over the full width of the screen? Or is is only going e.g. halfway? I think it's the latter. And you can not move your browser window over the blank area at the right or at the bottom without it disappearing.

If so, please specify your hardware, specifically the video chip set and the monitor (make and model). If this is a laptop, make and model of the laptop instead of the monitor.

---

### Post by mschultz0009 on 2012-11-02
Subsystem: Acer Incorporated [ALI] Device 0266
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fc500000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

0b:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device 0266
    Flags: fast devsel, IRQ 19
    Memory at fc501000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

0b:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
    Subsystem: Acer Incorporated [ALI] Device 0266
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fc502000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

mike@mike-Aspire-Z5600:~$

---

### Post by mschultz0009 on 2012-11-02
> **Champlin93 said:**
> What distribution are you using? (Ubuntu, Xubuntu, etc). 
We are really having trouble figuring out what you are asking. If you mean you want to maximize a window then it would be the middle of the three buttons on the top left (or top right depending on your distribution or desktop environment). If you mean fullscreen then F11 is your answer.


I'm going to try and put up a pix, What I'm asking I want the browser to fill my entire screen. f11 won't do it . I can't even move my mouse all the way down the screen. I have a blank screen at the bottom and another at the right side.

---

### Post by mschultz0009 on 2012-11-02
That's it... only going halfway Blank screen at bottom and at right can't move it or make it bigger.

---

### Post by mschultz0009 on 2012-11-02
Here is a pix I think.

---

### Post by mschultz0009 on 2012-11-02
:confused:help

---

### Post by dannyboy79 on 2012-11-02
there's no picture attached. host it at imagshack or if you have a gmail account, create a picasa web album open to the public and post it there.

Im wondering if you have an overscan issue and you don't have the correct screen resolution set.

---

### Post by mschultz0009 on 2012-11-02
> **dannyboy79 said:**
> there's no picture attached. host it at imagshack or if you have a gmail account, create a picasa web album open to the public and post it there.

Im wondering if you have an overscan issue and you don't have the correct screen resolution set.


No picture. I see it in post number 14. I can email it or try like you said to do

---

### Post by mschultz0009 on 2012-11-02
> **mschultz0009 said:**
> No picture. I see it in post number 14. I can email it or try like you said to do


I put it on picasa.    [https://picasaweb.google.com/110755606557810958313](https://picasaweb.google.com/110755606557810958313) never used it before hope this works.

---

### Post by dannyboy79 on 2012-11-02
double click the top bar, then tell me what happens

---

### Post by mschultz0009 on 2012-11-02
> **dannyboy79 said:**
> double click the top bar, then tell me what happens

Nothing

---

### Post by mschultz0009 on 2012-11-02
I Got it, I went to display for the 100th time and clicked on monitor image and made it bigger and that was it.  Thanks for all your help.

---

### Post by dannyboy79 on 2012-11-03
whats your screen resolution set to?

---


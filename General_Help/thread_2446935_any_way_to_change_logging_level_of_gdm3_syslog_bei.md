---
title: "any way to change logging level of gdm3? syslog being filled with junk"
date: 2020-07-09
forum: General Help
---

### Post by Ranbunta_Bantubunt on 2020-07-09
Howdy,

When i look in /var/log/syslog, the (literal) vast majority of text in there consists of repeated outputting of the state of the NVIDIA graphics driver, 24/7/365.24. 
I am getting the below output, several times per minute, all the time. Makes it hard to find other things in syslog and also I wonder even about the effect on the life of the SSD.

I am using ubuntu 20.04, running cinnamon as my desktop manager. I am  using the recommended NVIDIA provided driver and am not having any  problems with GPU/display.

Can anyone help me change the logging level so syslog doesnt get so polluted? 

Thanks for any ideas

Rabu


```
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): connected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): 600.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: 165.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): connected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): 600.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: 165.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-0: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): connected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): AOC 2367 (DFP-2): 600.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-3: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-4: 165.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: disconnected
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0): DFP-5: 2660.0 MHz maximum pixel clock
7/9/20 11:49 AM    /usr/lib/gdm3/gdm-x-session    (--) NVIDIA(GPU-0):
```

---

### Post by wildmanne39 on 2020-07-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Ranbunta_Bantubunt on 2020-07-10
Thank you for the tip.

---

### Post by Ranbunta_Bantubunt on 2020-07-22
Any possibility anyone might be able to help with this? :)

---

### Post by ihor3 on 2020-09-14
I have this issue too, different monitor, but same issue

---


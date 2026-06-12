---
title: "window resize issues"
date: 2021-02-06
forum: General Help
---

### Post by Unguidedone on 2021-02-06
I added more monitors to my computer

Main screen hides a bit of the window.  Screens 2 3 4 are fine when resizing.

screen shot of issue:
[URL="https://imgur.com/a/9hhzMkY"]https://imgur.com/a/9hhzMkY

[IMG]https://i.imgur.com/G9Rv7fu.png[/IMG][/URL]

I rebooted but nothing.

---

### Post by Unguidedone on 2021-02-08
???? any help

---

### Post by Unguidedone on 2021-03-23
i still have this issue

---

### Post by Unguidedone on 2021-03-25
any ideas on how to fix this

---

### Post by Unguidedone on 2021-06-03
i still have this issue what do i do?

---

### Post by Unguidedone on 2021-07-06
i went from 3 monitors to 4 now im having the same issues where the window overlay is actually higher then gnome fallback top bar.

what i know is it has something to do with screen positions other then that idk.

anyone know how i can work through this issue?


this issue only applies to the main window that has gnome panel.  all other monitors are not effected...

---

### Post by ActionParsnip on 2021-07-07
Is the top bar pinned or something like that?
Do you have extensions that would do this?
[https://www.maketecheasier.com/hide-top-bar-ubuntu/](https://www.maketecheasier.com/hide-top-bar-ubuntu/)

---

### Post by coley9225 on 2021-07-07
When I click the link, it fails to fully load,so I going on just the verbal description of your issue. I use a laptop with a 40 inch 1080p tv as a second monitor. If I use the suggested resolution ( 1920 x 1080) I get full windows cropped as you describe. To work around this I reduced my resolution to 1680 x 1050 ( I dropped by 1 notch) and everything is correct. Try reducing your resolution by 1 position and see if that helps. Good luck.

---

### Post by Unguidedone on 2021-07-09
no extensions but it has to do with scaling and gnome-pannel just changing itself when i put the 4th monitor.

it was odd i had 3 monitors and no problem, then i put the 4th and it came back again.  Zero issues when i had 2 monitors it worked perfect.


i did find an error the monitors refresh rate was wrong changed 60->75, all monitors are the same size.  change the scale of the monitors to no effect :(

[IMG]https://i.imgur.com/G9Rv7fu.png[/IMG]

---

### Post by Unguidedone on 2021-07-11
throw me a bone here its still not fixed

---

### Post by him610 on 2021-07-11
I only use one monitor that works great, and displays to my satisfaction; therefore, I am not the one to give you advice on configuring four, three, or even two monitors.
With that said, please show the results between the code tags, of ...
```

inxi -Fxz

```
What make & model of monitors are you using?
How is each monitor connected to your system? VGA, DVD-D, DVD-I, HDMI, displayPort? Are there any adapters in use?

---

### Post by Unguidedone on 2021-07-12
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.8 ) driver: amdgpu
           Resolution: 1920x1080@74.99hz, 1920x1080@60.00hz, 1920x1080@60.00hz, 1920x1080@74.99hz
           OpenGL: renderer: Radeon RX 570 Series (POLARIS10, DRM 3.35.0, 5.4.0-77-generic, LLVM 10.0.0)
           version: 4.6 Mesa 20.0.8 Direct Render: Yes

i have 1 hdmi and 3 display ports

i have 4 asus 22 inch monitors

Asus VP228QG 21.5&#8221; Full HD 1920x1080 1ms DP HDMI VGA Adaptive Sync *2

ASUS VP229Q 21.5&#8221; Monitor, 1080P Full HD, 75Hz, IPS, FreeSync/Adaptive-Sync *2

i tried to get the exact type but it was no longer on amazon fml

so 2 monitors are 75hz / 2 are 60 hz

---

### Post by dragonfly41 on 2021-07-12
Here is a bone to gnaw on ...

[https://sarata.com/manpages/x-tile.1.html](https://sarata.com/manpages/x-tile.1.html)

   **[http://www.giuspen.com/x-tile](http://www.giuspen.com/x-tile)**

---

### Post by Unguidedone on 2021-07-15
thanks but its a bandaid and does not fix the underlying problem

---


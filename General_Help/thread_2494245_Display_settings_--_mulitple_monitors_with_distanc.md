---
title: "Display settings -- mulitple monitors with distance"
date: 2024-01-09
forum: General Help
---

### Post by bme186 on 2024-01-09
Hi guys


I have three monitors that are connected to the same desktop (GPU)  but each of them is a separate location  (each monitor is in a separate room). When using any monitor, the other two are switched off from the display settings.  My question is "how to choose on which monitor the window of the display sitting will show up?" as the unpredictability-inconsistency causes inconvenience. 

For example, suppose I am working on monitor '1' (the other two monitors are on), I choose to turn monitor 1 off and turn monitor 2 on. When calling the display settings, it is hard to anticipate on which of the three monitors exactly the display settings will show up  .. it is not necessarily neither the monitor on which the pointer the triggered opening the display sitting nor is it the main monitor ..  I am not sure if there is a rule of thumb to decide where the display settings window will show up or is it totally arbitrary (so perhaps to request a new feature)

Any idea?

---

### Post by guiverc on 2024-01-09
You've not provided the basic details of your *software stack*... ie. what OS & release are you using? and what desktop/wm may also be helpful.

I have five monitors connected to this box, and often turn monitors off (*one is off now*) but that doesn't impact my alignment (*nor if they were all displaying the same image, which wouldn't work for me*).

 I am using a DM that shows the greeter on all displays (*some DMs that don't do this can be annoying when monitors are often off*). FYI: My monitors are all in the same room, but its software config that matters, and the OS, release & software choices are what I consider matters; though if connections are often *broken* (ie. disconnected), that can make the setup far more complex.

---

### Post by bme186 on 2024-01-09
> **guiverc said:**
> You've not provided the basic details of your *software stack*... ie. what OS & release are you using? and what desktop/wm may also be helpful.

I have five monitors connected to this box, and often turn monitors off (*one is off now*) but that doesn't impact my alignment (*nor if they were all displaying the same image, which wouldn't work for me*).

 I am using a DM that shows the greeter on all displays (*some DMs that don't do this can be annoying when monitors are often off*). FYI: My monitors are all in the same room, but its the software config that matters, and the OS, release & software choices are what I consider matters; though if connections are often *broken* (ie. disconnected), that can make the setup far more complex.

Hi, thank you very much. I am using Ubuntu 22.04 Desktop .. but I think that issue exists in all other earlier editions. I am using the default Display settings. I am Not talking turning them off physically (like pressing the power button of the monitor). Rather, I am talking about turning the monitor off from the display settings window (where you can find a toggle button that allows switching on and off the screen),

Still, the main issue is how to predict on which monitor the display settings window will show up. It sounds to me that Ubuntu shows them in an arbitrary way and it was not designed for such use cases (like having two or more monitors connected to the same computer and there is a distance between them).. But one could think of many use cases .. like someone is working on the monitor and using the other to show their children a cartoon show they choose for them .. then monitors can be separated from each other .. it does not make sense not to know exactly where the display sitting window will appear (unless you want your baby child start crying when display sittings interrupt their show and appears on their monitor .. and you can not calm them down by telling them  "sudo stop crying" :))

---

### Post by #&amp;thj^% on 2024-01-09
For me the Monitor I click the Mouse on display's my settings.
With the Key Combo [Super +p]
Xubuntu XFCE4

---

### Post by MAFoElffen on 2024-01-09
Well, what you described is more of a reverse KVM switch, where you are using one computer, but switching to various displays.

The factors that brings up that are challenging... The resolution needs to be set manually, because it needs to be set to something that all have, but overriding the EDID...

Then there is a factor of cable distance. Max length of HDMI is 50 feet. Max length of DVI cable is 9 feet. VGA cable max length of 150 feet. (You said thy wer is different rooms...)

Mine, how I handle that, is much different. I have 2 main work-horses that just sit there running with their displays turned off. They are both running KVM.

From my laptop: 
I can ssh into either (which I do a lot.) I can run VM's from either. If I wanted to run VNC on ether (do not need to.)

---


---
title: "Compiz / Screensaver problems"
date: 2008-05-02
forum: General Help
---

### Post by trendal.toews on 2008-05-02
Compiz doesn't work and only the basic (low graphics) screen savers work.  Wondering if this could be due to flaky video driver install on the fresh Hardy Heron install?  Or not a good enough video card?

Trying to find my graphics card info but I don't seem to have (Hardware Information) under System->Preferences->Hardware Information. Am I just missing it or is there another way to get there?

---

### Post by NightwishFan on 2008-05-02
Does it have any restricted drivers availiable? System -> Administration -> Hardware Drivers. If so install them from there and reboot then see if anything works.

---

### Post by trendal.toews on 2008-05-02
There is restricted drivers available. When I install them and reboot on startup I get a window that says ( Ubuntu is running in low-graphics mode. Your screen and graphics card could not be detected. You must configure them yourself ) So I check the generic screen and then select one of the resolutions and boot up.  But then my screen resolution comes up as 800x600. In system-preferences-screen resolutions there is only one other option (640x480). :mad:

---

### Post by NightwishFan on 2008-05-02
Try this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the best you can, if you are unsure use the default.

---

### Post by trendal.toews on 2008-05-02
If I reboot again it goes to the better resolution 1280x1024 but the proprietary driver in Hardware Drivers goes back to the (not in use) status.  And the compiz and screensaver still doesn't work.

Sorry wrote this before seeing that last post will give it a try

---

### Post by NightwishFan on 2008-05-02
oh ok when you try that make sure the drivers are enabled

:mad:

That worked for me before. Try this:
```
sudo apt-get update
```

Then reboot, and then try to reenable graphics and then reboot again if the same thing happens then it is not a repository error. If any error messages come up please post them here.

---

### Post by trendal.toews on 2008-05-02
> **NightwishFan said:**
> Try this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the best you can, if you are unsure use the default.

Thank you for the help... but no success yet.  Could it be my graphics card isn't good enough to run compiz or some of the screensavers?  Like I said I can't find the hardware tab under system-preferences. So I am not sure what card I got.

Ok let me try it with the drivers enabled

---

### Post by NightwishFan on 2008-05-02
Try this:
```
sudo apt-get install hardinfo
```
It will show up in: System -> Administration -> (i think) system information and benchmarking tool

---

### Post by trendal.toews on 2008-05-02
Oops I forgot. I am running on a KVM and I had to hook my moniter up direct to set it up the first time so maybe I need to do that again to fix this problem.

---

### Post by NightwishFan on 2008-05-02
Ok keep me posted I will try to help where I can.

May the force be with you.

---

### Post by trendal.toews on 2008-05-02
> **NightwishFan said:**
> Try this:
```
sudo apt-get install hardinfo
```
It will show up in: System -> Administration -> (i think) system information and benchmarking tool

Okay, that worked but the problem has degenerated to this...  8.04 won't recognize/detect my graphics card (nvidea geforce4 mx4000) nor my moniter (Acer AL1706).  
The proprietary drivers in Hardware Drivers are enabled but that hasn't seemed to change anything.
I am not using the KVM anymore, hooked up direct.

I guess I will hit the skids for tonight. Be back on Monday:mad:

Thank you much for your help.

---

### Post by NightwishFan on 2008-05-02
No problem, I will ask someone experienced to review and help some more.

---

### Post by trendal.toews on 2008-05-05
Okay, back on Monday. Basically it won't recognize my hardware. I have to manually tell it what graphics card and monitor I am using by choosing from the list it gives me at start up in the "Ubuntu is running in low graphics mode / configure" menu. Then the resolution is great but compiz and the screensavers don't work.

Thank you for any help I get.=D>

---

### Post by trendal.toews on 2008-05-16
Okay, its been some time since I wrote here but I have fixed two of these same problems since then. 

The problem lies in trying to install Ubuntu through a KVM. Hooking up monitor direct fixed all problems.  Simple. Then I just let Ubuntu tell me what drivers it wanted and we were good to go.

Thanks for helping anyway.


Edit: Turns out I had a flaky screen also. New screen works through kvm so not sure if kvm messes it up or not.

---


---
title: "Keyboard/mouse issue which has to be solved as gaming comes to Ubuntu"
date: 2012-11-07
forum: General Help
---

### Post by Howard Hatecraft on 2012-11-07
Hello!

I turned to you some months ago for having a mouse/keyboard problem on my Thinkpad T420. As today Steam for Ubuntu was launched for beta-testers, I want to have this problem solved asap. When I type on the keyboard, I cannot move the mouse for, well, half a second.

I'm pretty sure it has something to do with my tlp-usblist output concerning my mouse:

Bus 002 Device 004 ID 046d:c01d control = on,   autosuspend_delay_ms =  2000 -- Logitech, Inc. MX510 Optical Mouse (usbhid)

Every other device is on "auto" instead of "on". I cannot find a way to turn the control to "auto" here.

People, I really need this issue to be solved!

---

### Post by linrunner on 2012-11-10
Hi,

I'm pretty shure this is *not* the cause of your problem.

Do you  observe the same symptom outside the steam application, i.e. on the desktop or in a terminal?

Background: many mice do not wake up properly when moved while the device is powered down by USB autosuspend, so by design TLP disables USB auto suspend for *all* input devices:  
[LIST]
[*]*control = on, autosuspend_delay_ms =  2000* : autosuspend disabled, device stays powered on all the time &#8211; btw: this is the kernel default when TLP is not installed
[*]*control = auto, autosuspend_delay_ms =  2000* : autosuspend enabled, device powers down after 2 secs (= 2000 ms) of inactivity
[/LIST]
ps. I'm the developer of TLP.

---

### Post by 2F4U on 2012-11-10
I am also pretty sure this has nothing to do with TLP. I am running it on several machines with the exact same setting without any issues. You should rather verify that the setting to disable the mouse while typing is not active.

---

### Post by Howard Hatecraft on 2012-11-10
Thanks for your replies. I am not only observing the problem in steam, rather everywhere (desktop, terminal). It seems that the mouse is disabled while typing, but if I turn the setting off (on and off on and off...), nothing happens. My touchpad on the other hand is not responding to the settings at all. So if I disable the touchpad while typing, neither my touchpad nor my mouse is responding to the change of setting. The touchpad is always working while typing, my mouse is always stuck.

---

### Post by linrunner on 2012-11-10
Which Ubuntu version / desktop entvironment do you use? Did you check with a Live CD?

---

### Post by Howard Hatecraft on 2012-11-11
i m using the latest ubuntu version 12.10 on the unity desktop. when booting from the usb-stick i don't have the problem, i can type and move my mouse..

---

### Post by linrunner on 2012-11-12
Did you try to boot with previous kernels via the Grub menu?

---

### Post by Howard Hatecraft on 2012-11-12
yes i did. smells like a fresh set up here

---

### Post by linrunner on 2012-11-13
I do not disagree .

---


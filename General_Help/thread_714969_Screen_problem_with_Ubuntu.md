---
title: "Screen problem with Ubuntu"
date: 2008-03-04
forum: General Help
---

### Post by DeliriousNor on 2008-03-04
Hi! I am experiencing a problem with my screen while running Ubuntu. I have a dualscreen set-up with my Thinkpad x41 docked and connected to a samsung syncmaster 226bw with the resolution 1680x1050. I seem to be having a problem with the samsung screen. Allthough it says that it is actually running on the correct resolution the screen is somewhat blurry and unclear.

I have heared that are a problem with the current X.org (I'm talking about Ubuntu 7.10) and that it has a certain problem conncerning screen output via VGA to a widescreen?

Is there anyway to fix this in Ubuntu 7.10? Or should I perhaps switch to 7.04? I know it doesn't support dualscreen set-ups, but I don't really need to use more than one screen at one. Another possibility could be to try the latest alpha of the 8.04 which contains the X.org 7.3, however I am quite sure that it is not yet stable enough for normal use.

Hope someone can help her!:)[


**Edit:** I also took a screenshot when using the LiveCD. Even though it looks quite nice here, it feel blurry compared to my laptopscreen and to my other screen when running windows.

---

### Post by cmnorton on 2008-03-05
What exactly are the problems?

Does this Thinkpad have advanced graphics (like 3D)?

I have a Thinkpad T61 in a KVM environment, but even straight output to a monitor had troubles. Eventually, I went to restricted drivers manager, de-selected my nvidia driver, and was able to get a perfectly good resolution for my T61p. I am just not using the advanced graphics.

Thinkpad Support told me I had to define two monitors, but the second monitor I tried to define never looked like it was live. I think this has to do with how Thinkpads output, because even in VGA+LCI mode, my laptop screen is always blank when my KVM monitor is attached.

---

### Post by DeliriousNor on 2008-03-05
As I said earlier it seems like the screen is quite unclear and blurry. Allthough it says it puts out 1680x1050, it is ALOT of difference between the laptopscreen which is totally perfect and the external screen.

As for the Thinkpad I cannot say that it has advanced graphics. The grafic card is a intel915, I do not know if that will help or not.

Still hoping somebody can help me out here:)

---

### Post by cmnorton on 2008-03-05
Does the restricted device manager indicate a specialized driver is loaded?

You may have to reconfigure X, but I don't even know where to begin on that subject. 

What is the native setting of your monitor? Maybe the monitor does not like the display configuration.

---


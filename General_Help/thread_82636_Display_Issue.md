---
title: "Display Issue"
date: 2005-10-26
forum: General Help
---

### Post by Sivel on 2005-10-26
I have an Inspiron 1100 notebook.

I just installed Ubuntu 5.10 on it but I cannot figure out how to get the display to fill the entire screen.  I have about a 2-3 inch black border all the way around the display.  In the screen resolution properties I only have 640x480 and I have verified that I have other resolutions configured in xorg.conf such as 1280x1024 1024x768 and so on.

I am sure this is very easy to fix but I am not very familiar with configuring the display properties of linux.  I normally configure Linux servers with no care with what the display looks like.

Anyone have any ideas?

---

### Post by mykey on 2005-10-27
just put the resolution of your screen in the appropriate section in xorg.conf e.g. 720x576 or 768x576 together with the ones already ion there - restart x and you should be able to choose from 'System' -> 'Preferences' -> 'Screen Resolution'

---

### Post by Sivel on 2005-10-27
Nope that didn't resolve the problem.  It appears as though it just couldn't handle higher resolutions at higher bit depths.  I lowered it to 8 and now I can adjust the resolution up to 1024x768 and it fills the whole screen.  Just the video quality is really sucky due to the low number of colors.

---

### Post by mykey on 2005-10-28
then you should look for a modified driver for your graphics card

---

### Post by bionnaki on 2005-10-28
I know my screen gets all weird after a fresh install of any linux distro. I have a button my monitor called "auto" that sets everything correct. do you have any options of the kind?

---


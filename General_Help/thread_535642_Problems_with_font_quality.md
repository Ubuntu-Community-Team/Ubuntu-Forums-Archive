---
title: "Problems with font quality"
date: 2007-08-26
forum: General Help
---

### Post by sml on 2007-08-26
Over the past 6 years I have tried basically every linux distribution, as well as Windows and OS X.

Ubuntu & Kubuntu clearly have the worst fonts in the world. I have searched the ubuntu forums and web and found a few threads for making improvements but they are still shocking.

The distro with the best fonts would be Arch Linux. In fact, they are basically all pretty good except for Ubuntu / Kubuntu.

How can such a popular distro continue to have terrible fonts? The threads in the ubuntu forums go back for years and still no improvements have been made to Ubuntu / Kubuntu.

---

### Post by wirelessmonkey on 2007-08-26
I'm not sure what's up on your system, but my fonts are every bit as clear in Kubuntu Feisty as in any other OS.

---

### Post by fragos on 2007-08-26
> **sml said:**
> Over the past 6 years I have tried basically every linux distribution, as well as Windows and OS X.

Ubuntu & Kubuntu clearly have the worst fonts in the world. I have searched the ubuntu forums and web and found a few threads for making improvements but they are still shocking.

The distro with the best fonts would be Arch Linux. In fact, they are basically all pretty good except for Ubuntu / Kubuntu.

How can such a popular distro continue to have terrible fonts? The threads in the ubuntu forums go back for years and still no improvements have been made to Ubuntu / Kubuntu.
There have been some issues with OpenOffice and fonts in the past.  Have you tried using other fonts like the DejaVu set that come with Ubuntu?  That's what I use and the fonts are displayed in high quality.

---

### Post by steveneddy on 2007-08-26
I installed msttcorefonts and some other ones that I like and it looks great to me.

---

### Post by fjgaude on 2007-08-26
Just what is it you find wrong with the fonts supplied with Ubuntu? I'm a graphic designer and find nothing wrong with any of the fonts. I use three different screens, 1280x1024, 1680x1050, and 1600x1200 dpi, and they all show well, as they should with the free fonts, as do about 500 high-priced Adobe, etc., ones.

frank

---

### Post by Steveway on 2007-08-26
I use Red-hats Liberation Fonts.
Those are pretty awesome and some of the best free fonts around.

---

### Post by sml on 2007-08-27
That's odd. I thought most people were experiencing problems.

I have tried attaching a screenshot capture file. Hopefully the quality of the screenshot demonstrates the problem.

There is nothing really special with my notebook. An intel 915 board, nvidia graphics and using nvidia driver. External LCD running at native resolution 1680x1050. Have tried three or four of the solutions in the other threads .. installed a bunch of new fonts, tried adjusting all the different 'smoothing' effects both in the desktop manager and nvidia graphics settings, tried the fontconfig changes, etc.

---

### Post by sml on 2007-08-31
Solved.

The native resolution of my LCD is 1680x1050.

For some reason, using nvidia-settings and specifying 1680x1050 caused poor font & image quality.

Using nvidia-settings and setting to AUTO for the resolution resulted, still displayed at 1680x1050, but for some reason is much clearer and as expected.

I dont understand the reason but it is solved at least!

---


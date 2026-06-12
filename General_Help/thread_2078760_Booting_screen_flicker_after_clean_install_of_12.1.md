---
title: "Booting screen flicker after clean install of 12.10 on Dell Inspiron 1525"
date: 2012-10-31
forum: General Help
---

### Post by Azhar Ebrahim on 2012-10-31
I just installed Ubuntu 12.10 on my Dell inspiron 1525 which  was previously running on windows 7. During booting, immediately after  the purple screen, my screen flickers like crazy (kind of switching  between the bootlogo screen and a text screen). Sometimes, I am able to  reach the ubuntu desktop, sometimes I dont.
  After this issue, I used a program called Xdiagnose and checked the options namely:
  Disable bootloader graphics
  Disable VESA framebuffer driver
  Disable PAT memory
  After that, the bootlogo screen was not appearing and instead a text  based screen was appearing during next two startup. ( the text based  screen used to have someting like this [[[B^[[[B^[[[B^[[[B^.............  this runs for 3-4 lines )
  Upon third startup, the screen flicker has resumed. This is the 3rd  time I am reinstalling Ubuntu 12.10. I am an absolute beginner to linux.  Step by step suggestions are welcome as I am not aware about linux or  ubuntu terminologies.
  My screen looks somewhat like this fellows screen:
  [http://blog.fourthwoods.com/2012/04/24/flickering-ubuntu-11-10-boot-splash-screen/](http://blog.fourthwoods.com/2012/04/24/flickering-ubuntu-11-10-boot-splash-screen/)
  I had tried the Nomodeset mentioned in the above link on my second  installation after which my ubuntu started showing low graphics mode  error and I had to reinstall again.
  My laptop is using Mobile Intel GM965 express chipset. My laptop  specifications are as per this link except that the RAM is 2.5 GB DDR2
  [http://www.cnet.com/laptops/dell-inspiron-1525/4507-3121_7-32814939.html](http://www.cnet.com/laptops/dell-inspiron-1525/4507-3121_7-32814939.html)
  Thanks in advance

---

### Post by DenysT on 2012-11-01
I too had problems installing 12.10 on an Inspiron 1525. The first install was the 64-bit version and I always got an error after logging in. Even after updating system errors were frequent. Finally I installed the 32-bit version and the laptop works like a charm.

---


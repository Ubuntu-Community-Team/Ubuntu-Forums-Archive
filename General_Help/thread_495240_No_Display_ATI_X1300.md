---
title: "No Display ATI X1300"
date: 2007-07-07
forum: General Help
---

### Post by xcalibur32 on 2007-07-07
I installed ubuntu recently. The installation went fine. It updated some stuff and then to update a proper dirver for ati drivers, i followed 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and when i restarted..it says no display. when i type glxinfo or fglrxinfo it says unable to open display. 

I cannot see the /etc/x11 directory to make any modifications to the xorg.conf.

Can anybody please help me

Thanks

---

### Post by southernman on 2007-07-07
To manually edit the xorg.conf file from the console just do **sudo nano /etc/X11/xorg.conf**. 

Before editing the file, make a backup first by doing **sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**.

Did you try running **sudo dpkg-reconfigure xserver-xorg** at the command prompt?

If your at a root prompt, no need for the sudo portion on any of these commands.

---

### Post by xcalibur32 on 2007-07-08
If i restore to default 'vesa' it works. But I am really eager to get the graphics card and accelarated graphics working. I followed the wiki for installing the ati driver step-by-step and it did not work. It is very frustrating..

Any help?

Thanks

---


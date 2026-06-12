---
title: "Problems configuring graphics: VIA EX10000EG"
date: 2007-04-15
forum: General Help
---

### Post by jamespetts on 2007-04-15
I recently set up a new mini-ITX system based on the [VIA EX10000EG](http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=450) motherboard (the fanless version of the E15000G). That motherboard uses the VIA Unichrome Pro 2 graphics hardware, with the CX700M2 chipset. 

I am setting it up to use a CRT monitor, but have had considerable difficulties changing the refresh rate to exceed 60hz. When I first installed it, there were no options other than 60hz available for 1024x768 in the relevant menu. 73hz was purportedly available for 800x600, but, when I selected the 800x600 mode, and after it changed resolutions, it would still be at 60hz, freeze, then return to 1024x768 at 60hz, and log me out (XOrg would keep running). 

When I tried editing xorg.conf to have a greater range of refresh rates, XOrg would fail to load entirely, giving a "no screens found" error message. So, I tried to install the correct graphics driver, since xorg.conf currently specifies "vesa". Initially, when I replaced "vesa" with "via", it would come up with the same "no screens found" (after a "device not found") error message, even when the refresh rate was reset. I tried [this](http://www.viaarena.com/Driver/via_cle266cn400cn-cx700cn800_kernel_source_installation_guide_v0.81.gz) installation method for the source versions of the drivers, but failed: either the supplied files or the instructions were faulty, as the instructions told me to compile from sources in a directory that the previous step had left empty. Another set of instructions, linked on these fora somewhere, the link to which momentarily escapes me, also failed, complaining, when I tried to run the install file, having built the drivers from sources, that it could not find the /etc/rc.d/ directory, even though Ubuntu 6.10 does not seem to have an etc/rc.d/ directory. 

I tried installing the [framebuffer](http://www.viaarena.com/default.aspx?PageID=420&OSID=44&CatID=3200&SubCatID=110) binaries, and that purported to work. I could boot into XOrg after I installed them, however the refresh rate was still stuck at 60hz (although the GUI told me that it was actually 61hz; my monitor begged to differ). I tried editing xorg.conf manually again to give it values that I know that my monitor can do (having been using exactly those values in xorg.conf with a previous machine running Mandriva), and booted into XOrg again. This time, XOrg started, and the GUI menu showed as 76hz on 1024x768, but the monitor still told me (and looked like) 60hz. Switching to 800x600 (purportedly 86hz) had the same effect as before. Also, upon having logged in again, running the screen resolution program, opening its help applet and leaving the computer for a minute or two, it hard froze within a minute or two of returning. 

Does anybody have any idea what I might do to avoid the pain of 60hz? I was planning to start with a clean install when Feisty comes out next week; might that help? All responses would be greatly appreciated.

---

### Post by Mal E Volent on 2007-04-24
Hi,
Do check your xorg.conf, it's  the "Section "Monitor" " part of it that is of primary interest and make sure that the monitor data correctly reflects it's capabilities. Autodetect doesn't always work that well.
Then go to [http://www.openchrome.org/]("http://www.openchrome.org/") and read up a bit and then download/compile/install the driver as per instructions on the site. Not perfect but a whole lot better than bog standard vesa. 

/Mal...

---

### Post by mengedej on 2007-05-14
I have problems installing the drivers in the first place, using the same Motherboard and chipset, posted in another forum:
[http://ubuntuforums.org/showthread.php?t=443589]("http://ubuntuforums.org/showthread.php?t=443589")
or
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77816&enterthread=y]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77816&enterthread=y")

I'd be grateful for any assistance.

---


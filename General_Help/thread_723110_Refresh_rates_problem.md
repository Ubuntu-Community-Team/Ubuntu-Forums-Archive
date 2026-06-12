---
title: "Refresh rates problem"
date: 2008-03-13
forum: General Help
---

### Post by Kram33 on 2008-03-13
Hi first applogies if this is the wrong thread to do this.   You probably have heard this problem before so appologies again, but I would like to ask if anyone has any as to why I cannot even see the bootloader for Ubuntu?  My monitor is a Wharfdale L15T11W-C tv/monitor and has a fixed refresh rate of 60hz.  When I load the Nvidia glx driver and reboot I can no longer see the display because the screen is on 55hz and therefore not compatible with my monitor:(  

Is there any work around to this?  Also My card is a Nvidia 6200 with a DVI output, would this be of any difference to me, right now Im using standard VGA.

Thanks Mark

---

### Post by dayanandasaraswati on 2008-03-13
You go to the command line and reconfigure the Xserver. This can be done by this command 

**> sudo dpkg-[B]reconfigure xserver**-xorg[/B]

---

### Post by Kram33 on 2008-03-13
ok thank you :)

---

### Post by Kram33 on 2008-03-13
dayanandasaraswati I did what you advised, but now I cannot see the command line either, it comes up with the same error "no support", is there a fix for this in the GUI of Ubuntu?

Im new to Linux and could really use the help :)

Thank you Mark

---

### Post by dayanandasaraswati on 2008-03-13
Go to System->Administration->Screen and Graphics. Now a pop up dialogue box will open up. Just click on the box with the label MODEL. Now another dialogue box will pop up. This box allows you to manually configure your display. There are two panes. The left one displays the brand names and on the right pane their models. Check if you have your model listed there, or choose the nearest.

---

### Post by Kram33 on 2008-03-13
thank you once again:)

---


---
title: "Setting a higher GRUB2 screen resolution"
date: 2016-02-06
forum: General Help
---

### Post by cjsmall on 2016-02-06
During boot, the series of system messages that are displayed used to be in a nice tight font. Recently, I installed the Nvidia 352.79 driver, switching from the default X.Org Nouveau driver, and reconfigured my graphic displays (an Nvidia K4000) using the Nvidia X Server Settings tool. Something was changed in the process and now these system messages are displayed in a very large and crude font which is probably the result of the display resolution longer being properly set during the boot sequence.

I used the Grub Customizer to up the resolution but the highest resolution available was 800x600x24.  My monitors are currently running at 1600x1200 and the font display is still much too large.  Notes in **/etc/default/grub** indicate that only supported VBE modes may be used.  Does Grub Customizer probe the graphic card and report the only available resolutions?  If so, then why was the display resolution previously better.  (Maybe due to the switch in video drivers???)

Is there a method to check what is going on and adjust it to get the original superior boot display? Thanks.

---

### Post by oldfred on 2016-02-06
At grub menu, go to grub command line.

 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

That should show what system is offering in sizes.
Then use that size to set grub file.


 Use command line editor grub's on setting to size from above:
#gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub



 > `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


---


---
title: "Command Line resolution"
date: 2007-03-29
forum: General Help
---

### Post by t94xr on 2007-03-29
I want to find out if I can make the command load up at 1024x786res so the font isn't so pixellated and out of focus on a laptop, desktop & server.

If you can show me how that should be awesome! :)

---

### Post by gepatino on 2007-03-29
You have to specify the vga mode in /boot/grub/menu.lst, maybe I'm wrong but I think it was 792 for a 1024x768 screen.

Edit the mentioned file, and search for 'defoptions', you'll see an example saying vga=791. Add 'vga=792' to the line:

# defoptions=quiet splash

After this, run update-grub as superuser.

---

### Post by mcduck on 2007-03-29
> **gepatino said:**
> 
After this, run update-grub as superuser.
..or just add the same thing to kernel line while you are editing the menu.lst ;)

---

### Post by dreadlord_chris on 2007-03-29
> **gepatino said:**
> You have to specify the vga mode in /boot/grub/menu.lst, maybe I'm wrong but I think it was 792 for a 1024x768 screen.

Edit the mentioned file, and search for 'defoptions', you'll see an example saying vga=791. Add 'vga=792' to the line:

# defoptions=quiet splash

After this, run update-grub as superuser.

vga=785 
640x480 

vga=788 
800x600 

vga=791 
1024x768 

vga=794 
1280x1024

---

### Post by mcduck on 2007-03-29
> **dreadlord_chris said:**
> vga=785 
640x480 

vga=788 
800x600 

vga=791 
1024x768 

vga=794 
1280x1024

792 is for 1024x768 with 32-bit colors.. those values are for 16-bit colors. Not a big difference other than that 32-bit colors allow you to have nice looking text (if you remove the 'quiet'-option in menu.lst) in usplash when 16-bit colors make the text blue.

---

### Post by Railsbuntu on 2008-03-19
Hi, I have an LCD 19" 1280x1024 that I have plugged in my server (I have no gui). I wanted to change the resolution to 1280x1024, so I entered vga=794. The problem is now I get an error message sent by the screen: "Input not supported". Are you sure of you figures? Where can I find the complete list?

PS: how do I reboot in recovery mode? because now my computer is unusable.

---

### Post by gryphon_wolf on 2008-03-19
If your computer works comperably to mine there should be a visible option right near the beginning of a boot that allows you to change to recovery mode.

---

### Post by Railsbuntu on 2008-03-19
This is getting ridiculous, I have tried vga=794, 791, 775, none of them work. How can I know what works? I don't want to toast my screen.

EDIT: from the gentoo docs, this happens when framebuffer is activated, and the solution is to turn it off by removing the vga=xxx statement. How can I know if framebuffer is installed on my box? I am probably missing that.

EDIT2: do I need to install the graphics card driver? (I have an nvidia)

---


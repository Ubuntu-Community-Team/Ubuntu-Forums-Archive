---
title: "Help with Geforce 5200"
date: 2005-04-02
forum: General Help
---

### Post by newbuntu on 2005-04-02
I am able to run Warty 4.10 live on an old P111 450 and an AMD with a geforce 2. When I try to run on my own PC - P4 2,66, 512mb ram and a geforce 5200 - everything is fine until it seems to go into the O\s and then my screen goes blank with all the lights blinking - a CTX monitor. This is the same monitor that worked on the AMD system. Any ideas? I am brand new to linux and keen to learn.

---

### Post by Whiffle on 2005-04-02
Sounds to me like the screen refresh rate isn't right and the monitor is shutting itself down.  Look on the back of the monitor, there should be a tag with the model number on it.  We can google that and find the right specifications for the Horizontal sync and vertical refresh frequencies.  Then, edit /etc/X11/XF86Config-4 with the new values.  Do this by hitting ctrl+alt+f2 when your monitor goes blank after you start the computer, log in, run  " sudo nano -w /etc/X11/XF86Config-4 ", then scroll down to the "Monitor" section.  Then put the correct values for HorizSync and VertRefresh.  Then hit f3 to save, ctrl+x to quit nano, and ctrl+d to logout.  At this point, press ctrl+alt+f7 , and then ctrl+alt+backspace and if everything is right, the X server will restart and you'll soon be at the pretty login  screen :)

---

### Post by newbuntu on 2005-04-03
Thank you for the advice - tried this, but a message stating the file is read only. I also tried to boot in "expert mode" and down the line a message "Do you want to (re)configure your graphics (x11) subsystem? (not currently working in morphix" When I select yes - again a message that the file is read only. Looks like I will have to wait for the next version, unless I can laod someting of a stiffy somehow?

---

### Post by jazzer on 2005-04-03
When I first tried the Warty LiveCD with my Geforce 5200; my screen went blank when it booted into X (graphical desktop).  I would suggest when it gives you the boot options you should go and select advanced options (can't remember the exact names - been a bit since I tried it) and select the option for an nvidia graphic card. Mine worked after that.... On a promising note my nvidia card worked right away when I actually installed Ubuntu on my desktop.  Hopefully this helps.  If you can't find the options, I'd be more than happy to reboot into the LiveCD and find the actual boot options...  :D

---

### Post by akshoslaa on 2005-04-03
Just making sure, did you run the command with sudo?

sudo nano -w /etc/X11/XF86Config-4

rather than

nano -w /etc/X11/XF86Config-4

You need to have admin permissions to edit XF86Config-4, otherwise it opens as read-only

File permissions was one of the biggest stubling blocks I had when I made the switch... so used to Windows, where the user can just do whatever they want... (hence why I spent today fixing someones onputer after her husband decided to clear some space by deleting things he didn't recognise... *facepalms*)

[EDIT]
Oh, Live CD... Whoops... *reads the question properly*
CD's are read only...so you can't edt the configuration files easily (I assume it can be done by extracting the iso, making the changes then rebuilding/burning, which might be necessary if you want to use the live CD often... No idea how involved that'd be though, still learning myself :P)

For occasional use though, Jazzer's suggestion of setting the boot paramiters is all good... It'd get ratehr annoying after a while though

---

### Post by newbuntu on 2005-04-05
Thanks jazzer - got it working. Thanks to everyone for the help.

---


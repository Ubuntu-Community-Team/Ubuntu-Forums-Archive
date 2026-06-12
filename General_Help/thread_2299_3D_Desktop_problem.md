---
title: "3D Desktop problem"
date: 2004-10-27
forum: General Help
---

### Post by vaskark on 2004-10-27
Hi. I'm a new Ubuntu user and think it's terrific. I've been trying some of the software thru Synaptic and came across 3ddesktop (thru 'universe'), which performs a 3D animation when switching between workspaces. I installed this app and ran this command at the CL:
 
 3ddesk --acquire
 
 ... and was given this response:
 
 Attempting to start 3ddesktop server.
 get property WIN_WORKSPACE failed - setting one
 get property WIN_WORKSPACE_COUNT failed - setting one
 Daemon started.  Run 3ddesk to activate.
 Xlib:  extension "XFree86-DRI" missing on display ":0.0".
 3ddeskd: glXIsDirect failed, no Direct Rendering possible!
 3ddeskd: Please configure hardware acceleration.  Exiting.
 Can't get message queue: No such file or directory
 Maybe 3ddeskd server not started?
 
 Has anyone else tried 3ddesktop and encountered this? Any help would be greatly appreciated.
 
 -- vaskark

---

### Post by orion_114 on 2004-12-20
I had the same problem. Managed to get it working by installing "nvidia-glx" from synaptic package manager. 

if you run :
glxinfo | grep "direct rendering"

and it responds:
direct rendering: yes

Then you should be able to work it.
You might have to change some ot the configurations in the file
/etc/X11/XF86Config-4
I was prompted to change the Driver parameter from "nv" to "nvidia" in the "Device" section
to edit it use the command:

sudo gedit /etc/X11/XF86Config-4

to restart your xserver go "ctrl" + "alt" + "backspc"
then in the  cli type "startx".

Also check out:
[http://www.ubuntulinux.org/wiki/3ddesktopHowto/](http://www.ubuntulinux.org/wiki/3ddesktopHowto/)
[http://ubuntuguide.org/index.html#enhancenvidiaperformance](http://ubuntuguide.org/index.html#enhancenvidiaperformance)

Hope you get it working :)

---

### Post by vaskark on 2004-12-22
Thanks for replying, orion_114. I installed nvidia-glx and ran ...
  
  glxinfo | grep "direct rendering"
  
  which responded:
  
  Xlib:  extension "GLX" missing on display ":0.0".
  Xlib:  extension "GLX" missing on display ":0.0".
  Xlib:  extension "GLX" missing on display ":0.0".
  Error: couldn't find RGB GLX visual
  Xlib:  extension "GLX" missing on display ":0.0".
  Xlib:  extension "GLX" missing on display ":0.0".
  Xlib:  extension "GLX" missing on display ":0.0".
  Xlib:  extension "GLX" missing on display ":0.0".
  
 I'm using hoary and my graphics card is an ATI Radeon 9200se 128 Mb. Hoary uses XOrg. I've attached my xorg.conf file. Can you take a look and make some further suggestions? Thx.
  
  -- vaskark

---

### Post by orion_114 on 2004-12-23
Just looking at the config it looks like you havent setup your drivers correctly.
In the section below it looks as though you have an s3 card installed.

Section "Device"
	Identifier	"S3 Inc. 86c764/765 [Trio32/64/64V+]"
	Driver		"s3"
	BusID		"PCI:0:8:0"
EndSection

So try reinstalling your ati drivers.

---

### Post by orion_114 on 2004-12-23
try this link for some help ....

[http://ubuntuforums.org/showthread.php?t=3713&highlight=ATI](http://ubuntuforums.org/showthread.php?t=3713&highlight=ATI)

---

### Post by vaskark on 2004-12-23
I followed that tutorial for installing ATI drivers, but I don't think it worked. I noticed some error messages when I was rebooting. I guess I need instructions that are more in-depth. That tutorial on installing ATI drivers really confused me, at step 3.

-- vaskark

---

### Post by snipes420 on 2004-12-24
I dont mean to hijack the thread, I also have a question about 3ddesktop.

I installed it with synaptic from universe and then started 3ddeskd.
It says it started ok. Then I set up a key bind from F12 to /usr/bin/3ddesk like it suggests on the 3ddesktop website. it describes how to do it in redhat but since ubuntu uses metacity too it worked perfectly.

> Run "gconf-editor". Drill down to apps --> metacity --> global_keybindings. Find "run_command_1" and change it to your key such as "F12" or "<Control><Alt>S". Then in apps --> metacity --> keybinding_commands find "command_1" and set it to "/usr/bin/3ddesk".

But when I hit F12 it only shows one of my 4 workspaces. and if I press left or right it doesn't switch through the other workspaces because I dont think it can see them or something. The FAQ on the 3ddesk page mentions there is some information in the readme about this issue but I read through it and I couldn't find anything to help me with this problem. I am going to look for an older version of this package to see if an older readme has the information I need, But if anyone can enlighten me I would appreciate it.

[README](http://desk3d.sourceforge.net/README)
[3ddesk website](http://desk3d.sourceforge.net/)
[3ddesk FAQ](http://desk3d.sourceforge.net/faq.php)

---

### Post by snipes420 on 2004-12-24
ok I found it already. im embaressed now. :oops: 
in the file /etc/3ddesktop/3ddesktop.conf
you have to uncomment the line that says 
```
#ewmh        on  ## For GNOME 2, KDE 3, etc  (NET protocol Standard)
```then it works. its a pretty sweet piece of eyecandy too

---

### Post by MrTrumpets on 2005-01-21
Thanks! This is awesome!

both the F12 command and the comment block.  :)

---

### Post by Campitor on 2005-02-03
[QUOTE=MrTrumpets]Thanks! This is awesome!

both the F12 command and the comment block.  :)[/QUOTE]
 Hi :

   Sorry to but-in but I had the same problem as Vaskark...when i tried to start 3ddesk I got:

ttempting to start 3ddesktop server.
get property WIN_WORKSPACE failed - setting one
get property WIN_WORKSPACE_COUNT failed - setting one
Daemon started. Run 3ddesk to activate.
Xlib: extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration. Exiting.
Can't get message queue: No such file or directory
Maybe 3ddeskd server not started?

But...And here is were I get embarrased about my computer...I dont have an ATAPI driver, I have a Matrox video card.  When I type :

glxinfo | grep "direct rendering"

it responds:
direct rendering: no

Can I enable direct rendering, or with my outdated video card I should just settle for normal desktop switching?  Thanks in advance for help..

Camp.

---

### Post by meissen on 2006-10-11
Bumpin it up, I have a Dell Inspiron E1505 with an ATI X1400 video card. I've followed the steps for the ATI how-to (method 2) but when I do the [COLOR=Red]glxinfo | grep "direct rendering"[/COLOR] I get: [COLOR=Red]direct rendering: No[/COLOR]



Is there a way to get direct rendering enabled?

---

### Post by mumiz3807 on 2007-05-15
> **snipes420 said:**
> I dont mean to hijack the thread, I also have a question about 3ddesktop.

I installed it with synaptic from universe and then started 3ddeskd.
It says it started ok. Then I set up a key bind from F12 to /usr/bin/3ddesk like it suggests on the 3ddesktop website. it describes how to do it in redhat but since ubuntu uses metacity too it worked perfectly.


But when I hit F12 it only shows one of my 4 workspaces. and if I press left or right it doesn't switch through the other workspaces because I dont think it can see them or something. The FAQ on the 3ddesk page mentions there is some information in the readme about this issue but I read through it and I couldn't find anything to help me with this problem. I am going to look for an older version of this package to see if an older readme has the information I need, But if anyone can enlighten me I would appreciate it.

[README](http://desk3d.sourceforge.net/README)
[3ddesk website](http://desk3d.sourceforge.net/)
[3ddesk FAQ](http://desk3d.sourceforge.net/faq.php)


[Girls Tsunami biology caffeine photosynthesis](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---


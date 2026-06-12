---
title: "X server failing"
date: 2005-10-20
forum: General Help
---

### Post by ges4 on 2005-10-20
Alright, I'm completely new to Linux, and I believe I got the install to go correctly, but then on reboot and choosing the default settings for display I will eventually get a blue screen with message after the login prompt flickers to black twice:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <Yes>  <No>

On Yes:

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819
[email]root@crested.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Buils Operating System: Linus 2.6.8.1 x86_64 [ELF}
Current Operating System: Linux Swan 2.6.12-9-amd64-generic #1 Mon Oct
10 13:27:39 BST 2005 x86_64
Build Date: 10 October 2005

Module Loader present
OS Kernel: Linus verision 2.6.12-9-amd64-generic (buildd@king) (gcc
version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon
Oct 10 13:27:39 BST 2005
Markers: (-) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.0.log",
(++) Using config file: "etc/X11/xorg.conf"
Skipping
"/usr/X11R6/lib/modules/extenstions/libGLcore.a:m_debug_clip.o": No
symbols found
Skipping
"/usr/X11R6/lib/modules/extenstions/libGLcore.a:m_debug_norm.o": No
symbols found
Skipping
"/usr/X11R6/lib/modules/extenstions/libGLcore.a:m_debug_xform.o": No
symbols found
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support at [http://wiki.X.Org](http://wiki.X.Org) for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


and then, the next screen displayed shows:


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819
[email]root@crested.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Buils Operating System: Linus 2.6.8.1 x86_64 [ELF}
Current Operating System: Linux Swan 2.6.12-9-amd64-generic #1 Mon Oct
10 13:27:39 BST 2005 x86_64
Build Date: 10 October 2005

Module Loader present
OS Kernel: Linus verision 2.6.12-9-amd64-generic (buildd@king) (gcc
version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon
Oct 10 13:27:39 BST 2005
Markers: (-) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/Var/log/Xorg.0.log," Time: Thu Oct 20 00:31:14 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |--> Screen "Default Screen" (0)
(**) |     |-->Monitor "Generic Monitor"
(**) |     |-->Device "ATI Technologies, Inc. Radeaon X850 Pro (R480)"
(**) |--> Input Device "Generic Keyboard"
(**) |--> Input Device "Configured Mouse"
(WW) THe directory "/usr/share/X11/fonts/cyrillic" does not exist
Entry deleted from font path
(WW) The directory "/usr/share/X11/fonts/CID" does not exist
Entry deleted from font path
(WW) 'fonts.dir' not found (or not valid) in 
"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
Entry deleted from font path
(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").

then more random stuff

(WW) Open  APM failed (/dev/apm_bios) No such file or directory)


which is the end of the WW marks and is only II marks for the rest of the entry


What the heck do I do? is this not enough info? (I can type more, but i can't copy paste so it takes a bit) I really wanna use linux so this is really important to try and get this to work.

---

### Post by ecobuntu on 2005-10-20
Try This

sudo dpkg-reconfigure xserver-xorg

This will let you reconfigure X.  See if you can figure it out there.

---

### Post by ges4 on 2005-10-20
when i get to the color bit select, all options give me a warning and send me to the prompt and 24 bit gives me:

: error: backup xorg.conf file /etc/X11/xorg.conf .200510200123 already exists; please remove it and try again

THe monitor is 19 inch LCD

---

### Post by Bloodwolf808 on 2005-10-20
Ya im getting the exact same problem as you.  I tried to reconfig a few times and I always get the same problem.  For monitor I just put in generic monitor then I tried putting my monitor model(eview 17f3) still nothing.  Tried 24 bit 1024x768 @60 hz still nothing =/. Please help!!!

---

### Post by daahli on 2005-10-20
Hey guys,

I just formatted my entire hard drive yesterday and fresh installed Breezy. To my surprise I ran into the exact same problem. The problem has to do with your graphics card. I managed to fix the problem eventually by typing the following into the command line.

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg

This brings you back to the configuration screen. Now make sure to select the **fglrx** driver for your graphics card (not ATI!). Then proceed as you would normally. 

Once your done you can simply type:

startx

to start X.

Hope this works for you guys :)

---

### Post by Bloodwolf808 on 2005-10-20
I have AMD 64 3500(i know it doesnt matter)
ATI sapphire x850 pro PCI-E
160 GB/40GB slave(for linux)
DFI LP NFD-4
1024 RAM

Help please That thing didnt work.

---

### Post by ges4 on 2005-10-20
I still get the same problem trying to configure the bit depth, After selecting a number, I drop out of X server with the same warning as before with my changes unsaved in the previous config screens. Is there a reason i wouldn't be able to change the config file?

---

### Post by ges4 on 2005-10-20
Alright, I admit my newbieness and admit through more testing that the config file IS saving correctly, it's just warning me that it's doing so.

guess I'm used to windows where warnings meant that the system was dying in some way, not that I might want to actually know something important.

But still, I digress.

On startx, I get the following text after a normal opening thing:

Skipping "/usr/X11R6/lib/modules/extenstio0ns/libGLcore.a:m_debug_clip.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extenstio0ns/libGLcore.a:m_debug_norm.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extenstio0ns/libGLcore.a:m_debug_xform.o": No symbols found
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure

then the Please consult website and log file

XIO: fatal IO error 104 (connection reset by peer on X server ":0.0"
       after 0 requests (0) known processed) with 0 events remaning.


If it helps at all, my machine is custom: my friend built it for me. I'm not sure of all the specs, but I do know it's a Lanparty, with Amd64, 2 Gigs of RAM, creative sound blaster audigy2 ZS pro, Radeon video card which I believe is in the lower PCI slot. Anything more specfic I have to delve through old papers for. The monitor is a Sceptre gamer 19" LCD. Thanks again guys, I appreciate all the help.

---

### Post by ges4 on 2005-10-20
Alright, i changed the graphics driver to vesa because of something on another post, and that seemed to work (16 bit graphics)

Now i'm in GNOME, how can I  get my video card to work or is this temporary solution all I have?

---

### Post by ges4 on 2005-10-23
I've tried everything I can think of at this point, but I can't get my video card to work at any color depth higher than 16 bit in VESA. I can't stand the low quality. What else can I try to do?

---

### Post by porter on 2005-10-24
i get the same x server failing message.

[QUOTE=ecobuntu]Try This

sudo dpkg-reconfigure xserver-xorg

This will let you reconfigure X.  See if you can figure it out there.[/QUOTE]

tried that but after typing it in i get:
"unable to lookup ubuntu5.10 via gethostbyname"

now what?

---

### Post by zinkee on 2005-10-25
hello all
Am also new in linux and i have the some xserver failing problem and the the three commands above doesnt work ...
 can anyone help:???:

---

### Post by zinkee on 2005-10-25
hello all
Am also new in linux and i have the some xserver failing problem and the the three commands above doesnt work ...
can anyone help

---

### Post by longshot5000 on 2005-10-26
well i have also posted about this.  I have this problem happen with 5.04 x386 version and also with 5.10 AMD64 I also have a 19inch LCD - I wonder if that is what is causing ths problem.  Otherwise I am stumped and really hope someone can help out with this problem

---

### Post by RAOF on 2005-10-26
The 19inch LCD won't be the problem.  It seems the problem is the ati driver.  Now, I don't have an ati card myself, so I can't really help you, but I'd try searching the forum for "fglrx", or looking at [this thread]("http://www.ubuntuforums.org/showthread.php?t=75428&highlight=ati+fglrx").

---

### Post by zinkee on 2005-10-26
my card is Gforce 5200 & i have the same problem

---

### Post by RAOF on 2005-10-26
For nvidia cards, you should be able to do
```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```
and that should get you get you working nvidia drivers.  If it doesn't, try "sudo dpkg-reconfigure xserver-xorg", and select "nvidia" for the driver.

Oh, and porter:
[QUOTE=porter]
...
tried that but after typing it in i get:
"unable to lookup ubuntu5.10 via gethostbyname"

now what?[/QUOTE]
This is actually a problem with sudo.  A quick search of the forums suggests[ this thread.]("http://www.ubuntuforums.org/showthread.php?t=81561")

---

### Post by zinkee on 2005-10-26
My problem now is about sudo
when i type any sudo command then this message appears
could not find kernel image: sudo
how can i fix it
& also it appears when i try to type any command

---

### Post by N8MAN1068 on 2005-10-27
Interesting. I'm having this problem too.
I was running fine under gnome. Last things I can remember were installing KDE+games(was fine).
I also installed the k7 kernel/module/headers because I have an AMD cpu. I have a nvidia geforce 3 card.

I'm going to try to follow [http://ubuntuforums.org/showthread.php?t=75074&highlight=command+login](http://ubuntuforums.org/showthread.php?t=75074&highlight=command+login)
hopefully, I 'll be able to do all of this through command line, and my usb drive will be recognized on boot(which is another thread, because reboot shuts down the pc).

---

### Post by N8MAN1068 on 2005-10-27
no dice :/
I have a 17" monitor, so that rules out the 19" equation.
I was ok on the 386 kernels, although longshot5000 said he had this problem on 386 in hoary....
could it be the Breezy kernels+AMD+Nvidia=fubar?

---

### Post by Mustard on 2005-10-27
[QUOTE=N8MAN1068]no dice :/
I have a 17" monitor, so that rules out the 19" equation.
I was ok on the 386 kernels, although longshot5000 said he had this problem on 386 in hoary....
could it be the Breezy kernels+AMD+Nvidia=fubar?[/QUOTE]

I'm running a Breezy 686 kernel, AMD, nvidia with no problems, so I would say its not fubared (in my case at least).

---

### Post by N8MAN1068 on 2005-10-27
you're running the 686 kernel on an AMD?
Any benefits to not using the K7 package?

I've opted for a complete clean reinstall. I think it'll be much faster to reinstall and try again than the poke around and find out whats wrong. Unless of course, is fails again. Then i'll be ticked.

---

### Post by Mustard on 2005-10-27
[QUOTE=N8MAN1068]you're running the 686 kernel on an AMD?
Any benefits to not using the K7 package?

I've opted for a complete clean reinstall. I think it'll be much faster to reinstall and try again than the poke around and find out whats wrong. Unless of course, is fails again. Then i'll be ticked.[/QUOTE]

I wouldn't have a clue, N8MAN1068.  I was always keen to try kernel suited to my system, but was unsure what to choose.  Someone in IRC suggested installing 686, so I did.  Everything still worked, so I have been happy.

---

### Post by porter on 2005-10-29
ok, i got passed the sudo probelm, but still no luck with getting a successful boot. it's still quitting with the x server failing. i've run through the reconfigure a couple of times with different selections but no go. 

any other suggestions? 

i've got an ati radeon xpress 200. the reconfigure finds the right video card but still won't boot.

---

### Post by porter on 2005-11-01
i dug around through the forums and found that i may need to install the fglrx drivers. so far the 'sudo apt-get install xorg-driver-fglrx' gives me an error of "couldn't find package xorg-driver-fglrx". 

how do i get it to find the driver?

---


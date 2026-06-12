---
title: "Two identical machines, one the graphics works the other does not."
date: 2008-06-05
forum: General Help
---

### Post by lawentzel on 2008-06-05
I have two laptops here at work running Ubuntu 8.04.  The laptops are Dell Latitiudes.  I managed to get my graphics working and can not get them working right on the other one.

So, with that said, what all files do I need to copy from my system to the other system to see if we can't get it up and running?  I've already tried the xorg.conf.  This didn't help.

How I am testing the computers is through screen saver, and looking at "Endgame".  The video cards are NVidia.  I haven't got a clue what it was I did to get mine to work.  But, it does.  Looking at "Endgame" on my machine everything is rendered nicely.  Looking at it on the second laptop, the screen is blank.  No graphics at all.

Help please.  Thanks in advance.

---

### Post by Zorael on 2008-06-05
What is the terminal output of the following commands entered on the non-working machine?
```
$ glxinfo
$ lshw -C video
$ cat /etc/X11/xorg.conf | grep -i driver
$ dpkg -l nvidia*
$ apt-cache policy xserver-xgl
```
Encase it within code tags, please, to make it more legible.

---

### Post by lawentzel on 2008-06-05
First, thank you for replying.  Secondly, he is all the data you had requested.

```
glxinfo=
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

(sudo) lshw -C video=
 *-display               
       description: VGA compatible controller
       product: NV17 [GeForce4 440 Go]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master vga_palette cap_list
       configuration: driver=nvidia latency=32 maxlatency=1 mingnt=5 module=nvidia

cat /etc/X11/xorg.conf |grep -i driver=
	Driver		"kbd"
	Driver		"mouse"
	Driver		"synaptics"
	Driver		"vesa"
	Driver		"vesa"

dpkg -l nvidia*=
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  nvidia-glx     1:96.43.05+2.6 NVIDIA binary XFree86 4.x/X.Org driver
un  nvidia-glx-leg <none>         (no description available)
un  nvidia-glx-new <none>         (no description available)
un  nvidia-glx-src <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
ii  nvidia-kernel- 20051028+1ubun NVIDIA binary kernel module common files
un  nvidia-kernel- <none>         (no description available)
un  nvidia-setting <none>         (no description available)
un  nvidia-xconfig <none>         (no description available)

apt-cache policy xserver-xgl=
xserver-xgl:
  Installed: (none)
  Candidate: 1:1.1.99.1~git20080115-0ubuntu1
  Version table:
     1:1.1.99.1~git20080115-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/universe Packages

```

---

### Post by Zorael on 2008-06-05
Well, you certainly have the nvidia driver installed but it doesn't seem to be enabled in your xorg.conf.

Is this an upgraded installation?
Do you have two monitors? The cat | grep line suggests as much, with two driver "vesa" entries.

I'd suggest you do this, regardless.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0806
$ sudo dpkg-reconfigure xserver-xorg      # go through guide, ignore error messages
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Save your work, log out, Ctrl+Alt+Backspace to restart X, log in again, try your screensaver.

---

### Post by lawentzel on 2008-06-05
Ok.  Got an error when running the last line.
```
sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```

The error reads:
```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver line.
```

I rebooted the computer any way to see if it resolved the issue.  It did not appear to.  Any suggestions?  Oh and to answer your previous question, the computer that isn't work was updated from version 7.10.  The one that does work was a clean install.

---

### Post by Zorael on 2008-06-05
The error is to be expected, but if it doesn't work it shows that indeed, the xorg.conf is okay.

Were I you, I'd (continue troubleshooting for a while, then) bite the sour apple, backup my home directory, and install 8.04 fresh.

---


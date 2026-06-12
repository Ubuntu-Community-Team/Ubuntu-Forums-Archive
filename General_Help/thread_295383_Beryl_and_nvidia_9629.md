---
title: "Beryl and nvidia 9629"
date: 2006-11-08
forum: General Help
---

### Post by Russty of Oz on 2006-11-08
I was wondering if anyone else is having problems with Beryl since the new Nvidia drives 9629 were installed?  I can't get Beryl to start properly, there is no frame (or whatever you call it) around the windows.  So there is no close, minimize etc. buttons.  On one try to start Beryl I got the terminal saying that there was NO GLXBconfig (well, something like that) and this kept going on until I switched back to KDE.

Any help would be much appreciated or else I will have to stick with KDE and forget about Beryl.

Russty.

---

### Post by GameManK on 2006-11-08
I can't quite understand what you're using to start it, but here's what I do that works fine with the beta drivers:
Log into KDE as usual, go to konsole and launch```
beryl-manager
```
That starts up beryl and gives you a little diamond in your system tray to change settings, including ability to pick a theme for the window decorator.

You need to have emerald-themes (I think that's what it was) installed.
EDIT: Running 9625 drivers, upgrading..

---

### Post by Russty of Oz on 2006-11-08
That is how I start Beryl.  Something just isn't working properly.

---

### Post by _simon_ on 2006-11-08
Just replaced the beta 9629 drivers with the official 9629 ones and beryl still works fine for me.

---

### Post by 23meg on 2006-11-08
Same here, but I also still have the black window bug.

---

### Post by Russty of Oz on 2006-11-08
So it must just be something in my system that is the problem.  Perhaps I will have to uninstall Beryl and start again.

Oh well! :neutral:

---

### Post by UlyssesR on 2006-11-08
Hi

Well, I'm having the same problem over here, however my drivers are older.

If I just Ctrl+Alt+Backspace and restart gdm (launching X again) Beryl works correctly most of the times.

I have never tried to sort it out, but if it happens to me the problem must be in Beryl...

---

### Post by adam.skinner on 2006-11-08
On the Beryl wiki, one of the admins was kind enough to post his working xorg.conf.  Archive yours and adapt this to your own use.  You probably have some extra stuff in there that's causing problems.

[http://www.geocities.com/charetjc/xorg.conf.html](http://www.geocities.com/charetjc/xorg.conf.html)

---

### Post by Clarencemark on 2006-11-08
I had the same problem. My solution was a reboot of my cpu and all is well. I like the new Nvidia logo by the way.

---

### Post by UlyssesR on 2006-11-08
Thanks adam.skinner!

I modified my xorg.conf and now it's working good and even faster. Just checked and the driver running is version 9629...

---

### Post by Russty of Oz on 2006-11-08
> **adam.skinner said:**
> On the Beryl wiki, one of the admins was kind enough to post his working xorg.conf.  Archive yours and adapt this to your own use.  You probably have some extra stuff in there that's causing problems.

[http://www.geocities.com/charetjc/xorg.conf.html](http://www.geocities.com/charetjc/xorg.conf.html)

Sorry for the silly question, but how do I find my xorg.conf? :redface:

---

### Post by Russty of Oz on 2006-11-08
I just installed Beryl again and this is what happened.


russty@russty-desktop:~$ beryl-manager
russty@russty-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
Initiating splash
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32


There is no task bar or window themes etiher so I will have to restart to get back to normal.

Any ideas? :-?

---

### Post by HoMe_CaNiBaL on 2006-11-09
Hi there..


My system freezes everytime with nvidia beta 96.25 or 96.29, working with beryl 0.1.1..

My problem was solved installing beryl 0.1.2..but i still have a problem..
everything is ultra fast.the rain, every efect is very fast.

My system is
Pentium 4 2.8
1gb Ram
300gb HDD
6600 GT 128Mb
P4C800 DLX
Audigy 1

I'm with Edgy with kernel 2.6.17.10-generic (i think)

Thanks

---

### Post by astoltz on 2006-11-09
> **HoMe_CaNiBaL said:**
> 
My problem was solved installing beryl 0.1.2..but i still have a problem..
Where did you find 0.1.2?  The beryl-project.org repository still shows 0.1.1 for me.

---

### Post by HoMe_CaNiBaL on 2006-11-09
> **astoltz said:**
> Where did you find 0.1.2?  The beryl-project.org repository still shows 0.1.1 for me.

wait 5 minutes...let me see if i can find the repository.i'm working, not in home...

---

### Post by HoMe_CaNiBaL on 2006-11-09
> Add this repository to sources.list

deb [http://ubuntu2.beryl-project.org](http://ubuntu2.beryl-project.org) edgy main

To enable the public key:
sudo -s
wget [http://ubuntu2.beryl-project.org/1609B551.gpg](http://ubuntu2.beryl-project.org/1609B551.gpg) -O- | apt-key add -


Beryl 0.1.2 was launched today...
I like the new Beryl Logo, and i have no problem with freezes.... Think so...

Cumps

---

### Post by Russty of Oz on 2006-11-09
I got an error, this is what it said

russty@russty-desktop:~$ wget [http://ubuntu2.beryl-project.org/1609B551.gpg](http://ubuntu2.beryl-project.org/1609B551.gpg) -O- | apt-key add -
--09:51:34--  [http://ubuntu2.beryl-project.org/1609B551.gpg](http://ubuntu2.beryl-project.org/1609B551.gpg)
           => `-'
Resolving ubuntu2.beryl-project.org... 80.77.247.17
Connecting to ubuntu2.beryl-project.org|80.77.247.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s             

09:51:37 (126.91 MB/s) - `-' saved [1730/1730]

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error


What do I do about that? :-?

---

### Post by Russty of Oz on 2006-11-09
After doing the beryl 0.1.2 thing I got the update icon but when I went to get the updates it says there was an error with the downloads, it appears to be with this one deb [http://ubuntu2.beryl-project.org](http://ubuntu2.beryl-project.org) edgy main


Nothing works! :(

---

### Post by Russty of Oz on 2006-11-09
Well, 2 hours later and I tried the updates again and for some reason this time it worked.

Now to see if Beryl will work, fingers crossed!

---

### Post by Russty of Oz on 2006-11-09
Well I now have Beryl 0.1.2 but still have the same problem as before.  I still get this  [B]beryl: No GLXFBConfig for depth 32
[/B]  

So does anyone know what it means?

---

### Post by 23meg on 2006-11-09
Change your DefaultDepth in xorg.conf to 24.

---

### Post by HoMe_CaNiBaL on 2006-11-09
> **Russty of Oz said:**
> Well I now have Beryl 0.1.2 but still have the same problem as before.  I still get this  [B]beryl: No GLXFBConfig for depth 32
[/B]  

So does anyone know what it means?

post here your xorg.conf please...

in xorg you must have something like this..

> Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "SyncMaster"
    **DefaultDepth    24**


see in your xorg the bold...if you have 32 thats the problem..i think...because in nvidia-settings i have depth at 32...

try it..

---

### Post by dannyboy79 on 2006-11-09
not having the window borders and no close button etc etc is nothing new to composite, it has to do with a window theme and beryl. i know when I had the issue i simply typed in meta city or something like that at the command line and my  borders came back etc etc. someone posted that you need to install the emerald themes did you do that? also, the beryl forums would help you more than the ubuntu forums since that;s all they deal with over there. [http://www.beryl-project.org/index.php](http://www.beryl-project.org/index.php) and it turns out that you don't need emerald i just read, beryl has a window decorator built in, so I would head over there for the answer to the missing window decorator issue

---

### Post by Russty of Oz on 2006-11-09
how do I find my xorg.conf?

---

### Post by 23meg on 2006-11-09
```
sudo kate /etc/X11/xorg.conf
```assuming you're using Kubuntu.

---

### Post by Russty of Oz on 2006-11-09
Here is my xorg.conf.


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:47:17 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Slim View 700"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce FX 5200"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce FX 5200"
    Monitor        "Slim View 700"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Russty of Oz on 2006-11-10
OK, I have finally got it to work!  :D 

It  seems that I was missing a line in my /etc/X11/xorg.conf  file.  This was the missing bit:

[B]As far as i know the following is depreciated... although you may as well try with it on and off to see the difference: Add

Option          "TripleBuffer" "true"

to Section "Device" It should help with performance, especially during rain![/B]

By the way, what is "rain"?  (I assume it is not referring to precipitation?):-k

---

### Post by 23meg on 2006-11-10
It's an effect achievable with the water plugin. Not of any use (that I've figured), just a demonstration.

---

### Post by Russty of Oz on 2006-11-10
Ah!  :neutral:

---

### Post by ariel on 2006-11-10
> **Russty of Oz said:**
> OK, I have finally got it to work!  :D 

It  seems that I was missing a line in my /etc/X11/xorg.conf  file.  This was the missing bit:

[B]As far as i know the following is depreciated... although you may as well try with it on and off to see the difference: Add

Option          "TripleBuffer" "true"

to Section "Device" It should help with performance, especially during rain![/B]

By the way, what is "rain"?  (I assume it is not referring to precipitation?):-k

I think Rain comes enabled by default in beryl 0.1.1, try Shift F7 or Shift F8 (I think one should be the rain effect, the other is the wiper).

---

### Post by Russty of Oz on 2006-11-10
I tried Shift F7 & F8 but nothing happened. :-?

---

### Post by HoMe_CaNiBaL on 2006-11-10
Shift F9 and start raining

---

### Post by Russty of Oz on 2006-11-10
Nope!:(   Still nothing, I tried shift and all the F's but nothing at all happens.  Perhaps something need to be enabled.  I will have to try the Beryl Forum and see what I can find out.

---

### Post by PriceChild on 2006-11-10
Thread moved.

beryl is not a beginners subject.

---

### Post by HoMe_CaNiBaL on 2006-11-11
> **Russty of Oz said:**
> Nope!:(   Still nothing, I tried shift and all the F's but nothing at all happens.  Perhaps something need to be enabled.  I will have to try the Beryl Forum and see what I can find out.

go at beryl-manager (right click on beryl icon) and try enabling "water efect"

---

### Post by Russty of Oz on 2006-11-11
Ah!  that did it! :)   Cool, but if I turn the wiper on it goes so fast that I don't get a chance to see much rain.  Oh well.

It is nice to see some rain, seeing as we are in the midst of a drought down here!

---

### Post by alinuxfan on 2006-11-12
I followed the howto and WHAM!  Works great!!

I tried a while back with compiz and I got all confused and it wasn't very pretty looking, kinda jumpy.  I thought, well it must be that fact that I am using an AMD XP 1700 with a NVIDIA GeForce 5200 w/128mb ram and only 1 gig of DDR RAM
Well today, I was thoroughly amazed when it worked smooth and all

(Still doesn't take away from the fact that I need a computer upgrade, but at least it is one success story in the world of failed attempts)

Adam

---

### Post by budman21901 on 2006-11-12
Same exact problem with a Nvidia FX 5500.  Solved problem by installing compiz.  I thought with edgy all i needed was the beta driver, and beryl.  I already had xgl, and aiglx included with edgy.  It wouldn't work without compiz.  Heck, i don't know.  I am a newbie.  I am just glad to get it working.  Works well also!!

---


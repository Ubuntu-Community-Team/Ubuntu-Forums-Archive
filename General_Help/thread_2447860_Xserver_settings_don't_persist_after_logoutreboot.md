---
title: "Xserver settings don't persist after logout/reboot"
date: 2020-07-27
forum: General Help
---

### Post by dakahn on 2020-07-27
Hello! I use a dual monitor setup  with the monitor on the right rotated to the left into portrait mode. I  have to re-rotate my right most monitor in nvidia-settings every time I  log in or reboot. This is pretty frustrating. It's made even more  frustrating by the fact that I actually _somehow_ fixed this problem  once and swapping my second monitor (same make/model) after the old one  started to die brought the problem back.

I  have tried manually deleting xorg.conf and all the backups and then  re-generating new configs with `sudo nvidia-xconfig` and then updating  my settings with `sudo nvidia-settings` but the next time I log out and  log back in -- my monitor has de-rotated.

Funnily  enough (actually very unfunny) after logging out and logging in and  seeing my monitor rotation settings reset if I open up my xorg.conf it  seems like the rotation settings are right where they should be

So my educated guess is that my x  config is getting clobbered somehow on boot and some default rotation  settings are getting loaded in? Not sure where to go from there.
Things worth noting:- My graphics card is a RTX 2060
- My main monitor is DVI and my secondary portrait mode monitor is HDMI
- I'm running Ubuntu 20.04.1 LTS with NVIDIA driver 440
-  NVIDIA Settings seems to be bugged because when I make changes, apply  those changes, update my xorg.conf (through the GUI) and then attempt to  quit it throws a dialog informing me I have unsaved changed and asks me  if I'm sure I want to quit. But if I manually inspect my xorg.conf in  Vim it seems like the settings saved just fine.
-  My Ubuntu display settings seem completely jacked up. Like settiing any  rotation in that UI at all causes the right monitor to totally turn off  and both monitors to be spread on the middle monitor so I'm able to  edge scroll like an RTS. Could be another clue.
Thanks in advance for any help or guidance

---

### Post by SBFree on 2020-07-28
Amazing. Just upgraded to 20.04 and using the NVIDIA driver 440 driver with one landscape and one portrait monitor. I have similar behavior. I hope someone has insights or suggestions for us.

---

### Post by dakahn on 2020-07-29
Hello, fellow suffering dual monitor user. Since it looks like help isn't coming I thought I'd post what I've subsequently found out.
[https://forums.developer.nvidia.com/t/unable-to-save-x-configuration-file/70249/2](https://forums.developer.nvidia.com/t/unable-to-save-x-configuration-file/70249/2)

My sort of educated guess is that something about maybe where xserver/Ubuntu is looking for x configs doesn't sync up with where Nvidia put them? Honestly, as dramatic as it sounds, I'm at my wits end and might just jump ship to another distro that better supports my hardware.

---

### Post by dakahn on 2020-07-29
So I'm stubborn and refuse to admit defeat here. I've got some new clues I thought I'd share:

I happened to be updating a config file in my home directory and noticed a file named .nvidia-settings-rc which seems to simply load in a xinit config from some other part of my system. 

So searching the name of that file led me to the [Ubuntu manpage for nvidia-settings]("https://manpages.ubuntu.com/manpages/bionic/man1/nvidia-settings.1.html") with this juicy tidbit from section 3

       > The  NVIDIA X driver does not preserve values set with **nvidia-settings** between runs of the
       X server (or even between logging in and logging out of X, with **[xdm]("https://manpages.ubuntu.com/manpages/bionic/man1/xdm.1.html")**(1),  **gdm,**  or  **kdm**  ).
       This  is  intentional,  because different users may have different preferences, thus these
       settings are stored on a per-user basis in a configuration file stored in the user's  home
       directory.

       The  configuration  file  is  named  _~/.nvidia-settings-rc_.
...
If you do not already have an _~/.xinitrc_ file, then chances are that **[xinit]("https://manpages.ubuntu.com/manpages/bionic/man1/xinit.1.html")**(1) is  using  a
       system-wide xinitrc file.  This system wide file is typically here:

            /etc/X11/xinit/xinitrc

       To  use  it,  but  also  have  **nvidia-settings**  upload  your settings, you could create an
       _~/.xinitrc_ with the contents:

            nvidia-settings --load-config-only &
            . /etc/X11/xinit/xinitrc
 

Uh, cool. So all this frustration experienced by seemingly hundreds of users for years and years is potentially caused by a feature and not a bug. Gnarly. Reading on it details steps to make your nvidia-settings persistent between sessions
> 
After you have run **nvidia-settings** once and have generated a configuration file,  you  can
then run:

nvidia-settings --load-config-only
...
If you do not already have an _~/.xinitrc_ file, then chances are that **[xinit]("https://manpages.ubuntu.com/manpages/bionic/man1/xinit.1.html")**(1) is  using  a
system-wide xinitrc file.  This system wide file is typically here:

/etc/X11/xinit/xinitrc

To  use  it,  but  also  have  **nvidia-settings**  upload  your settings, you could create an
_~/.xinitrc_ with the contents:
nvidia-settings --load-config-only &
. /etc/X11/xinit/xinitrc 

Following these steps doesn't work -- or seem to do anything for me. So my new question is what is .nvidia-settings-rc and how does it relate to xorg.conf? Is one derived from the other?

---

### Post by CatKiller on 2020-07-29
Bear in mind that I don't use Gnome and I don't use multiple monitors. > **dakahn said:**
> So my new question is what is .nvidia-settings-rc and how does it relate to xorg.conf?

It doesn't, really. 

Xorg.conf sets up devices and their options during the startup process. Since automatic detection is mostly OK these days, it isn't strictly necessary unless there's some particular thing you need to change. These days you can use snippets in xorg.conf.d rather than putting everything into a single file. Also note that the automatically generated xorg.conf from Nvidia's configuration tool is hideous to attempt to read, and specifies a bunch of stuff that it doesn't need to. 

Nvidia-settings-rc is a place to store the runtime settings for the nvidia driver. The nvidia Linux driver is in many ways the nvidia Windows driver made to work on Linux, so it does many things its own way relative to the rest of the graphics stack. As you've found, it doesn't automatically apply them again, so it's only marginally more convenient than specifying the options you want at the command line. It also doesn't store all the settings you can specify in the Nvidia configuration tool: overclocks won't be applied from that file, for example. It's pretty straightforward to load the settings from that file, or specify your own particular settings, when you log in, although the particular method may vary by desktop environment. 

Desktop environments may also have their own methods for setting attributes for the display. Some of them will store those settings in ~/.config/monitors.xml.

You can also change monitor rotation attributes with xrandr, which interfaces with the XRandR (Resize and Rotate) extension to X11. Many of the other tools for configuring display attributes are actually using this extension. If you find a command that works for you, you could run that when you log in rather than working out which configuration file will give you the same effect.

---

### Post by SBFree on 2020-07-30
If I found a XRandR command that worked how would I make this run at login?
Thanks in advance for any thoughts.
scott

---

### Post by SBFree on 2020-07-30
My apologies for replying to my own post. The code:
```
xrandr --output HDMI-0 --rotate left
```
puts my second monitor into portrait but doesn't adjust it's relative position. It looks like getting this to run at login is described at : 
[https://askubuntu.com/questions/270049/how-to-run-a-command-at-login]("https://askubuntu.com/questions/270049/how-to-run-a-command-at-login")

---

### Post by CatKiller on 2020-07-30
> **SBFree said:**
> If I found a XRandR command that worked how would I make this run at login?

Most desktop environments have a setting for automatically running things when you log in.

---

### Post by dakahn on 2020-07-30
Yeah, I went the same route myself with just manually running an Xrandr script at startup.
xrandr --output HDMI-0 --rotate left --pos 1920x-420

Rotates my second monitor left and then positions it down 420px so it's centered relative to my main monitor.

---

### Post by SBFree on 2020-07-31
Did you find a way to make this run at login? I tried adding to the end of ~/.profile but it did not work.

---

### Post by dakahn on 2020-07-31
Yeah I saw that method as well and it totally doesn't work as described. Ended up just adding the script to my Startup Applications Preferences.

---


---
title: "KDE screen blanks"
date: 2008-02-22
forum: General Help
---

### Post by bitmonkey on 2008-02-22
On 2 separate installs of ubuntu on a HP DV9657EM laptop, then doing sudo apt-get install kubuntu-desktop I get a KDE install that I can log into from either kdm or gdm, but after the splash screen where it loads the kde stuff I get to the desktop then about 5 to 10 second later the screen fades to black.

The fade to black takes place over about 2 or 3 seconds.

There is no response to ctrl-alt-f2/f3 etc or to ctrl-alt-del or ctrl-alt-backspace.

Turning off the power then turning it back on again produces a very strange phenomenon - the screen fades to black at the BIOS screen. The only way to fix it is to remove the power and the battery so the laptop is physically reset then start again.

Gnome works fine with ubuntu.

I have tried the opensource nv drivers and the proprietary nvidia ones - the same problem occurs with both.

Has anyone seen this or have any ideas?

thanks.

Paul

---

### Post by kwilliam on 2008-02-22
Wow, that's pretty serious, if it is messing things up so badly the screen fades to black after the BIOS screen.

It sounds similar to what occasionally happens to me when I resume from suspend-to-RAM.  (Suspend works *most* of the time for me, but occasionally does freaky things.)

Instead of Ctrl+Alt+Backspace, have you tried SysRq+R,E,I,S,U,B,O?  ([http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub))  That's kind of a last ditch attempt to turn the computer off nicely.

This doesn't sound like a normal error that could be caused by KDE directly.  If Ctrl+Alt+Backspace isn't working, I think that means something at the kernel or driver error is screwing up.  (And I'm not knowledgable enough to do anything but speculate beyond that.)  For the effect to persist to the next bootup suggests maybe a bios setting is getting changed.  Have you tried looking at the BIOS settings after doing the hard reboot, instead of letting it start booting?  I know my laptop has some screen brightness settings in the BIOS, which is the only thing I can think off that would cause a persistant screen blackening that is fixed by a battery reset.  On the other hand, I don't have much experience with such strange things, except I will say that my screen will occasionally fade to black (or fade to white!) when resume from RAM screws up (however, the problem never persisted between boots).

---

### Post by TVu on 2008-03-18
> **bitmonkey said:**
> On 2 separate installs of ubuntu on a HP DV9657EM laptop, then doing sudo apt-get install kubuntu-desktop I get a KDE install that I can log into from either kdm or gdm, but after the splash screen where it loads the kde stuff I get to the desktop then about 5 to 10 second later the screen fades to black.

The fade to black takes place over about 2 or 3 seconds.

There is no response to ctrl-alt-f2/f3 etc or to ctrl-alt-del or ctrl-alt-backspace.

Turning off the power then turning it back on again produces a very strange phenomenon - the screen fades to black at the BIOS screen. The only way to fix it is to remove the power and the battery so the laptop is physically reset then start again.

Gnome works fine with ubuntu.

I have tried the opensource nv drivers and the proprietary nvidia ones - the same problem occurs with both.

Has anyone seen this or have any ideas?

thanks.

Paul

This is like an exact description of what is happening with my fresh kde-installation. Only difference is that my system is alive and kicking. Perhaps yours is too and you just couldn't see ctrl-alt-backspace logging you off. 

In my case, display is not completely black, it seems like its back light gets gradually adjusted off. It's just barely readable with an ambient light and it is possible to operate the system if only I could see enough. Logging off from kde and logging in to gnome will fix the brightness. Restarting will cause the fading around the time Grub is firing up, power reset with a battery disconnected as an only way to fix it as you described.

Some additional notes: My system is HP pavilion dv9000 with nVidia GF 8400 M GS. I can make this happen even with starting live KDE. HP's Fn+f7 and f8 will adjust brightness with gnome, not with kde. When in kde, running ```
nvidia-settings --assign"Brightness=1"
``` doesn't affect backlight.

As kwilliam suggested, I also believe bios is to blame here. Only bugger is there is no brightness control in dv9000 bios. Could the nVidia be the culprit?

I suppose getting those fn+f8-commands to work would solve the issue. Any suggestions?

---

### Post by TVu on 2008-03-18
OK, seems like I found the solution from the other thread: [http://ubuntuforums.org/showpost.php?p=3698210&postcount=4]("http://ubuntuforums.org/showpost.php?p=3698210&postcount=4")

Blacklisting video in /etc/modprobe.d/blacklist got rid of dimming. Don't know yet what else it got rid off.

---


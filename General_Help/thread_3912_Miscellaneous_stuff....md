---
title: "Miscellaneous stuff..."
date: 2004-11-10
forum: General Help
---

### Post by mark on 2004-11-10
There's a couple of config settings I'm still having problems with - display resolution and the IPv6 problem...

Display - I'm most comfortable with a resolution of 1152x864 on 19" monitor.  I'm able to set this up in other distros (all Xorg, I'm afraid) and Win2K, but not Ubuntu.  I've run *sudo dpkg-reconfigure xserver-xfree86* many times, entering very specific values for video memory (98304KB), horizontal & vertical frequency ranges (30-86KHz and 50-160Hz, respectively), insured that 1152x864 was listed as a supported resolution, etc.  I can get either 1280x1024 or 1024x768 - but I can't split the difference for my "just-right" 1152x864.  I've also manually edited the *XF86Config-4* file & done everything short of deleting all resolutions *but* 1152x864 (that's next!).  My adapter is the Intel 865 "Graphics Extreme" on the D865GLC mainboard (with 1GB of system RAM), the monitor is a MAG Innovision 986FS.  Any suggestions?  (I'll gladly post any config files and/or fragments, as needed...)

IPv6 - This has been going on in a number of posts and I'm still really confused (mainly because I don't really understand IPv6 or tunnelling) - all I know is that quite a few Web sites are very slow to load in Mozilla 1.73 (yeah, I know - but I still prefer it to Firefox).  I've applied the "fix" of editing */etc/modprobe.d/aliases* to turn off PF10 (IPv6); I've also set the Mozilla *about:config* variable *network.dns.disableIPv6* to *true* - to (as far as I can tell) no avail.  If I've done all the fixes to disable IPv6, should I still be seeing an IPv6 address for *eth0* and a *sit0* section when I run *ifconfig -a* ?

Oh, and one last thing (promise!): I had my drive configured with Win2K in hda1 and Ubuntu installed across the remaining primary & extended partitions (/boot, /, /usr, /swap and /home).  I then tried to install Fedora Core 3 (hey, FC2 was my "old" distro!) but it wouldn't partition, saying it needed a primary.  I then redid the installs, with FC3 first (after Win2K) and then Ubuntu - and everything went fine.  Is this a quirk of FC/RH?  Or is a Debian-based distro just more, uh, flexible?

Sorry about the length of the post, but I would like to get these annoyances cleared up.

*Thanks!* 

Mark

---

### Post by JonAtkinson on 2004-11-10
With regards to needing to install on a primary partition, I think that RH/FC has a bit of a hangover from the days of Lilo, which is still present in the anaconda installer. I'm pretty sure that grub can deal fairly elegantly with booting from any partition nowadays.

--Jon

---

### Post by mark on 2004-11-10
Jon, thanks - yeah, I kinda figured that was the case.

BTW - I did edit *XF86Config-4* and delete all resolutions except 1152x864 - now X comes up with same choices as before (no 1152x864) - but it adds 1600x1200...I'm *so* confused....

---

### Post by mark on 2004-11-10
Okay, I'm answering some of my own questions (hey, I'm home with the flu - I gotta find something to take my mind off how bad I feel<g>): re: IPv6.

I went back and *carefully* re-read the mailing list posts about this.  Then I went back and re-edited */etc/modprobe.d/aliases* in this particular: ```
alias net-pf-10 off
``` That's all.  I had in the past *not* deleted the "IPv6" reference at the end of the line.  Oh, and I did run *update-modules* before I rebooted, just as a precaution.  Now, *ifconfig -a* makes no mention of an IPv6 address, nor is there a *sit0* section.

Awright! 1.5 down, 1 to go (the resolution thing)...

---

### Post by Klunk on 2004-11-10
[QUOTE=mark]There's a couple of config settings I'm still having problems with - display resolution and the IPv6 problem...

Display - I'm most comfortable with a resolution of 1152x864 on 19" monitor.  I'm able to set this up in other distros (all Xorg, I'm afraid) and Win2K, but not Ubuntu.  I've run *sudo dpkg-reconfigure xserver-xfree86* many times, entering very specific values for video memory (98304KB), horizontal & vertical frequency ranges (30-86KHz and 50-160Hz, respectively), insured that 1152x864 was listed as a supported resolution, etc.  I can get either 1280x1024 or 1024x768 - but I can't split the difference for my "just-right" 1152x864.  I've also manually edited the *XF86Config-4* file & done everything short of deleting all resolutions *but* 1152x864 (that's next!).  My adapter is the Intel 865 "Graphics Extreme" on the D865GLC mainboard (with 1GB of system RAM), the monitor is a MAG Innovision 986FS.  Any suggestions?  (I'll gladly post any config files and/or fragments, as needed...)

[/QUOTE]

I had trouble with X until I found a post that suggested using xf86setup and copied the XF86Config file over XF86Config-4 (after backup of course). I now have my 1280x1024 resolution I want. My problems were with my graphics card setup and I found the right config with this tool.

---

### Post by mark on 2004-11-10
[QUOTE=Klunk]I had trouble with X until I found a post that suggested using xf86setup and copied the XF86Config file over XF86Config-4 (after backup of course). I now have my 1280x1024 resolution I want. My problems were with my graphics card setup and I found the right config with this tool.[/QUOTE]Thnaks, Klunk.  I don't find *xf86setup* on my system (or through a Synaptic search), but I am playing around with *xf86cfg* now.  If I make any progress (&don't blow up my monitor!), I'll post back on the results.

Mark

---


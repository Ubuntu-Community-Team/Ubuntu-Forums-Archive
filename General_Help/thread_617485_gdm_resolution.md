---
title: "gdm resolution"
date: 2007-11-19
forum: General Help
---

### Post by murdochravlin on 2007-11-19
With Ubuntu 7.10, even though in /etc/X11/xorg.conf I have 

 DefaultDepth    24
        SubSection "Display"
                Modes    "1440x900"  "1024x768" "832x624" "800x600" "720x400" "640x480"

gdm insists on starting at  1280  x 960 :(

Where is gdm getting that resolution from ??????

Also although in test mode lm-sensors gives the correct information with gkrellm -12V and -5V values are incorrect. In text mode - -12V and -5V values indicate  "(reserved)" whatever that means ?????

---

### Post by por100pre1 on 2007-11-19
It is a bug, please read [this]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146828").

---

### Post by murdochravlin on 2007-11-19
Above solution does not apply. 
I suspect there is a problem with the way X or some of its components, or the defaults used when they were compiled. I have a Radeon 9200 and am using the open source drivers.

From somewhere I was getting a  Virtual 1792    1344 in my xorg.conf, but I removed it.
I suspect it really does not have anything to do with gdm or even xorg.conf, as just starting with X starts up at 1280  x 960. However after I did  displayconfig-gtk in gnome (which rewrites xorg.conf every time it is used), once gnome starts up it is at the correct resolution. My problem is, I like to use fluxbox and it automatically starts up a the same resolution as gdm. I can however use gnome-display-properties to set the resolution to the preferred 1440x900 every time I start, but it is a PAIN.

---

### Post by murdochravlin on 2008-02-16
Problem fixed but whoever is setting up the X server to ignore 
/etc/X11/xorg.conf should  get it right or please desist 

in  .fluxbox/startup I added the line 

xrandr -s 1440x900

just before the line 
exec /usr/bin/fluxbox

and as sudo in /usr/bin/wmaker i put the same thing just before

exec "$WindowMaker" "$@"

most likely there is someplace to fix gdm also but as it is viewable for me
I left it alone

---


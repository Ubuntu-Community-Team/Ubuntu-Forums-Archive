---
title: "troubleshooting a video-driver issue"
date: 2015-01-20
forum: General Help
---

### Post by thatstheway on 2015-01-20
I recently installed 12.04.5 on a [Toshiba Portege r100]("http://www.cnet.com/products/toshiba-portege-r100/specs/") with 1.25GB RAM and a Trident [COLOR=#000000][FONT=Arial]Microsystems [COLOR=#000000][FONT=Arial]CyberBlade[/FONT][/COLOR] [/FONT][/COLOR]XP4m32 graphics processor [COLOR=#000000][FONT=Arial](rev 91) [/FONT][/COLOR]with 32 MB RAM. To get the latest kernel, I used [fake-pae]("http://ubuntuforums.org/showthread.php?t=2113826&page=2&p=12504589#post12504589"). For about two years I had 12.04.2 running happily on this machine, using the xserver-xorg-video-trident driver. I had to install that driver myself, because it didn't come on the initial install, and that was my particular fix for the persnickety [low-graphics-mode]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error") problem. (I reinstalled due to a hard-disk meltdown.)

This time around, I booted up, got the low-graphics mode problem, and so I installed the driver as I did before (since that worked before), but this time, after returning no errors it said something like "Note, using xserver-xorg-video-trident-lts-trusty instead."

I rebooted, and got the low-graphics mode error, so I removed xserver-xorg-video-trident-lts-trusty, presumably forcing the switch to xserver-xorg-video-trident, and I booted up fine. However while installing a bunch of updates the screen just went dark, and I had no options but to reboot, which gave me a bad feeling about deleting xserver-xorg-video-trident-lts-trusty.

So I removed xserver-xorg-video trident, reinstalled xserver-xorg-video-trident-lts-trusty, and did another thing that has worked in the past: I created a .conf file according to [these steps]("https://wiki.archlinux.org/index.php/Trident"), and enabled a few of the options until it booted without getting the low-graphics mode error, which is where I am now. 

3 problems with that:
[LIST]
[*]The Gnome-Terminal is always transparent with white text, so I can't use it unless it's all alone on on a dark background. Configuring it using the preferences (solid background, transparent background with 0 transparency) has no effect. In the screenshot below, see how it looks on this forum. XTerm and UXTerm look fine. 
[*]In the Wordpress admin page, some menus are also transparent with white text. Sounds random, but I'm sure it's related. 
[*]Graphics overall are very slow. Window drawing, cursor movement, etc. 
[/LIST]

I tried returning to the other driver, xserver-xorg-video-trident, since I think things were fine using that (except for when the screen went dark, but it's possible that was a one-time event), but, after so many updates, this time, when I tried to install it, I was stopped by unmet dependency errors. It said that it needed
[LIST]
[*]xorg-video-abi-11, which is in the one below, and 
[*]xserver-xorg-core, which Synaptic shows as not installed, and if I mark it for installation, it says it wants to remove a whole bunch of stuff, and I'm reluctant to that. Further, a package-details site told me that this one is in xserver-xorg-core-lts-trusty, which Synaptic tells me is installed. So I'm baffled. I also tried installing this via the terminal, but got errors. Unfortunately I didn't capture these. 
[/LIST]

I tried jockey-text --list, but after working a long time, it didn't return anything. Shouldn't it? 

Questions:

[LIST]
[*]How can I know which video driver I'm using? Is there something I need to do to get jockey-text running correctly? 
[*]How can I switch from xserver-xorg-video-trident-lts-trusty to xserver-xorg-video-trident, to see what changes? Is that a bad idea? I *think* graphics were fine using that driver, and I'd like to test that out. 
[*]Should I look into more ways to configure the current driver rather than looking to switch drivers? Other ideas? 
[/LIST]

Any help would be most appreciated! 

[IMG]http://www.davidweiss.net/wp-content/uploads/2015/01/Screenshot-from-2015-01-19-212420.png[/IMG]

---

### Post by thatstheway on 2015-01-21
Success! 

I got brave and used Synaptic to install xserver-xorg-core, and let it remove whatever it wanted to remove, including xserver-xorg-core-lts-trusy. 

Rebooted, and got no change. 

So I deleted the config file I wrote to get xserver-xorg-core-lts-trusy to work, and everything now is fine: the terminal, the seemingly random wordpress issue, and the all-important graphics-speed-and-performance issue. :p

---


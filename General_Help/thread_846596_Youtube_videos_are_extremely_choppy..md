---
title: "Youtube videos are extremely choppy."
date: 2008-07-01
forum: General Help
---

### Post by Famicommander on 2008-07-01
I am running Xubuntu 8.04 on a KDS Valiant 6184 laptop. It has an 800mhz Pentium III processor, 256 MB of PC100 RAM, a 20 GB hard drive, and 8 MB of shared video RAM. I had major video issues a few days ago, but was able to solve them thanks to you guys. I don't know my specific video card, but here's the thread that got my video issues fixed:
[http://ubuntuforums.org/showthread.php?t=843061](http://ubuntuforums.org/showthread.php?t=843061)

I know that my video card can handle it, because when this laptop had Windows ME I was able to watch streaming media. I am also able to watch fullscreen DVDs on Xubuntu without any issues.

So, how might I be able to get streaming and flash videos to stream smoothly? Is this a driver issue? Would throwing in another 128 MB (that's the most I want to pay for; PC100 laptop RAM is crazy expensive seeing as I only paid 25 dollars for this whole laptop) fix the issue?

Also, while we're on the topic, would adding more RAM take some of the load off my CPU? I seem to be perpetually running at 25-60% CPU usage, even after disabling many of the GNOME processes.

Any help and advice would be much appreciated.

---

### Post by kevmitch on 2008-07-01
Unfortunately, flash in Linux is a bit of a disaster at the moment. Well, actually flash period is a bit of a disaster, but that's getting off topic. The gnu flash player (gnash) looks promising especially now that it supports youtube, but it needs a little more time to mature. 

In the meantime, I trust you're using the Adobe flash player (flashplugin-nonfree)?

I'm also guessing based on your hardware that you're running i386? That's probably recommended for best flash performance as the nsplugin emulator can slow things down a bit.

If you answered yes to the above questions, what version of flash are you running? You can determine this by typing "about:plugins" into the Firefox address bar or "apt-cache policy flashplugin-nonfree" on the command line.

You could try upgrading to flash 10 
[http://linuxondesktop.blogspot.com/2008/05/installing-adobe-flash-player-10-beta.html](http://linuxondesktop.blogspot.com/2008/05/installing-adobe-flash-player-10-beta.html)

or given your older hardware, downgrading might even be of some benefit. 

You could even give gnash a try. It has come a long way in the past few months. Just make sure you're runnning at least version 8.2 (that's when it started supporting youtube), but you're probably best using the bleeding edge 8.3, or better yet, download and compile the latest upstream [http://www.gnu.org/software/gnash/#downloading](http://www.gnu.org/software/gnash/#downloading).

Finally, you might try playing around with upgrading/downgrading the xserver-xorg and xserver-xorg-core packages.

In regards to the cpu usage, let's have a look at
```
/bin/ps -A -o user,%cpu,%mem,cmd --sort -%cpu
```

---

### Post by Famicommander on 2008-07-01
It appears that I am running Flash 9.0:
```
jason@ubuntu:~$ apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 9.0.124.0ubuntu2
  Candidate: 9.0.124.0ubuntu2
  Version table:
 *** 9.0.124.0ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/multiverse Packages
        100 /var/lib/dpkg/status
```
I'll try the newer version and see how it goes first.

Regarding the CPU usage:
```

jason@ubuntu:~$ /bin/ps -A -o user,%cpu,%mem,cmd --sort -%cpu
USER     %CPU %MEM CMD
root     16.9  9.9 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolis
jason    11.8 30.9 /usr/lib/opera/9.50/opera
jason     1.4  7.6 xfce4-terminal
jason     0.4  1.2 bash
jason     0.3  4.7 /usr/lib/opera/9.50/operapluginwrapper 22 28 /usr/lib/mozilla
jason     0.2 10.7 pidgin
jason     0.2  3.2 nm-applet --sm-disable
jason     0.1  4.0 xfce4-panel --sm-client-id 117f000101000121462013900000052110
jason     0.1  4.4 /usr/lib/xfce4/panel-plugins/xfce4-menu-plugin socket_id 2097
jason     0.1  4.3 xfwm4 --sm-client-id 117f000101000121462013800000052110000 --
jason     0.0  3.6 xfdesktop --sm-client-id 117f00010100012146201460000005211000
root      0.0  0.6 /sbin/init
jason     0.0  6.3 Thunar --sm-client-id 117f000101000121462014000000052110002 -
jason     0.0  2.6 x-session-manager
jason     0.0  2.1 xfce-mcs-manager
root      0.0  0.1 /sbin/udevd --daemon
root      0.0  0.4 hald-addon-storage: polling /dev/hdc (every 2 sec)
jason     0.0  5.0 update-notifier --sm-config-prefix /update-notifier-97aHU0/ -
jason     0.0  2.2 gnome-power-manager --sm-config-prefix /gnome-power-manager-F
root      0.0  0.0 [kswapd0]
110       0.0  0.9 /usr/sbin/hald
jason     0.0  3.6 /usr/lib/xfce4-places-plugin/xfce4/panel-plugins/xfce4-places
root      0.0  0.2 /usr/sbin/dhcdbd --system
jason     0.0  0.9 /usr/lib/libgconf2-4/gconfd-2 14
root      0.0  0.0 [kjournald]
jason     0.0  2.6 /usr/lib/thunar/xfce4/panel-plugins/thunar-tpa socket_id 2097
root      0.0  0.4 hald-addon-input: Listening on /dev/input/event1 /dev/input/e
klog      0.0  0.8 /sbin/klogd -P /var/run/klogd/kmsg
107       0.0  0.4 /usr/bin/dbus-daemon --system
jason     0.0  0.5 /usr/lib/gamin/gam_server
root      0.0  0.0 [events/0]
root      0.0  0.0 [pdflush]
jason     0.0  0.3 /usr/bin/dbus-daemon --fork --print-pid 10 --print-address 12
root      0.0  1.0 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
110       0.0  0.3 /usr/lib/hal/hald-addon-acpi
jason     0.0  1.3 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
root      0.0  0.0 [kblockd/0]
root      0.0  0.7 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/N
avahi     0.0  0.5 avahi-daemon: running [ubuntu.local]
root      0.0  0.0 [pdflush]
jason     0.0  0.2 /usr/lib/opera/9.50/operaplugincleaner 5220
syslog    0.0  0.2 /sbin/syslogd -u syslog
root      0.0  0.2 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
root      0.0  0.9 /usr/sbin/console-kit-daemon
root      0.0  0.4 hald-runner
root      0.0  0.0 [khelper]
jason     0.0  0.2 /usr/bin/ssh-agent x-session-manager
root      0.0  0.5 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      0.0  0.0 [kthreadd]
root      0.0  0.0 [migration/0]
root      0.0  0.0 [ksoftirqd/0]
root      0.0  0.0 [watchdog/0]
root      0.0  0.0 [kacpid]
root      0.0  0.0 [kacpi_notify]
root      0.0  0.0 [kseriod]
root      0.0  0.0 [aio/0]
root      0.0  0.0 [ksuspend_usbd]
root      0.0  0.0 [khubd]
root      0.0  0.0 [ata/0]
root      0.0  0.0 [ata_aux]
root      0.0  0.0 [pccardd]
root      0.0  0.0 [kpsmoused]
dhcp      0.0  0.1 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf
root      0.0  0.2 /sbin/getty 38400 tty4
root      0.0  0.2 /sbin/getty 38400 tty5
root      0.0  0.2 /sbin/getty 38400 tty2
root      0.0  0.2 /sbin/getty 38400 tty3
root      0.0  0.2 /sbin/getty 38400 tty6
root      0.0  0.0 [kondemand/0]
root      0.0  0.5 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/Networ
root      0.0  0.4 /usr/bin/system-tools-backends
avahi     0.0  0.1 avahi-daemon: chroot helper
root      0.0  0.3 /usr/sbin/cron
root      0.0  0.1 /sbin/getty 38400 tty1
jason     0.0  0.1 dbus-launch --autolaunch 299b9a173aced7ba037317164865a1c8 --b
jason     0.0  0.3 gnome-pty-helper
jason     0.0  0.3 /bin/ps -A -o user,%cpu,%mem,cmd --sort -%cpu
jason@ubuntu:~$ 
```

---

### Post by Famicommander on 2008-07-01
Two issues with Flash 10:
1. It's as choppy as ever in Firefox
2. It doesn't work at all in Opera

I refuse to use the memory-sucking, overrated, slow piece of garbage that is Firefox. Opera compatibility is an absolute must.

That said, is there a .deb for gnash, and is it Opera compatibile?

---

### Post by kevmitch on 2008-07-01
It looks like it's your xserver that's responsible for the CPU usage. Are there any animations or anything running in opera? If not, playing around with the version of the xserver you're running might be worthwhile.

Are you trying flash in opera or firefox? I ask because it looks like you're running a plugin wrapper which is likely how it would handle flash. Anything with "wrapper" in the name is usually the first thing to check when you're having performance issues. How does flash run in firefox? You might want to try both versions 2 and 3.

---

### Post by Famicommander on 2008-07-01
Went back to Flash 9, and it's still choppy. It's even choppy when I let the whole video buffer before playing it.

---

### Post by Famicommander on 2008-07-01
> **kevmitch said:**
> It looks like it's your xserver that's responsible for the CPU usage. Are there any animations or anything running in opera? If not, playing around with the version of the xserver you're running might be worthwhile.

Are you trying flash in opera or firefox? I ask because it looks like you're running a plugin wrapper which is likely how it would handle flash. Anything with "wrapper" in the name is usually the first thing to check when you're having performance issues. How does flash run in firefox? You might want to try both versions 2 and 3.
Flash 9 is bad in Opera and worse in Firefox.

Flash 10 is terrible in Firefox and non-working in Opera.

---

### Post by Famicommander on 2008-07-01
Also, I had a lot going on when I posted the output of that CPU command. Four or five Opera tabs, two Pidgin chats, and Terminal.

But even when I have nothing else except System Monitor running my CPU usage is at about 30%.

---

### Post by kevmitch on 2008-07-01
Yeah, gnash should be in the repositories. I imagine that you'd want to install mozilla-plugin-gnash which might be used through the wrapper in a similar way to flashplugin-nonfree, though I'm not sure. I have however found that installing the very latest version from source gives the best results. You'll probably also want to uninstall flashplugin-nonfree while you're trying gnash just to make sure that that is indeed what you're using. 

How does your CPU look when you're playing flash? My guess is that if flash itself isn't working at 100%cpu, then the xserver is.

---

### Post by kevmitch on 2008-07-01
Are you running firefox 2 or 3?

---

### Post by Famicommander on 2008-07-01
> **kevmitch said:**
> Yeah, gnash should be in the repositories. I imagine that you'd want to install mozilla-plugin-gnash which might be used through the wrapper in a similar way to flashplugin-nonfree, though I'm not sure. I have however found that installing the very latest version from source gives the best results. You'll probably also want to uninstall flashplugin-nonfree while you're trying gnash just to make sure that that is indeed what you're using. 

How does your CPU look when you're playing flash? My guess is that if flash itself isn't working at 100%cpu, then the xserver is.
Opera plugin wrapper is taking about 48% when playing flash. The rest is being used by the GNOME System Monitor, for a total of about 92%.

I'm about to install gnash.

---

### Post by Famicommander on 2008-07-01
> **kevmitch said:**
> Are you running firefox 2 or 3?
Firefox 3. 

Also, the same issues are present in Konqueror.

---

### Post by Famicommander on 2008-07-01
gnash was a no-go. I removed the flashplugin-nonfree and installed gnash+mozilla plugin, and youtube kept telling me that I needed to install a flash plugin. I restarted Firefox, tried Opera, and tried the Konqueror plugin too. Nothing worked.

Additionally, gnash wouldn't open at all from the Multimedia menu or Terminal.

---

### Post by Famicommander on 2008-07-01
Does anyone else have any ideas?

Do you think that adding more RAM would help?

---

### Post by kevmitch on 2008-07-01
Adding more RAM might help, but I don't think it's the main problem. What does 
"free -m" look like?

CPU usage appears to be the culprit. Like I said, downgrading the xserver would probably be the best bet. You might need to add older releases to your /etc/apt/sources.list, but the sure fire way is to just install an older release [http://releases.ubuntu.com/](http://releases.ubuntu.com/). You might even want to try an even lighter weight window manager than xfce like blackbox, fluxbox, or blackbox.

---

### Post by Famicommander on 2008-07-01
> **kevmitch said:**
> Adding more RAM might help, but I don't think it's the main problem. What does 
"free -m" look like?

CPU usage appears to be the culprit. Like I said, downgrading the xserver would probably be the best bet. You might need to add older releases to your /etc/apt/sources.list, but the sure fire way is to just install an older release [http://releases.ubuntu.com/](http://releases.ubuntu.com/). You might even want to try an even lighter weight window manager than xfce like blackbox, fluxbox, or blackbox.
It has nothing to do with CPU usage. I've had Fluxbox and OpenBox running since before I made this topic. Same problem, same choppiness. 

This has to be a video driver issue. You probably would've noticed the ridiculous amount of trouble I had to go through to get my video settings right if you'd read my original post and the link provided therein. There's no way I'm going back to Feisty or Gutsy just for the purpose of Youtube videos and risk screwing up my video settings.

---

### Post by Famicommander on 2008-07-01
Does anyone else have any ideas?

---

### Post by Famicommander on 2008-07-01
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver       	"trident"
	Option	"Monitor-VGA"	"My Monitor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-70
	VertRefresh	50-120
	Option    "DPMS"
	Modeline	"1024x768"  64.11  1024 1080 1184 1344  768 769 772 795 -HSync +Vsync
	Option	"PreferredMode"	"1024x768" 
EndSection
```

That's what my xorg.conf looks like. Does it offer any clues?

---

### Post by clparker on 2008-07-09
What's The Deal? It's Just Flash, It Shouldn't Be Running This Poorly!!!

---

### Post by das867 on 2009-02-19
ya i'm having the same problem on my box. i'm running ubuntu 8.04 with opera 9.63 and adobe flash player 10.0.12.something, i've noticed the same problem in both firefox and opera, but i've noticed the choppyness is mostly noticable in embeded videos and it helps when i move the mouse over the video screen quickly (maybe a problem with the hard coded refresh rate? i dunno really) i also notice the its not just youtube, its also metacafe, vimeo, myspace video and others. i wonder if anyone has fixed this yet? and does anyone have any new news on gnash, like is it useable yet?

---

### Post by lorddresefer on 2009-08-25
the system monitor takes up cpu.    i have very similar specs and youtube runs terrible.  try using a lighter window manager like lxde

---

### Post by badrra on 2009-12-16
Try this one. Works great and no choppiness. 

[http://badrra.wordpress.com/category/firefox/](http://badrra.wordpress.com/category/firefox/)

---


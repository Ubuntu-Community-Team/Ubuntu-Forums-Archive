---
title: "Slow starting of apps in fresh 18.04 install"
date: 2018-04-30
forum: General Help
---

### Post by mexp on 2018-04-30
I did a fresh minimal install of Ubuntu 18.04, and now the apps open very slow when I first open them, even small apps like Gedit and VLC. Spotify takes ages. 

Second time around the starting time seems more reasonable. I used 17.10 prior to this, and there was no such a problem. 

What could be the issue?

I added preload and TLP, it's a laptop I'm using.

Lenovo Thinkpad E540, i3 with 8 GB of RAM.

---

### Post by Claus7 on 2018-04-30
Hello,

1st attempt:
```
$ time gedit
```

real	0m4,284s
user	0m0,344s
sys	0m0,093s

2nd:

real	0m5,747s
user	0m0,409s
sys	0m0,043s

3rd:
real	0m3,606s
user	0m0,379s
sys	0m0,068s

4th:
real	0m4,584s
user	0m0,367s
sys	0m0,076s

Have you checked memory usage? I do not face such a problem. My applications respond pretty fast.
Also I would try to open them via terminal in case any errors appear.

Regards!

---

### Post by mexp on 2018-05-01
Ok, thanks, I did not know of "time" command.

Gedit opens fast now, but Spotify is miserable. Probably because of failed load of modules?

@ThinkPad-E540:~$ time spotify
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option force_s3tc_enable overridden by environment.

real	0m18,902s
user	0m2,536s
sys	0m7,214s

@ThinkPad-E540:~$ time spotify
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option force_s3tc_enable overridden by environment.

real	0m6,683s
user	0m2,309s
sys	0m0,458s

**VLC**

@ThinkPad-E540:~$ time vlc
VLC media player 3.0.1 Vetinari (revision 3.0.1-4-g14a4897)
[0000000001cfb4c0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Qt: Session management error: None of the authentication protocols specified are supported
[0000000001d9c170] main playlist: playlist is empty
QObject::~QObject: Timers cannot be stopped from another thread

real	0m9,620s
user	0m0,572s
sys	0m3,099s
@ThinkPad-E540:~$ time vlc
VLC media player 3.0.1 Vetinari (revision 3.0.1-4-g14a4897)
[0000000000a824c0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Qt: Session management error: None of the authentication protocols specified are supported
[0000000000b23170] main playlist: playlist is empty
QObject::~QObject: Timers cannot be stopped from another thread

real	0m2,859s
user	0m0,633s
sys	0m0,129s

---

### Post by mexp on 2018-05-01
Memory usage seems to be at around 20-25%, 2 GB out of 7,5, no swap at all.

---

### Post by mc4man on 2018-05-01
If you are using snap versions of apps then the first opening per session will be considerably slower than subsequent opens.
Most likely spotify & vlc are snap versions, you can check with this, look for an installed line, ex. vlc 
snap info vlc

---

### Post by Claus7 on 2018-05-01
Hello,

it is already mentioned (^) that these versions of programs are (most probably) snap ones. I did not expect them to be slower though. Why don't you try to use vlc at least from synaptic? Spotify I do not use, so I cannot tell.

To view all your snap packages do:
```
snap list
```

Have you upgraded them to their latest version at least? I was able to find out that snap packages are updated (usually) by themselves, yet you could try:
sudo snap refresh <snap package name>

Concerning vlc here is my output:
> $ time vlc
VLC media player 3.0.1 Vetinari (revision 3.0.1-0-gec0f700fcc)
[000055aefe3c2630] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[000055aefe3c65a0] main playlist: playlist is empty
QObject::~QObject: Timers cannot be stopped from another thread

real	0m7,384s
user	0m0,366s
sys	0m0,117s

so no qt error.

You could try also to remove them and install them back to see if this will fix your problem.

Regards!

---

### Post by mexp on 2018-05-01
Yes, VLC and Spotify are Snap.

I'll change that, probably it helps. 

These other entries  were installed by default, so I guess better to leave them alone.

@ThinkPad-E540:~$ snap list
Name                  Version                  Rev   Tracking  Developer  Notes
core                  16-2.32.5                4486  stable    canonical  core
gnome-3-26-1604       3.26.0                   62    stable/&#8230;  canonical  -
gnome-calculator      3.28.1                   167   stable/&#8230;  canonical  -
gnome-characters      3.28.0                   86    stable/&#8230;  canonical  -
gnome-logs            3.28.0                   31    stable/&#8230;  canonical  -
gnome-system-monitor  3.26.0                   39    stable/&#8230;  canonical  -
spotify               1.0.77.338.g758ebd78-41  13    stable    spotify    -
vlc                   3.0.1-4-g14a4897         190   stable    videolan   -

---

### Post by Claus7 on 2018-05-01
Hello,

when I type the same command there is no output for me, since as I mentioned, I do not have any snap packages installed.
I searched your posted packages in *synaptic* and the ones I have as well are the following:
> **mexp said:**
> 
$ snap list
Name                  Version                  Rev   Tracking  Developer  Notes
gnome-calculator      3.28.1                   167   stable/…  canonical  -
gnome-characters      3.28.0                   86    stable/…  canonical  -
gnome-logs            3.28.0                   31    stable/…  canonical  -
gnome-system-monitor  3.26.0                   39    stable/…  canonical  -


which I think that is good to have as deb files, since you notice that they are slowing you down.
Also, taking for example the gnome-system-monitor, the version that is mentioned is 3.28.1-1, which seems to be newer than the one I can see in your list. I do not have the others in my system.

Regards!

---

### Post by mexp on 2018-05-01
Ok, good to know.

So I could just remove these and reinstall through apt-get or Software center?

Probably I would mess up the system if I remove these, though...

core 16-2.32.5 4486 stable canonical core
gnome-3-26-1604 3.26.0 62 stable/&#8230; canonical -

---

### Post by Claus7 on 2018-05-01
Hello,

> **mexp said:**
> Ok, good to know.

So I could just remove these and reinstall through apt-get or Software center?


yes! I prefer synaptic. Actually, if you have snaps installed, I'm not so sure that using software center the applications installed this way won't be snap ones. You could check it out.

> **mexp said:**
> 
Probably I would mess up the system if I remove these, though...

core 16-2.32.5 4486 stable canonical core
gnome-3-26-1604 3.26.0 62 stable/… canonical -

I do not know what they do...

Regards!

---

### Post by mc4man on 2018-05-01
I don't have snapd on my main 18.04 install but looking at a secondary install things have improved in recent times.
So the slow opening should only occur on the first run of a snap ever, not per session. After that they should open in a reasonably fast time similar to a .deb.
(the increased time on first ever run (per user) is probably taken by creating the folders/files for that snap in ~/snap

As far as spotify, in 18.04 I believe your only choice is the snap as atm it uses a curl version not in 18.04

---

### Post by mexp on 2018-05-02
It really looks like the slow start up happens every time the computer is restarted.

Like this:

@ThinkPad-E540:~$ time gnome-calculator 

real	0m6,010s
user	0m0,312s
sys	0m1,866s
@ThinkPad-E540:~$ time gnome-calculator 

real	0m2,573s
user	0m0,315s
sys	0m0,130s
@ThinkPad-E540:~$ time gnome-calculator 

real	0m1,919s
user	0m0,320s
sys	0m0,133s
sannala@ThinkPad-E540:~$
@ThinkPad-E540:~$ time gedit

real	0m3,971s
user	0m0,376s
sys	0m0,036s
@ThinkPad-E540:~$ time firefox

real	0m6,076s
user	0m9,332s
sys	0m0,853s
@ThinkPad-E540:~$ 

So even Firefox feels to open "snappier" than Gnome Calculator...

But it looks like gnome-3-26-1604 is the desktop package, how to install this as deb without breaking the system?

Or how would it be possible to install the system without Snap altogether?

---

### Post by Holger_Gehrke on 2018-05-02
I don't think the gnome snap is the gnome used by the system. snaps can depend on other snaps (they're calling it 'slots' and 'plugs', but it is just old-fashioned dependencies with a bit of abstraction on top). You can easily check either in synaptic for the meta-package 'gnome' and it's dependencies or do an 'apt show gnome' and then do a 'dpkg-query -l' for all it's many dependencies.

Holger

---


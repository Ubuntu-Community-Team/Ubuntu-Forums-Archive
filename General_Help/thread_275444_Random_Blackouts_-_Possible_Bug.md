---
title: "Random Blackouts - Possible Bug?"
date: 2006-10-11
forum: General Help
---

### Post by drezha on 2006-10-11
Hi all, first post and probably in the wrong place.

I'm running Dapper Drake and something's been happening to get me quite annoyed (espcially as I left MS because linux is supposed to be more stable)

Anyhow, at random points, the screen will go blank. As in completly. The screen displays a message something like "No data is being recieved" which is exactly what it says if the screens on and the PC's off.

Now the PC stays on (lights still on at least) but doing anything with the keys doesn't work. I haven't really noticed a pattern about this. Only way to get the screen back is to restart the machine via the off button on the front (not nice). Unplugging the screen doesn't work or anything.

Anyhow, I thought maybe it was the nVidia drivers. But today it happened again (first time for 3 days since I installed the nVidia drivers and reinstalled Ubuntu) and I'm thinking I may have found the culprit...

I'd visted a site with Java chatroom and it happened to crash about a 10 minutes after I left the site.

When I restarted I found this log file in my home folder
[hs_err_pid6621.log]("http://www.drezha.net/files/hs_err_pid6621.log")

Now I'm thinking this maybe the problem.From the log does this prve it or not?  Has anyone else had any bother with Java at all? To uninstall Java wouldn't be very helpful because I use Frostwire everynow and then(wasn't on when this happened mind)

---

### Post by skymt on 2006-10-11
Sounds like a hardware problem. Is your graphics card integrated into the motherboard? If not, is it well seated in the slot? Either way, are you using Beryl/Compiz?

There's no way the Java crash could have caused this problem.

---

### Post by drezha on 2006-10-11
it's a nVidia 6200

Yes it's in fine. No Beryl/Compiz, just the plain standard Ubuntu one with the nVidia stuff downloaded.

Been running other version's of Linux no probs (FC5, Damn Small) and Windows I've had no problems what so ever (and if I can't fix this on Ubuntu I'll have to go back to them and figure out the bits that made me come back to Ubuntu)

Had no trouble whatso ever with 5.10 Ubuntu or before.

Was told elsewhere that the log is a Java Segmentation error. That wonldn't have an effect?:-k

---

### Post by AgenT on 2006-10-11
If this did not happen on another Linux distribution, then the reason is that what Ubuntu uses is either an older or a newer version of the software that crashes your computer. On the other distributions, were you running the closed source NVIDIA drivers? Whatever the case may be, it means the chances are very high it is fixable.

It is recommended that you do NOT use the NVIDIA drivers which are closed sourcce, but instead the open source xorg drivers for your NVIDIA card if possible. Basically, if you do not need amazing 3D acceleration for playing games (or 3D design), then there is little if any reason to use the NVIDIA drivers. The problem with NVIDIA drivers is that they are closed source and you are stuck with a problem/bug that is caused by them until NVIDIA fixes it for you (may be a LONG time). If using the open source drivers, you can submit bug reports and there is a good chance someone will fix it for you within a reasonable time period.

You java log file does seem ti indicate a java crash.

Please do the following:
attach a copy of your xorg.conf found in /etc/X11/
post, in code tags, the result of (from terminal): cat /proc/version
post, in code tags, the result of (from terminal): update-java-alternatives -l
mention how you installed java and your nvidia drivers

You may also try searching the [Ubuntu section on launchpad]("https://launchpad.net/distros/ubuntu") [click bugs, then search for 'nvidia' or something similar].

---

### Post by drezha on 2006-10-11
Right attached my Xorg.conf (saved as a txt file so I can upload it)

Here's the cat /proc/version output:
```
Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006

```

Java bit:
```
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-gcj 1041 /usr/lib/jvm/java-gcj

```

I installed Java by using the following:
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

and the nvidia drivers with:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
```


No I don't really play games (maybe the Gnome ones included every now and then) but part of the reason for moving to linux was to avoid playing games.( And thus help increase my uni marks :lol: )
The reason I installed the Java drivers was because when typing the cursour sometimes sticks where it is or starts having multiple ones (with only one that works but the others are ghosts)

---

### Post by AgenT on 2006-10-12
First, make sure that this is not a cable problem. It may be that your cable is not connected to your video card or your monitor. Try moving your cable around when you get the blank screen.

Second, this does not look like a JAVA problem. 

> **drezha said:**
> No I don't really play games (maybe the Gnome ones included every now and then) but part of the reason for moving to linux was to avoid playing games.
So why are you installing the closed source binary NVIDIA drivers? Why are you using drivers that are causing you problems when you do not have to? Why not just use the open source drivers for NVIDIA cards and be happy? 

Using open source drivers has another advantage: they never have to be installed or reinstalled by you when an update happens - this is done automatically. 

Suggestion for you: remove the closed-source binary NVIDIA drivers and use the open source xserver-xorg nvidia drivers. You will have to either edit your xorg.conf by hand or use dpkg-reconfigure. If you need help with this, ask.

---

### Post by drezha on 2006-10-13
It says in Synaptic that xserver-xorg nvidia drivers are already installed. I guess I would like a hand to edit these then please.

I've now removed the nVidia drivers as it just crashed/blacked out again. Not sure what it is because the music I was listening to stopped as well..so it might not just be a graphics problem.

I'm not that happy with the standard set that you get when you install Ubuntu because as I said, it ghosts the cursour at times and when I'm typing up my weekly lab reports, it drives me crazy.

Only other reason I think it might be messing about is because I removed powernowd. It wasn't upping itself for a process that needs 100% of the full speed CPU and because this was low nice, it iognored it.

---

### Post by AgenT on 2006-10-13
> **drezha said:**
> It says in Synaptic that xserver-xorg nvidia drivers are already installed. I guess I would like a hand to edit these then please.

I've now removed the nVidia drivers as it just crashed/blacked out again. Not sure what it is because the music I was listening to stopped as well..so it might not just be a graphics problem.

I'm not that happy with the standard set that you get when you install Ubuntu because as I said, it ghosts the cursour at times and when I'm typing up my weekly lab reports, it drives me crazy.

Only other reason I think it might be messing about is because I removed powernowd. It wasn't upping itself for a process that needs 100% of the full speed CPU and because this was low nice, it iognored it.
You removed your closed source drivers, so hopefully the configuration for the open source drivers was setup for you. Either that, or hopefully you did not reboot.

Please be advised that these instructions are not tested.

To activate your open source drivers, make sure you have the xserver-xorg-video-nv package installed. Then, locate your xorg.conf file and locate this section:
```
Section "Device"
    Identifier    "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
EndSection
```Replace the line "Driver" "nvidia" with this:
```
    Driver        "nv"
```
Either restart Xorg manually or reboot.

As per the ghosting issue: have you checked this forum and launchpad to see if anyone else is suffering from this? It may be that something is misconfigured.

---

### Post by drezha on 2006-10-13
It's already set like that so I assume it means that the drivers were setup when I removed them.

As for the ghosting, no I haven't. I will now.

I currently think the matters sorted. (at least until it happens again)

---


---
title: "ubuntu boot time - snapd.service"
date: 2020-02-10
forum: General Help
---

### Post by yaminb on 2020-02-10
Hi all,

I've been working on my system's boot time and have improved it a lot.
Right now, I'm working on the snapd.service.

I have a pretty decent system. Core i5, 16 GB ram, 7200 RPM HD...
Running 19.10

Is 17 seconds snapd.service 'normal' I've seen it as high as 45 seconds on mine. This is just the latest printout right now.
As luck would have it when I decide to write the port, there come to be 2 services that come higher on blame, but this was the case before :)

Are there any options I could try, like delaying loading/mounting of SNAPS until they're required?


```
systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @1min 2.637s
&#9492;&#9472;multi-user.target @1min 2.637s
  &#9492;&#9472;snapd.seeded.service @38.249s +253ms
    &#9492;&#9472;snapd.service @20.964s +17.281s
      &#9492;&#9472;basic.target @20.325s
        &#9492;&#9472;sockets.target @20.325s
          &#9492;&#9472;docker.socket @20.296s +29ms
            &#9492;&#9472;sysinit.target @20.184s
              &#9492;&#9472;haveged.service @20.184s
                &#9492;&#9472;apparmor.service @17.541s +2.630s
                  &#9492;&#9472;local-fs.target @17.537s
                    &#9492;&#9472;run-user-121.mount @37.352s
                      &#9492;&#9472;swap.target @17.387s
                        &#9492;&#9472;dev-disk-by\x2duuid-ed4ed90b\x2d7998\x2d4d92\x2dbd9e\x
                          &#9492;&#9472;dev-disk-by\x2duuid-ed4ed90b\x2d7998\x2d4d92\x2dbd9e
lines 1-18/18 (END)

systemd-analyze blame
         35.752s plymouth-quit-wait.service
         28.342s man-db.service
         25.736s apt-daily-upgrade.service
         17.281s snapd.service


```

---

### Post by oldfred on 2020-02-10
Do you even want snaps?
Willing to install the .debs for those apps that you do use that are snaps?

boot time cut in half by removing snap, they since have improved boot somewhat
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)

This removes all snaps at once:
sudo apt remove --purge snapd
sudo apt purge gnome-software-plugin-snap


Then use this to install the apps you really want.
Example:
sudo apt install "app"
sudo apt install gnome-system-monitor

Do not install from Ubuntu's software store, but use synaptic as that will be the .deb version.
sudo apt install synaptic

---

### Post by yaminb on 2020-02-10
Thanks for the input.
I'm pretty happy with SNAPs as far as applications go.
If I had to choose, I'd put up with the longer boot times. I'll work on making suspend work on my system :)

---

### Post by Dennis N on 2020-02-10
> Are there any options I could try, like delaying loading/mounting of SNAPS until they're required?
I see the 7200 rpm HDD as a weak point that you could upgrade. The snap applications aren't decompressed for use during startup; only when launched by you. Initializing the snapd services might be quicker with SSD? The snapd services initialization times I am seeing are in total less than 1 second:
```
dmn@Tyana:~$ systemd-analyze blame | grep snapd
           788ms snapd.service
            20ms snapd.seeded.service
             2ms snapd.socket

```
There's nothing extraordinary about the system I'm using here:
```
dmn@Tyana:~$ inxi
CPU: Quad Core Intel Core i3-8100 (-MCP-) speed/min/max: 800/800/3600 MHz 
Kernel: 5.0.0-38-generic x86_64 Up: 17m Mem: 1409.8/15908.9 MiB (8.9%) 
Storage: 1.82 TiB (9.7% used) Procs: 238 Shell: bash 5.0.3 inxi: 3.0.33 

```
I do not use any HDDs, though.

---

### Post by yaminb on 2020-02-10
yeah could be an sdd v hd thing. Just seems had to believe the ssd is like 20x quicker. But it could just be that. 
It's reasonable now, so we can see.

---

### Post by TheFu on 2020-02-10
+1 on removing the snapd subsystem.
+1 on using an SSD.

But really, how often do you really reboot?  Does 60 seconds longer really matter?
```
$ uptime
 13:29:19 up 30 days,  2:57,  3 users, 
```
I reboot when needed.  My laptop goes into standby unless it is physically moved, using a vehicle, usually just over the weekend.

---

### Post by yaminb on 2020-02-10
> **TheFu said:**
> 
I reboot when needed.  My laptop goes into standby unless it is physically moved, using a vehicle, usually just over the weekend.

I'd like to use suspend, but right now my computer doesn't come back from suspend. I'll try and get that working one day.

---


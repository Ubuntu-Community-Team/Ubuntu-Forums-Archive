---
title: "Is someone spying on me?"
date: 2020-07-27
forum: General Help
---

### Post by matrooswolf on 2020-07-27
Hi,

From time to time my screen flickers as if a screenshot is being taken. Just one time (at a time). I have no idea how this comes. It also happens when I'm doing nothing, so not touching any keys or so. It happens whatever program is open, I have the impression, LibreOffice, Firefox, ... 

Anybody any ideas? Any culprit who is spying on me?

(Running Ubuntu 20.04.1 LTS on a HP Probook 650 GS with Mesa Intel® UHD Graphics 620 (WHL GT2), also running latest kernel, 5.7.10)

---

### Post by ActionParsnip on 2020-07-27
Do you have the latest BIOS? Does the flicker happen on an external display too?

---

### Post by matrooswolf on 2020-07-27
BIOS: I don't know, it's a pretty new computer...
External display, I don't know, but I'll give that a try.
Thanks

---

### Post by dragonfly41 on 2020-07-27
I would explore, does flicker appear if
... running only on battery (no mains supply)
... disconnected from Internet

---

### Post by sdsurfer on 2020-07-27
I would not immediately suspect intrusion because it "looks like something else." I would probably look at graphics or some other system event. you can do
```
tail -f /var/log/syslog
```

in a terminal and leave the terminal open. the -f makes it interactive; as system events occur it gets logged here. press CTRL+C to exit tail.

Leave that open and the next time you get a blink, see if it tells you anything.

---

### Post by matrooswolf on 2020-07-30
Hi,
So I did ```
 tail -f /var/log/syslog
``` and finally got a blink (I missed some earlier ones)

This is what I get. But I do not understand it, or why something should cause a blink here.
```
Jul 30 09:48:02 HP-ProBook-650-G5 dbus-daemon[2597]: [session uid=1000 pid=2597] Activating via systemd: service name='org.freedesktop.Tracker1' unit='tracker-store.service' requested by ':1.1' (uid=1000 pid=2593 comm="/usr/libexec/tracker-miner-fs ")
Jul 30 09:48:02 HP-ProBook -650-G5 systemd[2582]: Starting Tracker metadata database store and lookup manager...
Jul 30 09:48:02 HP-ProBook-650-G5 dbus-daemon[2597]: [session uid=1000 pid=2597] Successfully activated service 'org.freedesktop.Tracker1'
Jul 30 09:48:02 HP-ProBook-650-G5 systemd[2582]: Started Tracker metadata database store and lookup manager.
Jul 30 09:48:02 HP-ProBook-650-G5 dbus-daemon[2597]: [session uid=1000 pid=2597] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.1' (uid=1000 pid=2593 comm="/usr/libexec/tracker-miner-fs ")
Jul 30 09:48:02 HP-ProBook-650-G5 systemd[2582]: Starting Tracker metadata extractor...
Jul 30 09:48:02 HP-ProBook-650-G5 tracker-extract[8855]: Set scheduler policy to SCHED_IDLE
Jul 30 09:48:02 HP-ProBook-650-G5 tracker-extract[8855]: Setting priority nice level to 19
Jul 30 09:48:03 HP-ProBook-650-G5 dbus-daemon[2597]: [session uid=1000 pid=2597] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
Jul 30 09:48:03 HP-ProBook-650-G5 systemd[2582]: Started Tracker metadata extractor.
Jul 30 09:48:03 HP-ProBook-650-G5 tracker-extract[8855]: can't init metadata tree /home/matroosje/.local/share/gvfs-metadata/root: open: Permission denied
Jul 30 09:48:14 HP-ProBook-650-G5 systemd[2582]: tracker-extract.service: Succeeded.
```

---

### Post by dragonfly41 on 2020-07-30
I don't know what "Miner" does but the suspicious log item is ```
org.freedesktop.Tracker1.Miner.Extract
```

Do a google search on that text pattern and there are many hits to explore further.

---

### Post by maglin2 on 2020-07-30
Isn't it the gnome file indexer?

---

### Post by HermanAB on 2020-07-30
Miner is indeed the Gnome file indexer.  I think the OP needs a double layer tinfoil hat.

---

### Post by Paddy Landau on 2020-07-30
> **HermanAB said:**
> I think the OP needs a double layer tinfoil hat.
Well, the OP does need an answer as to why the screen keeps doing that, and how to fix it. I wish that I knew the answer.

---

### Post by HermanAB on 2020-07-30
A bad screen backlight power supply is the the most likely cause.  The LCD backlight tube draws much power and it doesnt last forever.  It is not too hard to replace - done it a couple times many moons ago.  There are laptop spares vendors in Singapore and HK that have such things.

---

### Post by matrooswolf on 2020-07-31
Hi,
Thanks for the suggestion > I think the OP needs a double layer tinfoil hat. 

 I have to admit I only wear a one layer because of the heat. But I'll double up on the tinfoil and see if it gives any difference.

I missed another blink unfortunately, so I have no more information.

I didn't know the screen had a separate backlight power supply. But as it's a company laptop, (only a few months old), it's a little bit difficult to tinker with that.

Could it have something to do with Gnome Shell restarting automatically? It sometimes breaks down, and then I restart it manually. (It's only a suggestion). Maybe I'll try to make a screen recording of it. But the blinks only happen ever so often...

Meanwhile I'll double up on the tinfoil. Maybe wear a tinfoil mouth mask too? See if it helps...?

---

### Post by monkeybrain20122 on 2020-07-31
> **HermanAB said:**
> Miner is indeed the Gnome file indexer.  I think the OP needs a double layer tinfoil hat.

Tinfoil hat or not, tracker is a resource hog. Ubuntu is a lot snappier after removing it.

---

### Post by HermanAB on 2020-07-31
I think an easy way to check whether it is SW or HW, is to download an install ISO from a completely different distribution - say Fedora - run that from a memory stick and watch the screen while browsing the web or watching TV or something.

---

### Post by matrooswolf on 2020-08-11
Sorry, I have been absent for a while. But here are some of the logfile errors when there was a blink.
```
 Aug 11 14:13:53 user-HP-ProBook-650-G5 kernel: [15370.257988] i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun
Aug 11 14:14:04 user-HP-ProBook-650-G5 systemd[2411]: Started Application launched by gnome-shell.
Aug 11 14:14:04 user-HP-ProBook-650-G5 nemo[23995]: Current gtk theme is not known to have nemo support (Radiance) - checking...
Aug 11 14:14:05 user-HP-ProBook-650-G5 nemo[23995]: can't init metadata tree /home/user/.local/share/gvfs-metadata/root: open: Permission denied
Aug 11 14:14:18 user-HP-ProBook-650-G5 nemo[23995]: message repeated 170 times: [ can't init metadata tree /home/user/.local/share/gvfs-metadata/root: open: Permission denied]
Aug 11 14:14:25 user-HP-ProBook-650-G5 dbus-daemon[2429]: [session uid=1000 pid=2429] Activating service name='org.gnome.gedit' requested by ':1.158' (uid=1000 pid=23995 comm="nemo ")
Aug 11 14:14:25 user-HP-ProBook-650-G5 dbus-daemon[2429]: [session uid=1000 pid=2429] Successfully activated service 'org.gnome.gedit'
Aug 11 14:14:25 user-HP-ProBook-650-G5 gedit[24025]: can't init metadata tree /home/user/.local/share/gvfs-metadata/root: open: Permission denied
Aug 11 14:14:28 user-HP-ProBook-650-G5 nemo[23995]: can't init metadata tree /home/user/.local/share/gvfs-metadata/root: open: Permission denied
```
And
```
Aug 10 12:15:19 user-HP-ProBook-650-G5 kernel: [ 9025.153101] i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun
Aug 10 12:15:33 user-HP-ProBook-650-G5 nemo[31166]: can't init metadata tree /home/user/.local/share/gvfs-metadata/root: open: Permission denied
Aug 10 12:15:50 user-HP-ProBook-650-G5 nemo[31166]: message repeated 155 times: [ can't init metadata tree /home/user/.local/share/gvfs-metadata/root: open: Permission denied]
Aug 10 12:15:53 user-HP-ProBook-650-G5 dbus-daemon[4292]: [session uid=1000 pid=4292] Activating service name='org.gnome.gedit' requested by ':1.118' (uid=1000 pid=31166 comm="nemo ")
Aug 10 12:15:53 user-HP-ProBook-650-G5 dbus-daemon[4292]: [session uid=1000 pid=4292] Successfully activated service 'org.gnome.gedit'
Aug 10 12:15:53 user-HP-ProBook-650-G5 gedit[37447]: can't init metadata tree /home/user/.local/share/gvfs-metadata/root: open: Permission denied
```
It looks two times the same, so there must be something in there that causes the blink, I suppose...

---

### Post by Holger_Gehrke on 2020-08-11
I'd look into ownership and permissions of the files in '/home/user/.local/share/gvfs-metadata/'. Those files are created by the Gnome Virtual File System and unless you are running the file manager with sudo - not a good idea, at least use 'sudo -H' - the files in there should all be owned by 'user' and have permissions of either read and write by owner or read for everyone, write by owner. But this really shouldn't cause a blink.

On the other hand, the first message looks suspiciously like something that might cause a blink, because it's an error in the direct rendering manager (you are using intel 915 graphics ?). Searching online for 'Linux i915 FIFO underrun'  shows that it's a kernel / graphics driver problem that is actively being worked on. Seems to have come and gone and come back several times on various brands of laptops.

Holger

---

### Post by matrooswolf on 2020-08-11
Hi thank you for your reply.

I'm running Mesa Intel® UHD Graphics 620 (WHL GT2). Do they also cause a problem with linux?

---

### Post by Holger_Gehrke on 2020-08-11
While the kernel module is named i915, it actually handles all modern Intel onboard graphics, including the UHD 620.

In the [Arch Linux wiki]("https://wiki.archlinux.org/index.php/Intel_Graphics#Screen_flickering") there is a list of known problems and solutions for various problems with the i915 driver. One of the problems listed is screen flickering and they give a kernel parameter to switch off Panel Self Refresh (i915.enable_psr=0) as a solution. Whether or not this works for your problem I can't tell you, because a) I don't use Intel, so I can neither confirm your problem nor test this solution, and b) the descriptions in the bug-report I mentioned in my last post and this solution don't seem to have anything to do with each other ...

Holger

---


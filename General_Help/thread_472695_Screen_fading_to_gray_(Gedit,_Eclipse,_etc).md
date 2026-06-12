---
title: "Screen fading to gray (Gedit, Eclipse, etc)"
date: 2007-06-13
forum: General Help
---

### Post by leepr on 2007-06-13
Some of the applications I run fade to gray a few seconds after I open them. E.g. if I do `sudo gedit` and enter a valid password, the Gedit window appears, but the white screen fades to gray after a few seconds - I can no longer resize it, or type in it. If I type `sudo gedit` again, and am not prompted for my password, no window appears.

```
lee@lee:~$ sudo gedit
Password:
[COLOR="Gray"]# GEDIT OPENS UP, BUT FADES TO GRAY BECOMING UNUSABLE.[/COLOR]
lee@lee:~$ sudo gedit
[COLOR="Gray"]# GEDIT DOESN'T OPEN[/COLOR]
lee@lee:~$ ps -ef | grep -i gedit
lee      21207 14395  0 07:36 pts/0    00:00:00 grep -i gedit
[COLOR="Gray"]# NOTHING TO SEE HERE; MOVE ALONG[/COLOR]

```

This only happens for a few applications. Calling `sudo emacs` works perfectly well. Calling `gedit` (without the sudo) also works perfectly well. This problem occured in Eclipse also, but I think fixed that by just resizing the screen. Does anyone know what the problem might be, or where I might look to find relevant logs/errors?

Could this be related to my other issue posted in this forum ([http://ubuntuforums.org/showthread.php?t=472684Problem with theme gtkrc file - stopping DBVisualizer]("http://ubuntuforums.org/showthread.php?t=472684"))?

---

### Post by leepr on 2007-06-13
Actually, when I `tail -f /var/log/messages' and run `sudo gedit`, I see the following:

```
Jun 13 08:04:12 lee gconfd (root-32572): starting (version 2.18.0.1), pid 32572 user 'root'
Jun 13 08:04:12 lee gconfd (root-32572): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 13 08:04:12 lee gconfd (root-32572): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 13 08:04:12 lee gconfd (root-32572): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 13 08:04:12 lee gconfd (root-32572): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 13 08:04:12 lee gconfd (root-32572): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
[COLOR="Red"]# HERE IS WHERE THE SCREEN FADES TO GRAY[/COLOR]
Jun 13 08:04:42 lee gconfd (root-32572): GConf server is not in use, shutting down.
Jun 13 08:04:42 lee gconfd (root-32572): Exiting

```

---

### Post by chrisccoulson on 2007-06-13
Have you tried:
```
gksudo gedit
```

---

### Post by leepr on 2007-06-13
> **chrisccoulson said:**
> Have you tried:
```
gksudo gedit
```

Thanks, but that also fades to gray.

I can see the following in /var/log/messages:
```
Jun 13 08:31:25 lee gconfd (lee-5715): starting (version 2.18.0.1), pid 5715 user 'lee'
Jun 13 08:31:25 lee gconfd (lee-5715): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 13 08:31:25 lee gconfd (lee-5715): Resolved address "xml:readwrite:/home/lee/.gconf" to a writable configuration source at position 1
Jun 13 08:31:25 lee gconfd (lee-5715): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 13 08:31:25 lee gconfd (lee-5715): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 13 08:31:25 lee gconfd (lee-5715): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 13 08:31:29 lee gconfd (lee-5715): Resolved address "xml:readwrite:/home/lee/.gconf" to a writable configuration source at position 0
Jun 13 08:31:43 lee gconfd (root-5838): starting (version 2.18.0.1), pid 5838 user 'root'
Jun 13 08:31:43 lee gconfd (root-5838): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 13 08:31:43 lee gconfd (root-5838): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 13 08:31:43 lee gconfd (root-5838): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 13 08:31:43 lee gconfd (root-5838): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 13 08:31:43 lee gconfd (root-5838): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 13 08:32:43 lee gconfd (root-5838): GConf server is not in use, shutting down.
Jun 13 08:32:43 lee gconfd (root-5838): Exiting
```

I believe I know what the root of the problem is:

```
lee@lee:~$ gconf-sanity-check-1 
Please contact your system administrator to resolve the following problem:
Failed to get a file lock: Failed to lock '/tmp/gconfd-lee/lock/ior': probably another process has the lock, or your operating system has NFS file locking misconfigured, or a hard NFS client crash caused a stale lock (Resource temporarily unavailable)
```

I tried deleting the lock file and restarting the session/machine, but it still gives me the error.

Does anyone have any idea how to get rid of the lock? I'm not using NFS mounts....

---

### Post by palmtrees44 on 2007-11-18
my "fade to grey" experience was when attempting streaming video using firefox from BBC.  Not sure if related but Realplayer 10 I installed and ubuntu is stuck on associating video with the "mplayer plugin" in firefox instead of Realplayer 10.  Anyone know how to change file associations?  Once screen went grey I could not click anything.  My first assumption was a system problem and am changing the video memory available right now...... Anyone else have this problem?  And what programs were you running at the time?

---

### Post by wpshooter on 2007-12-29
> **palmtrees44 said:**
> my "fade to grey" experience was when attempting streaming video using firefox from BBC.  Not sure if related but Realplayer 10 I installed and ubuntu is stuck on associating video with the "mplayer plugin" in firefox instead of Realplayer 10.  Anyone know how to change file associations?  Once screen went grey I could not click anything.  My first assumption was a system problem and am changing the video memory available right now...... Anyone else have this problem?  And what programs were you running at the time?

I have this problem occasionally on all of my machines, most frequently it seems when I am browsing in Firefox.  I do have the RealPlayer10 program installed and I note that I don't ever remember seeing this problem until the last couple versions of Ubuntu, I think it started in Feisty.

Anyone have any clues as to what is causing this screen fading to gray (no color) and then some times the program locking up.   Like occasionally when this happens Firefox refuses to respond and I have to end the Firefox session and open a new one.

P.S. - The screen does not ALWAYS lockup but most of the time goes back to the normal display of colors and proceeds as normal.

Thanks.

---

### Post by Sidewinder1 on 2007-12-29
t's a feature of Compiz (the "Desktop Effects"). If a program gets frozen, Compiz will desaturate the window to notify you about it.

So the "greying out" is just a signal to tell you that the app is frozen, not part of the problem itself.

Although Compiz does this a bit too easily, sometimes if a program needs a long time to do something Compiz believes that it's frozen and desaturates it's window. This shouldn't be a problem, as soon as the program becomes responsive again Compiz will return the colors.

Usually you can close a frozen program easily by just clicking the x-button in the titlebar, or right-clicking it in the window list and selecting "Close". You'll get a popup telling you that the program mis frozen and asking if you want to force it to close. If that doesn't work, press Alt-F2 and run 'xkill'. This will change your cursor into skull&bones and now you can just click any window to force the program to close.
HTH

---


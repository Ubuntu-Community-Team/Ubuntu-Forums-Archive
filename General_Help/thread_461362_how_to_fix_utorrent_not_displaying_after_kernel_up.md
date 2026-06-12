---
title: "how to fix utorrent not displaying after kernel update"
date: 2007-06-01
forum: General Help
---

### Post by voxel on 2007-06-01
I haven't really looked around much to see if other people are having this problem, but I figured I'd share my (somewhat inelegant) solution to the problem...
If after a kernel update your utorrent window won't display, but the tray icon shows up (and shows activity), then follow these steps to resolve the problem:

1. Close utorrent (if open)
2. navigate to ```
/home/<username>/.wine/drive_c/windows/profiles/<username>/Application Data
```
3. you should see a uTorrent folder, remove the entire folder
4. re-run utorrent

You will have to set up your ports, scheduler, etc... but kernel updates don't come all that often, but no big deal in my opinion...
Hopefully this works for people experiencing this problem, or if you have another solution that worked for you, fill us in!

---

### Post by Kuoi on 2007-06-02
Thanks for this tip , I needed it !

=D> Kuoi

---

### Post by koshari on 2007-06-07
its a good idea to keep your recent and any torrent specific files in the applications directory especially if you have some torrents that have not finished.

it seems the settings.dat is the offending file (or the other file that utorrent writes on shutdown) that stop the window rendering.

---

### Post by voxel on 2007-06-07
thanks for the tip koshari
I always set up utorrent to store torrents in a particular folder (as well as completed torrents) so that resuming torrents even after having to 're-install' utorrent is trivial :)

---


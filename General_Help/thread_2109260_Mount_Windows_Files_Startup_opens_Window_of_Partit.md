---
title: "Mount Windows Files Startup opens Window of Partition"
date: 2013-01-27
forum: General Help
---

### Post by cooknathan on 2013-01-27
Hi, Im a noob coming over from windows so sorry if this is easy &/or has been answered and I could find it.

I am running a dual boot Windows 7 and Ubuntu 12.10 on my Asus eeepc 1001px. When I boot ubuntu, it mounts the files from the windows partition (which is handy) and then opens a window of those folders (which is annoying).

When I turn off the "Mount Windows Files" in the Startup Applications Preferences, the window with the partition doesnt come up but rhythmbox and launcher cant find my files on the windows partition (obviously ;)).

I was wondering If there is a way to have Ubuntu mount my windows files automatically on startup without it opening my other partition such that I dont have to close the window every time I boot just to get to my desktop.

Thanks in advance!

---

### Post by Zvlwab on 2013-01-27
I do not know this "Mount Windows Files" option, but the automount options are stored in /etc/fstab. I think it would be better to turn this off.
Could you post the output of the following command?
```
cat /etc/fstab
```
And the output of
```
df
```

---

### Post by Hedgehog1 on 2013-01-27
cooknathan,

I too have had this start happening in the last few updates to 12.04.

The UI (called Nautilus) opens a window for my 2nd internal NTFS drive, and also opens a window for each of my three NFS (Network File System) drives that from my NAS (Network Accessible Storage) device.

So this means it is happening to me for both Windows and Linux drive types.

I do not have a solution for this yet - but I wanted you to know others are seeing the issue, too.

---

### Post by mikewhatever on 2013-01-27
Nautilus is set to automount media and open it by default. There is a checkbox for that, hidden in dconf-editor. 
To make things simple, you can turn it off with 

```
gsettings set org.gnome.desktop.media-handling automount-open false
```

...and turn it back on with
```
gsettings set org.gnome.desktop.media-handling automount-open true
```

---

### Post by cooknathan on 2013-01-27
Thanks a million mikewhatever,

It worked perfectly. 

@Zvlwab let me know if you want me to send you that anyway ;)

Thanks again guys, I appreciate your time and help :)

---

### Post by Zvlwab on 2013-01-30
> **cooknathan said:**
> Thanks a million mikewhatever,

It worked perfectly. 

@Zvlwab let me know if you want me to send you that anyway ;)

Thanks again guys, I appreciate your time and help :)

If it works now, never mind :)

---


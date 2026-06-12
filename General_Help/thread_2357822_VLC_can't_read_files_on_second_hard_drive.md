---
title: "VLC can't read files on second hard drive"
date: 2017-04-06
forum: General Help
---

### Post by DaveBF on 2017-04-06
I'm on Ubuntu 16.04 with VLC 3.0.0-git Vetinari.  VLC can read mp3s from my home filesystem, but when I try to play mp3s from my laptop's secondary internal hard drive (that I use for media), it says that permission is denied.  Other audio filetypes and videos from the same directories work in VLC.  The error that comes when the mp3s don't play is:

```
 [COLOR=#ff0000]File reading failed:[/COLOR]

 [COLOR=#000000]VLC could not open the file "/media/...d.mp3" (Permission denied).[/COLOR]

 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'file:///media/...d.mp3'. Check the log for details.[/COLOR]
```

And I couldn't find written logs, but terminal outputs this error:

```
[00007f1fb4001188] filesystem stream error: cannot open file /media/...d.mp3 (Permission denied)
XmbTextListToTextProperty result code -2 {this prints nine times}
[00007f1fb4001878] filesystem stream error: cannot open file /media/...d.mp3 (Permission denied)
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
```

And so I checked permissions on the drive and on the files.  Again, the permissions are the same across m4as and video files, but vlc only seems to think it doesn't have permission on the mp3s, even though I've set all permissions on the mp3s in that filesystem to read and write for all.

So yeah, there's a particular hard drive in my laptop that VLC gets permission denied errors only when trying to play mp3s.  Any help would be great; I'm a musician and it sucks not being able to listen to music :P



EDIT: I installed a back version of VLC in the ubuntu repositories (2.2.2 Weatherwax) that can play the mp3s from the drive.  It's not a snap, like 3.0.0 is.  A solution that's good enough for me, but it's still an annoying error floating around out there.

---

### Post by veddox on 2017-04-06
Hi Dave,

what you are reporting sounds like a VLC bug to me... As far as I can see, VLC 3.0.0 is still a development version (their website says that 2.2.5 is the current one). I therefore suggest you submit a bug report to them ([https://trac.videolan.org/vlc](https://trac.videolan.org/vlc)).

Also, you could try out other media players, either the repository VLC version or Rhythmbox, MOC or whatever else catches your fancy :-)

Good luck!

---

### Post by mc4man on 2017-04-06
If you want the snap vlc (or any snap) to not be confined to $HOME then you have to install with the --classic option (formerly --devmode
i.e.
```
sudo snap install vlc --classic
```

(- if snap version is already installed then it, (snap),  must be removed before re-installing as above.

---


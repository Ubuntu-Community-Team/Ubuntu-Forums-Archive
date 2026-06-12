---
title: "Any media player which automatically plays next file in folder?"
date: 2012-10-17
forum: General Help
---

### Post by f3flight on 2012-10-17
In Windows it is a usual function - almost any player will play next file in folder if you press Next. In Ubuntu I can't seem to find any player that does that - all players have playlists which will only contain a single file after I click on it in explorer(Nautilus).

WTF? This is really basic, did not expect it to be like that in Ubuntu. Or is there a setting or a special player which does that? I know I can open a folder instead of a file, but I want to click on a file, to start with it and continue on in alphabetical order. Any chances?

Ubuntu is freshly installed 12.04 TLS

---

### Post by PowerBarry43 on 2012-10-17
Hi

If i remember correctly vlc has this feature and can be installed by running

```
sudo apt-get install vlc
```

if I'm wrong and vlc doesn't have this feature you can press ctrl+shift+o then click add and you can select any files you wish to play and in what order you wish to play them.

Hope this helps!

Barry

---

### Post by mhaggard on 2012-10-17
You can also make an entire library in Rhythm Box. It's not a bad program. I use that as kind of an iTunes replacement. So, it has pretty much the same functionality.

---

### Post by evilsoup on 2012-10-17
I just checked, and VLC doesn't do that. Neither does gnome-mplayer or totem.

---

### Post by f3flight on 2012-10-17
> **mhaggard said:**
> You can also make an entire library in Rhythm Box. It's not a bad program. I use that as kind of an iTunes replacement. So, it has pretty much the same functionality.
Actually I wrote this post with video files in mind. Rythmbox doesn't seem to be able to play videos.

---

### Post by rizzeh on 2012-10-17
mplayer can do it
```
sudo apt-get update
sudo apt-get install mplayer
cd /Music/Artist/Album
mplayer * 
```

will apply to video files too

---

### Post by evilsoup on 2012-10-17
> **f3flight said:**
> Actually I wrote this post with video files in mind. Rythmbox doesn't seem to be able to play videos.


It's not *exactly* what you want, but if you select all the files in a directory (ctrl+a, or you can do it with the mouse) and either press enter or right-click on one of the files --> select 'open with movie player', then it will put them all into a nice playlist.

> mplayer can do it

That's not what the OP asked for, though, and if they're willing to use the command-line then every media player I know of works that way.

---

### Post by LewisTM on 2012-10-17
Being a visual file manager, **GThumb** will do that. It now supports Videos.

Associate gthumb with videos and you can click next/previous in the Viewer to change files. It will respect the file order and filters you have set in its file Browser.

I recommend you get the latest version from the PPA.
[https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)
```
sudo apt-add-repository ppa:webupd8team/gthumb -y && sudo apt-get update && sudo apt-get install gthumb -y
```

Cheers!

---

### Post by houseworkshy on 2012-10-17
If you open the whole folder with totem then it will play all the files in sequence.  Right click on the folder, choose open with "other application" then choose movie player from the list.

---

### Post by oldos2er on 2012-10-17
> **evilsoup said:**
> I just checked, and VLC doesn't do that. 

Vlc will play all files in a folder if you open one with Ctrl-F.

---


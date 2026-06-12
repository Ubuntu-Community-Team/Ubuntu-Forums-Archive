---
title: "no DVD playback"
date: 2024-08-30
forum: General Help
---

### Post by chopra on 2024-08-30
Hi Guys,
I have a strange problem.
I have Ubuntu 20.04
a toshiba tecra intel core i7

and I am unable to play DVD's for some reason, except for one.

Neither VLC, nor Videos will play DVD's.  
I just get a blank black screen when using Videos for anything.

With VLC, I get the message:

[COLOR=#000000][COLOR=#FF0000]Playback failure:[/COLOR][/COLOR]
[COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
[COLOR=#000000][COLOR=#FF0000]Your input can't be opened:[/COLOR][/COLOR]
[COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
[/COLOR][COLOR=#000000]

[/COLOR]
[COLOR=#000000]whenever I am using my external DVD drive.
If I'm trying to use the laptop's internal DVD drive, VLC behaves the same way as Video, and just does nothing.

The one exception is that VLC is able to play a single DVD, from the Vault Universal Studios, which has the message on it:
"This disc is expected to play back in DVD video Play Only devices, and may not play in other DVD devices, including recorders, and PC drives"

VLC will only play that DVD if it's in the computer's drive.

So basically, for regular DVD's, nothing works, and for the specially protected one VLC works, but only if it's in the computer.

For some reason, VLC doesn't like my external drive.

Any insights would be appreciated.

Thanks, Chopra

[/COLOR]

---

### Post by nicolasdentremont on 2024-08-31
Video DVD playback normally won't work unless you install the proper library package.

I had to install libdvd-pkg

Then initialize it by running:

```

dpkg-reconfigure libdvd-pkg

```

I think the video DVD related stuff isn't free/open source which is why it's not shipped right with Ubuntu.

---

### Post by chopra on 2024-09-01
Thanks, that did the trick!
vlc works now.
If I use an external drive, I have to select a different block device manually.

---


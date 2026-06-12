---
title: "Is there a VNC that can do Sound ?"
date: 2023-04-22
forum: General Help
---

### Post by jonfisher on 2023-04-22
I am remote operating a Windows 10 machine from my Ubuntu 22.04.2 LTS
machine, using TightVNC, and find that I need/want to receive SOUND from
the remote system.  Is there a version of VNC that can do this, or another
program that runs on both platforms to share sound?   I'll probably need to
do the reverse at some point, too -- control the Linux machine from the
Windows 10 machine, including sending Linux sound back to Windows, so a
solution that supports both directions would be preferred.  Thanks in
advance.

---

### Post by TheFu on 2023-04-22
Any media playback is best handled using a remote file system mount.  However, I believe MSFT's RDP can do it between MSFT machines.  Don't know about the Linux versions of RDP, since MSFT tends to hold back just enough information to prevent complete integration.  

You might try the Gnome RDP integration. [https://ubuntuhandbook.org/index.php/2022/04/ubuntu-22-04-remote-desktop-control/](https://ubuntuhandbook.org/index.php/2022/04/ubuntu-22-04-remote-desktop-control/) though the comments say audio isn't working. Also came across an AskUbuntu thread, 
> The standard RDP service in Ubuntu 22.04 is gnome-remote-desktop (g-r-d).
Audio output forwarding in g-r-d was implemented in GNOME 43 (0 + some improvements in 1) (also requires PipeWire for audio handling), however Ubuntu 22.04 uses GNOME 42 (and Pulseaudio).

With Linux as the remote system, there are a few options that work, but that isn't the situation.
I barely use MS-Windows and don't know much about sound with it, but a normal answer would be to setup an audio streaming service that uses a published standard protocol and stream the media using that.  

For example, I have an mpd server and there are clients that support controlling it from anywhere.  For local playback, I tend to stream using either DLNA or a direct NFS mount.

Sadly, these are not general solutions. They are specific to the media.

---

### Post by jonfisher on 2023-04-24
I'm  sorry, I was insufficiently clear. I'm not looking to play static media  that merely reside on a remote computer, but rather to receive audio  being generated on-the-fly by, in this case a videogame emulator.

---

### Post by ActionParsnip on 2023-04-25
[https://superuser.com/questions/720772/how-to-remote-linux-desktop-with-audio-support](https://superuser.com/questions/720772/how-to-remote-linux-desktop-with-audio-support)

Possibly Remmina. Gaming will be awful over a remote connection

---

### Post by TheFu on 2023-04-25
> **jonfisher said:**
> I'm  sorry, I was insufficiently clear. I'm not looking to play static media  that merely reside on a remote computer, but rather to receive audio  being generated on-the-fly by, in this case a videogame emulator.

Best to run the game locally on the machine you sit behind, unless it is Solitaire or some other card game.  Then I suggest using x2go.

---


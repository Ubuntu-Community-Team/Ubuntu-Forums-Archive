---
title: "Need helping streaming videos from PC to laptop"
date: 2007-04-10
forum: General Help
---

### Post by Jump on 2007-04-10
On Windows I would use my PC as a server of sorts to store all my DVDs in xvid format. This allows me to fire up the laptop in another room and watch any movie from my collection. Now that I've switched both computers to Edgy, I need to find a way to stream the content like I did with Windows.

This is what I've tried so far

* right click folder and choose to "share" (it prompts me to install Samba, which then automatically allowed the other PC to view the folder a smb share.) - however, this would not stream. I asked around on IRC and they told me this was something that didn't work with smb shares right now.
* right click folder to share and chose NFS instead of Samba. This appears to share the folder but the other PC isn't able to view the shared folder with NFS. I'm not sure why this didn't work like other method. It doesn't map the network and find the shared folders like Samba did.
* using openssh and x forwarding to play a movie. (this *sort of* works but the audio for the video plays on the desktop instead of the laptop and the playpack is really slow)
* using VLC to setup a network stream (the laptop can connect to the stream using HTTP just fine, and it works beautify - the problem is that I don't have any control from the laptop. I'm forced to run back into the other room if I want to start up another movie)

None of these options have worked for me. What I'm looking for is a way to open the remote folder, see the pretty icons that show me which movie is which, and then just double click to open/play without problems.This is what I was used to doing with windows and I'd like to do this using Ubuntu as well.

How can I accomplish this?

---

### Post by Jump on 2007-04-10
bump

---


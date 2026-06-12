---
title: "Need help converting home server to Linux."
date: 2007-03-08
forum: General Help
---

### Post by Dimtar on 2007-03-08
Hi Guys. I wish to move my home server over to Linux permanently. I am a big fan of Ubuntu as i have it on my laptop. Currently my home server does the following running Windows XP Pro ( so i will require a Linux equivalent if possible )

- Most basic would be file sharing. Movies, downloads, pictures, music and program updates and installation are all fed direct from the server. So i need the windows boxes to be able to see the Linux Share.
- The Linux box would require Limewire and a torrent client such as UTorrent. I don't think this is going to a problem.
- The more difficult parts will be firstly remote access. It IS a home server and i do not connect anything but power and a lan cable to it.
- Also i currently use TVersity media server as a way of sharing files to media centres such as my Xbox 360. So i would require a similar program.

Any help would be much appreciated if possible. The specs of my server are:

AMD Athlon 64 3500
1 gig ddr 400 ram
200gb hdd, split with 40 for os and 160gb for files. (the 160gb partition is what the network share will consist of)
6600gt 128 mb gfx
dual gigabit ethernet

---

### Post by Azakus on 2007-03-08
Ok, here's what I did for my server. I'll try to match this in order with your requests.
1. Samba is a program that provides Windows network integration. There's a few guides around that can help configure it, but once you do, you can see it on your network.

2.Limewire has a linux client, so that's taken care of. Bittorrent clients are a dime a dozen for Linux.

3.SSH is as secure as remote access can get, so install it and you can run command line to the box like this ```
ssh -X -l usernameonserver ###.###.###.###
``` Where -X makes the GUI be sent to your computer, and -l logs you in with a different username (because ssh tries to log you in with your username on the computer with the screen). ###.###.###.### is of course your server's IP address.
You'll also need to use a program called screen that makes remote copies of the command terminal, otherwise all your open programs will die as soon as you stop connecting to the server via SSH.

4.Don't know of a media server right now, but look around for similar posts.

---


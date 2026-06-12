---
title: "Rsync on apllication open and close"
date: 2013-01-12
forum: General Help
---

### Post by biozenunity on 2013-01-12
I use a couple programs that i would like to have the data synced to both of my Linux boxes one of which is a laptop so the sync must work over the Internet. I am currently using Luckybackup and dropbox to accomplish this. I would prefer the sync to be either in real time or to write a script to rsync upon application open and close. Unfortunately I am a complete noob when it comes to scripts. Any help with how to write this script or alternatives would be greatly appreciated.

---

### Post by papibe on 2013-01-16
Hi biozenunity.

There are several steps to accomplish that.

If you're unfamiliar with that concepts mention below, take a look at this is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

This would be the main steps:
[LIST]
[*]Set your server with a LAN static IP.
[*]Install openssh-server on your server.
[*]Test LAN ssh access to your server.
[*]Optional: change the standar ssh port (22) to a different, preferable higher value.
[*]Subscribe to a Dynamic DNS service. There are free and pay options. For example: DynDNS, no-ip, zoneedit, etc (check [here]("http://dnslookup.me/dynamic-dns/") for a longer list).
[*]Either install and setup the package ddclient, or (better if available) set your DDNS client in your router.
[*]Forward the ssh port in your router to your server.
[/LIST]
Now you are ready to test accessing your server over the internet.

Important: do not try to access your server using its public IP, or dynamic name from inside your own LAN. The proper way to test access is from outside your network. For example, an internet café, public library, a friend house, or using your phone or tablet's 3G service (be sure to NOT being connected to your LAN's WiFi though).

I hope that points you in the right direction, and tell us how it goes.
Regards.

---

### Post by ronnoc on 2013-01-20
Anternatively, you could just install Ubuntu One on both boxes. You get 20GB for free. Synchronization between PCs using the cloud via U1 is in real time.

---


---
title: "Setting qBittorrent as default magnet app in Firefox"
date: 2015-03-04
forum: General Help
---

### Post by TheBrexas on 2015-03-04
Hello everyone, 

So I want my Firefox to use qBittorrent as default app instead of Transmission, the only one he lets me chose, and when I click in "other" and I try to find where qBittorent is installed I don't succeed to find it, i tried in /usr/bin and /usr/share/applications but there is no way I can't find it. Any clue how can I do this? Thanks everyone in advance I'm a newbie Ubuntu user!

---

### Post by phedup on 2015-03-08
If you have Transmission torrent on your launcher, you can right click it and pick 'unlock from launcher.'  Then google 'torrents' and download 'qBittorrent for Linux'.  Now go to the dash and type qBittorrent; the icon will appear.  (The dash will find where apps are installed; it's the top icon on the launcher bar on the left of your screen.)
Now you can drag the qBittorrent it to your launcher bar.  Voila.

---

### Post by speartip on 2015-03-09
You are going about it the right way. The program is installed in /usr/bin/qbittorent.
Alternatively you could uninstall transmission, & Firefox should default to qbittorent.

---

### Post by coldraven on 2015-03-09
I just right click a magnet and select "Copy link location". Then start qbitorrent and choose "File>Open link", and the link will automatically be pasted into the window.

---


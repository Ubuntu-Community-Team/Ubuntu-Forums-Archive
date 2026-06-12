---
title: "rutorrent automove fails at 4gb"
date: 2012-10-27
forum: General Help
---

### Post by Apathia on 2012-10-27
I've got automove on rutorrent set to move from one drive to another, it works perfectly until it gets to a file that's greater than 4gb, and then it fails. Simply fails at exactly 4gb.

I'm using ruTorrent 3.4, rTorrent 0.9.2-1r, Lighttp 1.4.28-2ubuntu4 on Ubuntu 12.04.1. Both drives are ext4

here's the automove log:
[26.10.12 22:48:40] AutoMove: --- begin ---
[26.10.12 22:48:40] AutoMove: Operation Move
[26.10.12 22:48:40] AutoMove: from /media/Downloads/Doctor.Who.2005.S05.720p.BluRay.DTS5.1.x264-CtrlHD/
[26.10.12 22:48:40] AutoMove: to   /media/Seeds/Doctor.Who.2005.S05.720p.BluRay.DTS5.1.x264-CtrlHD/
[26.10.12 22:49:46] rtMoveFile: from /media/Downloads/Doctor.Who.2005.S05.720p.BluRay.DTS5.1.x264-CtrlHD/Doctor Who 2005 S05E12 720p BluRay DTS5.1 x264-CtrlHD.mkv
[26.10.12 22:49:46] rtMoveFile: to   /media/Seeds/Doctor.Who.2005.S05.720p.BluRay.DTS5.1.x264-CtrlHD/Doctor Who 2005 S05E12 720p BluRay DTS5.1 x264-CtrlHD.mkv
[26.10.12 22:49:46] rtMoveFile: move fail, try to copy
[26.10.12 22:50:51] rtMoveFile: copy fail
[26.10.12 22:50:51] AutoMove: --- end ---

---


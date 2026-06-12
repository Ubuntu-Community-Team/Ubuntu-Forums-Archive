---
title: "Ubuntu Server, Simply Need To Auto Mount a Hardware Raid 1 Drive"
date: 2017-06-11
forum: General Help
---

### Post by h43442 on 2017-06-11
Ubuntu Server Command Line, not GUI

Okay so here is the situation. Last night I setup a hardware raid 1 on my poweredge R410. It synchronized for 8 hours and was good to go.

All I want to do is get this drive auto mounted every time at boot so a PLEX server can access my media library. When I attempted sudo mount /dev/sdb I got "wrong fs type, bad option, bad superblock". So at this point I thought it was a filesystem issue so I used the command mkfs.btrfs /dev/sdb

Im pretty sure I destroyed my raid because at first my drives looked like this (Notice sdb at the bottom and its sub partitions) BUT it no longer has the sdb1 and sdb2 subs.
[https://i.stack.imgur.com/MltP0.jpg](https://i.stack.imgur.com/MltP0.jpg)

So now I am in the process of resyncing for 8 hours. When itss done what do I need to do to just auto mount this drive and throw files on it?

Disclaimer - I am a total noob with command line and have been googling this for awhile now. I really want to keep using Ubuntu Server instead of switching to Windows but considering I already have the server and samba setup this was not the problem I expected to be having.

---


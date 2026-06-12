---
title: "Need Help!  Home Audio/Video Multimedia setup"
date: 2007-12-27
forum: General Help
---

### Post by Warchilde on 2007-12-27
Here's the situation I'm in... I just finished wiring my home for gigabyte ethernet, I have a central wiring closet which not only has the ethernet coming into a 24-port gigabyte switch which uplinks to a homebuilt router with WAN/WAP/LAN interfaces but also the cable (which also provides the internet access as well as video) going into a distributor/amplifier which feeds out to the rest of the house.  The Wiring Closet also functions as my "server room" and contains the following servers;

1.  Game Server for the LAN
2.  File Server for the LAN running ubuntu 7.10 server
3.  Multimedia Server 01 running ubuntu 7.10 server*
4.  Multimedia Server 02 running ubuntu 7.10 server*
5.  Home Automation Server
and so on...

These are homebuilt machines in a rackmount configuration so I can be a little flexible.  All the hardware works fine with the OS and they are all functioning fine except for the ones marked.

The primary issues I'm running into is with Multimedia Servers 01 & 02.  They are dual core 3800+ processors with 2gb of ram running 7200rpm harddrives in RAID5 (01 = 40gb Boot + 3x500gb HDs, 02 = 40gb Boot + 12x500gb HDs).  Multimedia Server 01 is the audio server which is *supposed* to provide streaming audio on demand to five Slimdevices media players and three HTPCs located throughout the house (as well as four personal PCs and notebooks).  The media players and HTPCs are all hardwired into the network.  Multimedia Server 02 is the video server which is supposed to be providing streaming video to each of the HTPCs and PCs on demand.  

The wireless is solely for visitors, the notebooks, and the Pepperpads I use for remote controlling a lot of the home automation and general lightweight entertainment.

Just wanted to get that out of the way.

What I need is a UPnP or Media Server software that allows each of those devices to *independently* access content.  Right now I can use one of the media players, HTPCs, etc... to connect and start a music playlist or video but then all the other ones are limited to what is already running.

For example;  Ideally I would like any of the media players to be able to connect to the server, browse a selection of music playlists, select one, and then start playing it without every media player in the house then being stuck listening to that one playlist.  I'd like the HTPCs and the personal PCs to be able to access a web GUI on that same server that would allow them to build playlists which could be saved to be played on the media players or immediately played on the HTPC or PC in question.  The same applies to the video server.   I'd like each of the HTPCs or PCs to be able to access a video, start it playing, and have this happen all independently of each other.

I have a mix of Linux (Ubuntu) and Windows PCs all trying to access these servers.  When things didn't work with the "default" configuration and instructions I tried to set up the music server with a variety of users (MP01-MP05 for the Media Players, HTPC01-HTPC03 for the HTPCs, etc...) to see if that would do the trick and either messed up the configuration or the server software I was trying just wouldn't handle what I was trying to do.  I have a feeling it's the former because I don't understand having server software that wouldn't allow multiple independent connections.  I've tried to use Slimdevice's Slimserver software, Geexbox's UPnP server, and a couple of others....

Anyone have any suggestions?  I'd prefer not to have to have 4-5 *different* streaming/UPnP server daemons running on each machine if I can help it.  The potential for conflicts with different servers trying to function together is obvious.

---


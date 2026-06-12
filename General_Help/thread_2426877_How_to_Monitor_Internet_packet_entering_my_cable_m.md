---
title: "How to Monitor Internet packet entering my cable modem"
date: 2019-09-14
forum: General Help
---

### Post by Ralph L on 2019-09-14
I have 2 Voice Over Internet Protocol (VOIP) phones.  One is an Obihai; the other is Ooma.  Both have voice breakup at the remote end, when my Internet is busy.  I run breakup tests using my home VOIP phone to call my cell phone, and while I am talking I run an Internet speed test.  These tests first download as much data as possible into my computer, then upload as much data as possible to the speed test Internet site.  During the download portion of the test my voice comes through quite well.  However, during the upload portion of the test my voice breaks up.  In other words, when there is a busy upload channel, voice packets don't get through on time, and the remote phone voice breaks up.
I want to build a system to test to see if the "voice priority" field is set appropriately on voice packets being uploaded.  My thought is to buy an Internet switch, and plug it in between my phone and my cable modem.  Then I will route one output port to the cable modem, and one output port to the ethernet port on my computer.  This should route all packets to my computer.  On the computer I need software to capture all the packets coming in the ethernet port and examine the voice priority field to see if it is set.

My questions are:
1. Is there a better approach to take?
2.  What Xubuntu software is available to receive and examine the packets?  I looked a little at Wireshark, but it seems very complex and I don't know if the linux version really works.

Any help is appreciated.....

---

### Post by TheFu on 2019-09-14
Many routers support something called QoS - Quality of Service.  Put VoIP traffic at a higher priority than all other types of packets.    ddwrt does.  openwrt does.  pfSense does.  They all work.  I've used it on each of those and on other router software/hardware.

Wireshark works. QoS is the better answer.

VoIP needs 128Kbps per channel used with ulaw (G.711u) as the voice codec.  If the VoIP provider supports G.729, the quality is good and the required upload bandwidth drops drastically. But G.729 does *slightly* cut off the beginning and ending of sentences. Depending on your voice, it might not matter at all.

QoS is the answer.

---

### Post by Ralph L on 2019-09-15
The Fu:  Thanks for responding.  Sounds like you have experience with VOIP.  Also, thank you for the info on dd-wrt.  I want to replace my router in the future and dd-wrt might be very useful.
However, my current problem is somewhat different.  My VOIP phone is placed between my router and my cable modem.  Both VOIP phone manufacturers recommend this configuration.  It allows the phone to prioritize voice packets ahead of all other packets that the router is sending (uploading).  In theory all the phone needs to do is buffer up a few packets from the router, while it uploads the voice packets.  However, a heavy upload still causes the voice packets to be delayed, and voice at the remote end breaks up.  The test rig that I am looking to build is to determine if voice priority is being set in the voice packets so the rest of the Internet gives the voice packets first priority.  My Internet provider (Mediacom) may ignore priority, but I need to determine if packets are even being sent with voice priority.  I have spoken with Mediacom and phone vendor tech support and they don't even know about packets--much less the packet priority field.

Again, thanks for your response and any other ideas you may have on the subject....

---

### Post by TheFu on 2019-09-15
All VoIP equipment makes claim that putting the ATA between the modem and router is required.  This isn't true. Most cheap ATAs can't handle all the packets that a GigE network will throw at it, especially if protocols using hundreds of connections are used. Put the ATA on the router, like any other internal LAN device, setup QoS on the router, and see how much better it works.  

You have nothing to lose.

BTW, if there is any wifi between the ATA, router, modem, don't do that.  Latency is the enemy of great sounding phone calls.

---


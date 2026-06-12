---
title: "Audacity recording fine but won't play back while doing so"
date: 2005-08-08
forum: General Help
---

### Post by thoms on 2005-08-08
When I use audacity, I can record from the line in but despite setting the correct options, playback of other tracks and the current one stutters in and out (most of the time I get nothing). Any ideas?

---

### Post by Jamie Jackson on 2007-11-23
I'm resurrecting this old thread because I'm having the same or a similar issue.

I'm using Audacity 1.3.3-beta (packaged/repo version on Gutsy). I've got a Dell Latitude D620 with a Core Duo and my sound seems to be as listed below (assuming I ran the right command.

I lay down a track, and it records fine and plays back with no problems. However, when I go to record another track on top of it, while listening to the first track, the playback track stutters so much that I can't play along.

Also, please see the screenshots of my config screens.

jamie@mercury:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---


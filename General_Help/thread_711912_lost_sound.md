---
title: "lost sound"
date: 2008-03-01
forum: General Help
---

### Post by benner on 2008-03-01
I no longer have sound.  The other threads that I read don't seem to offer solutions.  I go to preferences > sound and anything I test gives me:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource not found.

One post a guy entered the following and here's what happened...

ben@RAMEN-UBUNTU:~$ sudo lshw -C sound
[sudo] password for ben:
  *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP55 High Definition Audio
       vendor: nVidia Corporation
       physical id: 6.1
       bus info: pci@0000:00:06.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

I had a random freezing problem and tried a fix that hadme install the server kernel.  That was 2 days ago.  No freezes since, so I'm happy about that.  I couldn't update openmovieeditor because of some dependencies that were impossible so I did a force version.  I didn't notice when the sound went off but those are the last 2 big things I did.

It has always worked before.  I didn't notice the sound missing until today.

Any suggestions?

---

### Post by benner on 2008-03-01
this worked:

[https://help.ubuntu.com/community/SoundTroubleshooting#head-d8ad2bdeea082f749845b766aa82831110042360](https://help.ubuntu.com/community/SoundTroubleshooting#head-d8ad2bdeea082f749845b766aa82831110042360)

---


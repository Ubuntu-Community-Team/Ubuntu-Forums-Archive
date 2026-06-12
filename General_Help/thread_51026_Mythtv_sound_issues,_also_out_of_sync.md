---
title: "Mythtv sound issues, also out of sync"
date: 2005-07-22
forum: General Help
---

### Post by mcewen98 on 2005-07-22
I'm having trouble getting sound to work correctly with Mythtv.  I have a cheapo Avermedia tv studio tuner card and an older sound blaster live value sound card.  I have the line out on the tuner connected to the line in on the sound card.  Sound seems to work fine everywhere else, except in mythtv.

The problem is that when I watch live tv, the audio is out of sync, ahead of the video.  I think this is because the audio is being grabbed directly from the coax cable, rather than being written to disk and read back out again, like what happens to the video.

The other problem is that I get no audio when I try to do a recording.

My final problem is that after I exit the mythtv front end, the audio from the last channel that I was on still continues to play.

I did the things listed here, [http://ubuntuforums.org/showthread.php?t=44753&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=44753&page=1&pp=10)

But it had no effect.  I have the preferences->multimedia both set to Alsa.  I also have ESD turned off in preferences->sound.

Has anybody else had problems like this or have any ideas that I've missed? 

Thanks

---

### Post by xgregx on 2005-07-22
Try muting the line in.  It will prevent the sound coming from the coax from playing directly, but it will still get sent to the sound device.  That will help with your delayed sound.  You might have unmute another input, that is why you're not getting sound to record.  Try the command "amixer"  It will output a bunch of stuff about your connections and their volume statuses.  Good luck. :) 
Greg

---

### Post by mcewen98 on 2005-07-22
Thanks, I didn't know about amixer.  To add to the confusion, there are 4 devices listed when I double click on the speaker icon to bring up the mixer, then click on File->Change Device.

I have:

0:TriTech TR29608(OSS Mixer)
1: Bt87x (OSS Mixer)
2: Sound Blaster Live! (Alsa Mixer)
3: Brooktree Bt878 (Alsa Mixer)

When I was screwing with them before, I could get unsynced audio to go away, but nothing was still getting recorded or was playing during 'live tv'.

I'll try experimenting more with the muting and unmuting of the options there, when I get home later.  I think I also need to set MythTv to use ALSA:default instead of /dev/dsp for sound.

---

### Post by xgregx on 2005-07-22
The two bt878 devices have to do with your TV tuner.  The brooktree 878 is a TV tuner chip.  You might have to set your line in as a recorder.  Can't remember how to do it, it's been a while since I messed with mythtv.  GOod luck.
Greg

---

### Post by bloodroses75 on 2006-04-27
[QUOTE=mcewen98]I'm having trouble getting sound to work correctly with Mythtv.  I have a cheapo Avermedia tv studio tuner card and an older sound blaster live value sound card.  I have the line out on the tuner connected to the line in on the sound card.  Sound seems to work fine everywhere else, except in mythtv.

The problem is that when I watch live tv, the audio is out of sync, ahead of the video.  I think this is because the audio is being grabbed directly from the coax cable, rather than being written to disk and read back out again, like what happens to the video.

The other problem is that I get no audio when I try to do a recording.

My final problem is that after I exit the mythtv front end, the audio from the last channel that I was on still continues to play.

I did the things listed here, [http://ubuntuforums.org/showthread.php?t=44753&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=44753&page=1&pp=10)

But it had no effect.  I have the preferences->multimedia both set to Alsa.  I also have ESD turned off in preferences->sound.

Has anybody else had problems like this or have any ideas that I've missed? 

Thanks[/QUOTE]


Have you had any luck the sync issues, no audio recording, and audio from the last channel continuing to play after exiting Mythtv? I have a Leadtek Winfast TV2000XP Deluxe tuner card that uses the line in port as well on my sound blaster live and I am experiencing the same issues. ](*,)  I had setup my mythbox following the directions from here:
[http://www2.truman.edu/~dat725/htpc_single.html](http://www2.truman.edu/~dat725/htpc_single.html)
  Unfortunately his card is a RM card instead of a Deluxe and uses the AUX line on his soundcard, thus his method does not solve my audio problems (even after trying it for hours on end). By trying the suggestions on the truman site and using the gnome volume control, i either get severely out of sync audio with the line-in (in the capture tab) un-mutted and capture togged on (no red x), or no audio at all with the line-in mutted with capture still toggled on. Any other options i have messed with in the volume control window does nothing.

Any suggestions you can give are most appreciative.

---

